# OpenTelemetry

### Overview

OpenTelemetry is a collection of tools, APIs, and SDKs. Use it to instrument, generate, collect, and export telemetry data (metrics, logs, and traces) to help analyze software’s performance and behavior.

### OpenTelemetry Metrics

Prometheus Remote Write Exporter can be used to send OpenTelemetry metrics to Prometheus [remote write compatible backends](https://prometheus.io/docs/operating/integrations/)

LOGIQ.AI implements a preometheus remote write backend so metric data from open telementry collectors can be sent to LOGIQ with a simple configuration as described below.

Enable the _prometheusremorewrite_ exporter in your open telemetry configuration yaml

```
exporters:
  prometheusremotewrite:
```

Specify the LOGIQ.AI cluster endpoint to send the remote write data. LOGIQ.AI implements automatic retention tiering to object storage for all your opentelemetry metrics data giving you infinite retention and scale with zero storage overheads as your metrics needs grow.

```
endpoint: "https://<logiq-endpoint>/api/v1/receive"
```

Here's a full configuration example below with TLS enabled.

{% hint style="info" %}
if you are using OpenTelemetry on AWS, remove the "wal:" section below
{% endhint %}

```
exporters:
  prometheusremotewrite:
    endpoint: "https://<logiq-endpoint>/api/v1/receive"
    wal: # Enabling the Write-Ahead-Log for the exporter.
      directory: ./prom_rw # The directory to store the WAL in
      buffer_size: 100 # Optional count of elements to be read from the WAL before truncating; default of 300
      truncate_frequency: 45s # Optional frequency for how often the WAL should be truncated. It is a time.ParseDuration; default of 1m
    tls: 
      ca_file: <file-name>
      cert_file: <file-name>
      key_file: <file-name>

    external_labels: #labels to identify the metric
         label1: value1

receivers:
  otlp:
    protocols:
      grpc:
      http:

processors:
  batch:

service:
  pipelines:
    metrics:
         receivers: [otlp]
         processors: [batch]
         exporters: [prometheusremotewrite]
```

### OpenTelemetry Logs and Traces

LOGIQ.AI supports ingesting Logs and Traces using OpenTelementry agents and collectors. We also maintain compatibility with Jaeger agent and collectors for ingesting logs and traces. This provides broad support for anyone with existing Jaeger agents and collectors deployed as well as someone wanting to adopt the emerging OpenTelemetry standard.

See below for an example of configuring OpenTelemetry collector to push logs and traces to LOGIQ.AI

```
receivers:
  otlp:
    protocols:
      grpc:

exporters:
  logging:

  jaeger:
    endpoint: <logiq-endpoint>:14250
    tls:
      insecure: true

processors:
  batch:

extensions:
  health_check:

service:
  extensions: [health_check]
  pipelines:
    traces:
      receivers: [otlp]
      processors: [batch]
      exporters: [logging, jaeger]
```
