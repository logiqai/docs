# Overview

LOGIQ built-in monitoring engine is compatible with Prometheus, Thanos, and VictoriaMetrics. Also, LOGIQ.AI allows time-series data to be queried from external databases without having to push them directly to LOGIQ.AI. This makes querying time-series data a breeze. LOGIQ.AI's **AnyTime** capability allows other time-series databases such as InfluxDB to be connected as well. Not only that, you can apply our built-in AI/ML capabiltities for time-series data on any time-series database.

LOGIQ.AI offers various ways to gather and push infrastructure and application metrics to LOGIQ.AI

* [Open Telemetry Metrics](../../integrations/open-telemetry.md)
* [Prometheus Remote Write](../prometheus-remote-write.md) Protocol
* Query external Prometheus compatible Datasource
* Amazon Managed Service for Prometheus (AMP) Datasource
* External databases such as InfluxDB or time-series data in databases like Postgres, MySQL, Elastic, etc.

![A sample Prometheus dashboard with anomaly detection](<../../.gitbook/assets/image (31).png>)

The next few sections describe how to connect and query your metrics data in LOGIQ. For using LOGIQ's Prometheus Remote Write capabilities to push your metrics into LOGIQ see [here](../prometheus-remote-write.md).
