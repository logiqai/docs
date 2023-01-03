---
description: 'Version: v3.5.8.4'
---

# Release Notes 🚀

**📆 Thu, Dec 29, 2022**

****

* Added support for **Grafana dashboard import** for:&#x20;
  * Fluent Bit
  * Go
  * Kafka
  * Kubernetes
  * Node exporter
  * Postgres
  * Prometheus
  * Redis
* Added support for **Large log messages** up to 1Mb
* Added native support for **Azure blob store** for InstaStore
* Added new **Ingest plugins** for:
  * Kafka/Confluent
  * OCI bucket
  * Azure EventHub
  * GCP PubSub
  * AWS Kinesis
  * S3 Compatible object storage
* Added new **Forwarder plugins** for:
  * Splunk Metric index
  * Azure EventHub
  * AWS Kinesis
  * Google PubSub
  * S3 compatible object stores and Azure Blob store
* Added support for **Renaming attributes** of logs before forwarding data to the destination
* Added support for ingesting directly from **Splunk UF** (Universal Forwarder) and **Splunk HF** (Heavy Forwarder) using **Splunk cooked mode**
* Added support for ingesting **Splunk Metrics**
* Added support for **Archiving alerts** in InstaStore which will be available as an audit trail
* Added support for **Archiving events** that are older than 24 hours which will be available under events history
* Made **Search** and **UI performance** enhancements ✨
