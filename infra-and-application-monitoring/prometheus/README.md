# Overview

LOGIQ.AI's built-in monitoring engine is compatible with Prometheus, Thanos, and VictoriaMetrics. It offers a scalable monitoring tier that automatically uses S3-compatible storage for the metrics sent or generated by the platform providing easy scaleout with zero storage overheads.&#x20;

If you are using an existing time-series database, no worries. LOGIQ.AI allows external time-series database connectors to query them directly. Once connected, you now have a lot more capabilties enabled and available for your time-series data.&#x20;

E.g. if you are using InfluxDB, just use our InfluxDB connector and you can start querying data directly from InfluxDB. Not only that, you can now apply our built-in AI/ML capabiltities for **ANY** time-series data, and viola, your InfluxDB gets full AI/ML capabilities such as anomaly detection, data baselining, forecasting, applying statistical models, visualization, and CRON style reporting.

In summary, LOGIQ.AI offers various ways to gather and utilize application and infrastructure metrics.

* [Open Telemetry Metrics](../../integrations/opentelemetry.md)
* [Prometheus Remote Write](../../integrations/prometheus/prometheus-remote-write.md) Protocol
* Query external Prometheus compatible Datasource
* Amazon Managed Service for Prometheus (AMP) Datasource
* External databases such as InfluxDB or time-series data in databases like Postgres, MySQL, Elastic, etc.

![A sample Prometheus dashboard with anomaly detection](<../../.gitbook/assets/image (125).png>)

The next few sections describe how to connect and query your metrics data in LOGIQ. For using LOGIQ's Prometheus Remote Write capabilities to push your metrics into LOGIQ see [here](../../integrations/prometheus/prometheus-remote-write.md).