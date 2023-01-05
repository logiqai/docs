---
description: 'Version: v3.5.8.4'
---

# Release Notes 🚀

**📆 Thu, Dec 29, 2022**

* Added support for [**Grafana dashboard import**](https://docs.logiq.ai/dashboards/import-grafana-dashboards) for:&#x20;
  * Fluent Bit
  * Go
  * Kafka
  * Kubernetes
  * Node exporter
  * Postgres
  * Prometheus
  * Redis
* Added support for [**Large log messages**](https://docs.logiq.ai/data-management/large-log-events-metrics-traces) up to 1Mb
* Added native support for **Azure blob store** for InstaStore
* Added new **Ingest plugins** for:
  * ****[**Kafka/Confluent**](https://docs.logiq.ai/integrations/kafka)****
  * ****[**Azure EventHub**](https://docs.logiq.ai/integrations/azure/azure-event-hubs)****
  * ****[**GCP PubSub**](https://docs.logiq.ai/integrations/gcp-cloud-logging)****
  * ****[**AWS Kinesis**](https://docs.logiq.ai/integrations/kinesis)****
  * ****[**S3 Compatible object storage**](https://docs.logiq.ai/integrations/object-store-s3-compatible)****
  * ****[**Splunk S2S cooked mode**](https://docs.logiq.ai/integrations/splunk-heavy-forwarder#splunk-cooked-mode)****
* Added new **Forwarder plugins** for:
  * ****[**Splunk Metric index**](https://logflow-docs.logiq.ai/splunk-forwarding/metric-indexes)****
  * ****[**Azure EventHub**](https://logflow-docs.logiq.ai/real-time-stream-forwarding/azure-eventhub)****
  * ****[**AWS Kinesis**](https://logflow-docs.logiq.ai/real-time-stream-forwarding/aws-kinesis)****
  * ****[**Google PubSub**](https://logflow-docs.logiq.ai/real-time-stream-forwarding/google-pub-sub)****
  * ****[**S3 compatible object stores**](https://logflow-docs.logiq.ai/object-store-forwarding/s3-compatible) **** and [**Azure Blob store**](https://logflow-docs.logiq.ai/object-store-forwarding/azure-blob-storage)****
* Added support for [**Renaming attributes**](https://docs.logiq.ai/data-management/rename-attributes) of logs before forwarding data to the destination
* Added support for ingesting directly from [**Splunk UF** (Universal Forwarder)](https://docs.logiq.ai/integrations/splunk-universal-forwarder#splunk-cooked-mode) and [**Splunk HF** (Heavy Forwarder)](https://docs.logiq.ai/integrations/splunk-heavy-forwarder#splunk-cooked-mode) using _Splunk cooked mode_
* Added support for ingesting [**Splunk Metrics**](https://logflow-docs.logiq.ai/splunk-forwarding/metric-indexes)****
* Added support for [**Archiving alerts**](https://docs.logiq.ai/logiq-ui-configuration/audit-trail/alerts-trail) in InstaStore which will be available as an audit trail
* Added support for [**Archiving events**](https://docs.logiq.ai/logiq-ui-configuration/audit-trail/events-trail) that are older than 24 hours which will be available under events history
* Added new [**Severity Metrics**](https://docs.logiq.ai/log-management/explore-logs/severity-metrics) to measure the logs levels within the time range.
* Made **Search** and **UI performance** enhancements ✨
