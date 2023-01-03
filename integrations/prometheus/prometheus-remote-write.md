# Prometheus Remote Write

LOGIQ can collect Prometheus metrics from externally hosted Prometheus. LOGIQ uses the `remote_write` capabilities to help you do so.

### **Prometheus configuration**

To send metrics from Prometheus to Logiq endpoint, use the configuration below.&#x20;

{% hint style="info" %}
You may also want to add a relabel configuration section to make sure the metrics from your prometheus instance are prefixed for easier identification See Section below.
{% endhint %}

<pre><code><strong>remote_write:
</strong>  - url: https://&#x3C;Logiq-endpoint>/api/v1/receive
    tls_config:
        insecure_skip_verify: true
        # Optional - ca_file: &#x3C;file-name>
        # Optional - cert_file: &#x3C;file-name>
        # Optional - key_file: &#x3C;file-name>
</code></pre>

#### Adding relabel configuration to prefix your metrics

Replace \<prefix> in the _replacement_ attribute in the _write\_relabel\_configs s_ection to a prefix that can easily help you identify your metrics.

```
  remote_write:
  - url: https://<Logiq-endpoint>/api/v1/receive
    tls_config:
        insecure_skip_verify: true

    write_relabel_configs:
    - action: replace
      source_labels: [__name__]
      regex: (.*)
      target_label: __name__
      replacement: '<prefix>_$1'
```

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
