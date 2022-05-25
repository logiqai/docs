# Logiq remote-write

LOGIQ can collect Prometheus metrics from externally hosted Prometheus. LOGIQ uses the `remote_write` capabilities to help you do so.

### **Prometheus configuration**

To send metrics from Prometheus to Logiq endpoint, use the configuration below.

```
remote_write:
  - url: https://<Logiq-endpoint>/api/v1/receive
    tls_config:
        insecure_skip_verify: true
```

****

### **OpenTelemetry configuration**

Prometheus Remote Write Exporter can be leveraged to send OpenTelemetry metrics to Prometheus [remote write compatible backends](https://prometheus.io/docs/operating/integrations/), and these metrics can be visualized on LOGIQ.

```

exporters:
  prometheusremotewrite:
    endpoint: "https://<logiq-endpoint>/api/v1/receive"
    wal: # Enabling the Write-Ahead-Log for the exporter.
      directory: ./prom_rw # The directory to store the WAL in
      buffer_size: 100 # Optional count of elements to be read from the WAL before truncating; default of 300
      truncate_frequency: 45s # Optional frequency for how often the WAL should be truncated. It is a time.ParseDuration; default of 1m
    tls: 
      insecure: "false"
      insecure_skip_verify: "true"
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

### **VictoriaMetrics configuration**

VictoriaMetrics is a fast, cost-effective, and scalable monitoring solution and time-series database. `vmagent` is an agent which helps you collect metrics from various sources and store them in [VictoriaMetrics](https://github.com/VictoriaMetrics/VictoriaMetrics) or any other Prometheus-compatible storage systems that support the `remote_write` protocol. VMagent has the ability to push metrics additionally to pulling them; **** push model is a traditional model of the client sending data to the server:

![](https://docs.victoriametrics.com/keyConcepts\_push\_model.png)

Run the [<mark style="color:blue;"><mark style="color:purple;">**vmagent**<mark style="color:purple;"></mark> <mark style="color:blue;"></mark><mark style="color:blue;"></mark> ](https://docs.victoriametrics.com/vmagent.html#quick-start)as shown below and pass the below parameters

{% hint style="info" %}
&#x20;remoteWrite.tls.url=https://\<Logiq-endpoint>/api/v1/receive

remoteWrite.tlsInsecureSkipVerify
{% endhint %}

```
./vmagent-prod -promscrape.config=/etc/prometheus/prometheus.yml -remoteWrite.url=https://<Logiq-endpoint>/api/v1/receive -remoteWrite.tlsInsecureSkipVerify
```
