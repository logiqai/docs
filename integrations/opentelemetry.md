# OpenTelemetry

### Overview

OpenTelemetry is a collection of tools, APIs, and SDKs. Use it to instrument, generate, collect, and export telemetry data (metrics, logs, and traces) to help analyze software’s performance and behavior.

{% hint style="warning" %}
Supported otel agents - v0.59.0 or earlier - [https://github.com/open-telemetry/opentelemetry-collector/releases/tag/v0.59.0](https://github.com/open-telemetry/opentelemetry-collector/releases/tag/v0.59.0)
{% endhint %}

### OpenTelemetry Metrics

Prometheus Remote Write Exporter can be used to send OpenTelemetry metrics to Prometheus [remote write compatible backends](https://prometheus.io/docs/operating/integrations/)

Apica Ascent implements a prometheus remote write backend so metric data from open telemetry collectors can be sent to Apica Ascent with a simple configuration as described below.

Enable the _prometheusremorewrite_ exporter in your open telemetry configuration yaml

```
exporters:
  prometheusremotewrite:
```

Specify the Apica Ascent cluster endpoint to send the remote write data. Apica Ascent implements automatic retention tiering to object storage for all your opentelemetry metrics data giving you infinite retention and scale with zero storage overheads as your metrics needs grow.

```
endpoint: "https://<apica-ascent-endpoint>/api/v1/receive"
```

Here's a full configuration example below with TLS enabled.

{% hint style="info" %}
if you are using OpenTelemetry on AWS, remove the "wal:" section below
{% endhint %}

```
exporters:
  prometheusremotewrite:
    endpoint: "https://<apica-ascent-endpoint>/api/v1/receive"
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

### Scraping Prometheus Metrics

In the OpenTelemetry config file, you can include a scrape section to scrape data from Prometheus endpoints. You can subsequently push that to a remote Prometheus compatible write endpoint using instructions from the section above.

```
receivers:
  prometheus:
      config:
        scrape_configs:
        - job_name: 'otel-collector'
          scrape_interval: 10s
          static_configs:
          - targets: ['0.0.0.0:8888']

service:
  pipelines:
    metrics:
         receivers: [prometheus]          
```

### OpenTelemetry Logs and Traces

Apica Ascent supports ingesting Logs and Traces using OpenTelementry agents and collectors. We also maintain compatibility with Jaeger agent and collectors for ingesting logs and traces. This provides broad support for anyone with existing Jaeger agents and collectors deployed as well as someone wanting to adopt the emerging OpenTelemetry standard.

See below for an example of configuring OpenTelemetry collector to push logs and traces to Apica Ascent

```
receivers:
  otlp:
    protocols:
      grpc:

exporters:
  logging:

  jaeger:
    endpoint: <apica-ascent-endpoint>:14250
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

### Language Integrations

#### Java

If you are writing a Java-based application and want to enable OpenTelemetry for instrumenting your application logs, traces, and metrics, you can use the OpenTelemetry Java agent Jar file to attach to your existing Java applications.

The Jar file can be found here - [https://github.com/open-telemetry/opentelemetry-java-instrumentation#about](https://github.com/open-telemetry/opentelemetry-java-instrumentation#about)

{% hint style="danger" %}
the Prometheus metrics options create a pull metric instance that should be scraped by an external Prometheus compatible instance
{% endhint %}

<table><thead><tr><th width="273.3437417078941" align="right">JAVA_OPTS</th><th align="center">Value</th><th align="center">Notes</th></tr></thead><tbody><tr><td align="right">otel.service_name</td><td align="center">&#x3C;User defined></td><td align="center">Give a service name to group your OpenTelemetry data traces under this service name</td></tr><tr><td align="right">otel.traces.exporter</td><td align="center">jaeger</td><td align="center"></td></tr><tr><td align="right">otel.exporter.jaeger.endpoint</td><td align="center">http://&#x3C;Apica Ascent ENDPOINT>:14250</td><td align="center">Apica Ascent OpenTelemetry traces endpoint</td></tr><tr><td align="right"></td><td align="center">https://&#x3C;Apica Ascent ENDPOINT>:14250</td><td align="center">TLS must be enabled on the collector port on the Apica Ascent server</td></tr><tr><td align="right">javaagent</td><td align="center">&#x3C;PATH TO JAR>/opentelemetry-javaagent.jar</td><td align="center">OpenTelemetry agent Jar file</td></tr><tr><td align="right">otel.metrics.exporter</td><td align="center">prometheus</td><td align="center"></td></tr><tr><td align="right">otel.exporter.prometheus.port</td><td align="center"></td><td align="center">Default port is 9464</td></tr><tr><td align="right">otel.exporter.prometheus.host</td><td align="center"></td><td align="center">Default is 0.0.0.0</td></tr></tbody></table>

<pre class="language-shell" data-overflow="wrap" data-line-numbers><code class="lang-shell">$> java -javaagent:opentelemetry-javaagent.jar -Dotel.exporter.otlp.certificate=./ca.crt -Dotel.traces.exporter=jaeger -Dotel.exporter.jaeger.endpoint=<a data-footnote-ref href="#user-content-fn-1">https</a>://$APICA_ASCENT_SERVER:14250 -Dotel.metrics.exporter=none -Dotel.service-name=java-petclinic-sample-app -Dotel.exporter.logging.prefix -jar -Djava.util.logging.config.file=logging.properties target/spring-petclinic-2.7.0-SNAPSHOT.jar --server.port=8080
</code></pre>

{% hint style="info" %}
When using TLS please ensure you have the CA cert of the Apica Ascent environment installed in the JVM Cert store. Instructions can be found here - [https://connect2id.com/blog/importing-ca-root-cert-into-jvm-trust-store](https://connect2id.com/blog/importing-ca-root-cert-into-jvm-trust-store)
{% endhint %}

![](<../.gitbook/assets/Screen Shot 2022-08-02 at 6.29.42 PM.png>)

### Example Petclinic app with open telemetry integration

You can use our freely available petclinc java application for opentelmetry integration testing. Just launch our free container as below and point it to the Apica service IP/DNS

{% code overflow="wrap" %}
```
docker run --name petclinic -d -p 8080:8080 -e LOGIQ_SERVER=mylogiqip.example.com logiqai/petclinic_open_telemetry
```
{% endcode %}

{% hint style="warning" %}
Make sure your Apica Ascent server is running and port 14250 is reachable
{% endhint %}

[^1]: TLS Enabled, Use http if TLS is not enabled.
