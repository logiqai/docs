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

### Language Integrations

#### Java

If you are writing a Java-based application and want to enable OpenTelemetry for instrumenting your application logs, traces, and metrics, you can use the OpenTelemetry Java agent Jar file to attach to your existing Java applications.

The Jar file can be found here - [https://github.com/open-telemetry/opentelemetry-java-instrumentation#about](https://github.com/open-telemetry/opentelemetry-java-instrumentation#about)

{% hint style="danger" %}
the Prometheus metrics options create a pull metric instance that should be scraped by an external Prometheus compatible instance
{% endhint %}

|                    JAVA\_OPTS |                    Value                   |                                        Notes                                        |
| ----------------------------: | :----------------------------------------: | :---------------------------------------------------------------------------------: |
|            otel.service\_name |               \<User defined>              | Give a service name to group your OpenTelemetry data traces under this service name |
|          otel.traces.exporter |                   jaeger                   |                                                                                     |
| otel.exporter.jaeger.endpoint |       http://\<LOGIQ ENDPOINT>:14250       |                        LOGIQ.AI OpenTelemetry traces endpoint                       |
|                               |       https://\<LOGIQ ENDPOINT>:14250      |            TLS must be enabled on the collector port on the logiq server            |
|                     javaagent | \<PATH TO JAR>/opentelemetry-javaagent.jar |                             OpenTelemetry agent Jar file                            |
|         otel.metrics.exporter |                 prometheus                 |                                                                                     |
| otel.exporter.prometheus.port |                                            |                                 Default port is 9464                                |
| otel.exporter.prometheus.host |                                            |                                  Default is 0.0.0.0                                 |

<pre class="language-shell" data-overflow="wrap" data-line-numbers><code class="lang-shell">$> java -javaagent:opentelemetry-javaagent.jar -Dotel.exporter.otlp.certificate=./ca.crt -Dotel.traces.exporter=jaeger -Dotel.exporter.jaeger.endpoint=<a data-footnote-ref href="#user-content-fn-1">https</a>://$LOGIQ_SERVER:14250 -Dotel.metrics.exporter=none -Dotel.service-name=java-petclinic-sample-app -Dotel.exporter.logging.prefix -jar -Djava.util.logging.config.file=logging.properties target/spring-petclinic-2.7.0-SNAPSHOT.jar --server.port=8080
</code></pre>

{% hint style="info" %}
When using TLS please ensure you have the CA cert of the LOGIQ environment installed in the JVM Cert store. Instructions can be found here - [https://connect2id.com/blog/importing-ca-root-cert-into-jvm-trust-store](https://connect2id.com/blog/importing-ca-root-cert-into-jvm-trust-store)
{% endhint %}

![](<../.gitbook/assets/Screen Shot 2022-08-02 at 6.29.42 PM.png>)

### Example Petclinic app with open telemetry integration

You can use our freely available petclinc java application for opentelmetry integration testing. Just launch our free container as below and point it to the logiq service IP/DNS

{% code overflow="wrap" %}
```
docker run --name petclinic -d -p 8080:8080 -e LOGIQ_SERVER=mylogiqip.example.com logiqai/petclinic_open_telemetry
```
{% endcode %}

{% hint style="warning" %}
Make sure your logiq server is running and port 14250 is reachable
{% endhint %}



[^1]: TLS Enabled, Use http if TLS is not enabled.
