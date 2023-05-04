# Releases-old

## v3.5.8.4

### **📆 Thu, Dec 29, 2022**

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
  * [**Kafka/Confluent**](https://docs.logiq.ai/integrations/kafka)
  * [**Azure EventHub**](https://docs.logiq.ai/integrations/azure-eventhub)
  * [**GCP PubSub**](https://docs.logiq.ai/integrations/gcp-pubsub)
  * [**AWS Kinesis**](https://docs.logiq.ai/integrations/kinesis)
  * [**S3 Compatible object storage**](https://docs.logiq.ai/integrations/object-store-s3-compatible)
  * [**Splunk S2S cooked mode**](https://docs.logiq.ai/integrations/splunk-heavy-forwarder#splunk-cooked-mode)
  * [**IBM QRadar**](https://docs.logiq.ai/integrations/ibm-qradar)
  * [**OSSEC**](https://docs.logiq.ai/integrations/ossec-variants-ossec-wazuh-atomic#starting-the-manager-ossec-server)
* Added new **Forwarder plugins** for:
  * [**Splunk Metric index**](https://logflow-docs.logiq.ai/splunk-forwarding/metric-indexes)
  * [**Azure EventHub**](https://logflow-docs.logiq.ai/real-time-stream-forwarding/azure-eventhub)
  * [**AWS Kinesis**](https://logflow-docs.logiq.ai/real-time-stream-forwarding/aws-kinesis)
  * [**Google PubSub**](https://logflow-docs.logiq.ai/real-time-stream-forwarding/google-pub-sub)
  * [**S3 compatible object stores**](https://logflow-docs.logiq.ai/object-store-forwarding/s3-compatible) and [**Azure Blob store**](https://logflow-docs.logiq.ai/object-store-forwarding/azure-blob-storage)
* Added support for [**Renaming attributes**](https://docs.logiq.ai/data-management/rename-attributes) of logs before forwarding data to the destination
* Added support for ingesting directly from [**Splunk UF** (Universal Forwarder)](https://docs.logiq.ai/integrations/splunk-universal-forwarder#splunk-cooked-mode) and [**Splunk HF** (Heavy Forwarder)](https://docs.logiq.ai/integrations/splunk-heavy-forwarder#splunk-cooked-mode) using _Splunk cooked mode_
* Added support for ingesting [**Splunk Metrics**](https://logflow-docs.logiq.ai/splunk-forwarding/metric-indexes)
* Added support for [**Archiving alerts**](https://docs.logiq.ai/logiq-ui-configuration/audit-trail/alerts-trail) in InstaStore which will be available as an audit trail
* Added support for [**Archiving events**](https://docs.logiq.ai/logiq-ui-configuration/audit-trail/events-trail) that are older than 24 hours which will be available under events history
* Added new [**Severity Metrics**](https://docs.logiq.ai/log-management/explore-logs/severity-metrics) to measure the logs levels within the time range.
* Made **Search** and **UI performance** enhancements ✨



## 3.0 - 2022-07-31

### Changed

1. Distributed Tracing
   * Compatible with OpenTelemetry and Jaeger agents
   * Infinite Scale and retention on InstaStore
2. AnyTime - AI/ML Engine for any time-series database
   * Anomaly detection
   * Statistical data baselining and dynamic thresholds
   * Forecasting
   * Moving average&#x20;
3. Anomaly and dynamic threshold-based alerts
4. Input Plugins
   * IBM QRadar
   * Splunk S2S
5. LogFlow Forwarders
   * Splunk Syslog, Splunk HEC, Splunk S2S
   * Datadog
   * Dynatrace
   * NewRelic
   * IBM QRadar
   * ArcSight
   * Syslog, Syslog CEF
6. New Data Sources
   * AWS CloudWatch Metrics ( YAML )
   * AWS CloudWatch Metrics (SQL Insights)

## 2.1.11.32 - 2021-06-11

### Changed

* LD-35 multi-variate regEx in log2Metrics

## 2.1.11.31 - 2021-06-07

### Changed

* A-4 Comparator operator results in lesser search results

## 2.1.11.30 - 2021-06-02

### Changed

* LD-30 Custom Search Indices

## 2.1.11.26 - 2021-04-15

### Changed

* Namespace level Log distribution graph in Search and Logs page
* Performance Improvements

## 2.1.11.25 - 2021-04-08

### Fixed

* DEFECT#613 Query backend not honoring the startTime sent from UI

### Changed

* PERF#614 Uploader Optimizations

## 2.1.11.24 - 2021-04-02

### Changed

* PERF#603 Query Improvements
  * Bloom filter for faster search
  * Query interval skip improvements
* PERF#602 Metadata Improvements
  * Metadata uploader improvements
* UI#599 UI enhancements
  * Search and logs page optimizations
* FEATURE#580 AWS improvements
  * AWS ECS logging improvements
  * Customized AWS fargate 1.4 fluent driver image
  * AWS Cloudwatch exporter



## 2.1.11 - 2020-12-13

### Log aggregation

* Support for **and** expressions in search&#x20;
* Event rules designer support for **&&** and **||** for individual parameters
* Performance and memory improvements

### Data convergence

* Support for Apache DRUID connector
* Optionally deploy Grafana with the LOGIQ stack

### UI

* Logs compare view to select 2 logs to be viewed side by side
* Easy toggle for activating/deactivating periodic queries

## 2.1.9 - 2020-11-28

### Added

#### Log aggregation

* Support for full data/metadata recovery on service restarts

#### Log analytics

* Support for application and process/pod context in log and search views

#### Deployment and Infrastructure

* Support for node selectors. Both taints and node selectors are supported
* Support for using spot instances on EKS/AWS
* Support for using S3 compatible buckets directly without a caching gateway to optimize for region optimized deployments

#### UI

* Multi cluster support
* License management UI
* Ingest configuration settings exposed in the UI
* Logs page and search now have application and process/pod level contexts

## 2.1 - 2020-09-28

### Added

#### Log aggregation

* Parquet with Snappy compression for data at REST

#### Log analytics

* Log view supports full JSON view for ingested log data like Search view
* Performance improvements for faster search, logs, and tailing

#### Monitoring

* Event deduplication can reduce event data by up to 1000x at peak data rates
* Deduplication of monitoring events at Namespace granularity

#### Deployment and Infrastructure

* Separation of LOGIQ server into microservices for data ingestion, ML/UI and S3/Metadata management
* Support for taints in HELM chart for more control over large-scale deployments e.g. schedule ingest pods on dedicated nodes etc.
* Log tailing infrastructure using Redis switches to diskless replication/no persistence

## 2.0 - 2020-08-12

### Added

#### Log aggregation

* Support for AWS Fargate, Firelens, [Fluent forward Protocol ](https://github.com/fluent/fluentd/wiki/Forward-Protocol-Specification-v1)&#x20;
* LOGIQ Fluent-bit daemon-set for K8S clusters
* Data extraction via Grok patterns, compatible with Logstash Grok patterns using the [Grokky library](https://github.com/logrusorgru/grokky)

#### Log analytics

* Redesigned - Elastic/Kibana like search UI that scales to infinite data from S3 compatible object store
* Real-time alertable events and alerts from log data
* Real-time extraction of log data facets using Grok expressions
* 1-Click conversion of log data events to time series visualization &#x20;

#### Logiqctl

* Logiqctl command-line toolkit
* Works with SAML users via API Key

#### Monitoring

* Prometheus alert manager integration into LOGIQ alerts for unified alerting across logs and metrics
* Built-in Logiq dashboard for LOGIQ cluster performance and health monitoring&#x20;

#### LOGIQ Data platform

* Connect numerous popular data sources into the LOGIQ platforms such as Postgres, MySql, Elasticsearch, Athena, MongoDB, Prometheus, and more.&#x20;
* JSON Data source for easily converting arbitrary JSON data into tables, widgets, and alerts

#### Role-based access control

* Namespace RBAC for log data from K8S namespaces
* SAML Integration for RBAC allowing SAML Attributes to map to RBAC groups

#### Security and Compliance

* Fully secured HELM deployment using Role, RoleBindings, ServiceAccounts and Pod Security policies for all service
* Cryptographically verified JWT token for API communication
* Built-in audit logging for the entire product and infrastructure

## 1.2.1 - 2020-05-11

### Added

#### K8S

* Add support for ingress with http and optionally have https
* ServiceMonitor for ingesting server if prometheus is installed

#### UI

* Logs modal ordering to match how developers view logs from a file
* Highlight logline from search

#### Misc

* Bug fixes for performance, graceful failure handling/recovery

## 1.2.0 - 2020-04-28

Official GA of LOGIQ's complete Observability platform with support for metrics and log analytics

### Added

#### K8S

* Scale-out and HA deployment for Kubernetes via HELM 3 chart ( [https://github.com/logiqai/helm-charts](https://github.com/logiqai/helm-charts) )

#### UI

* Monitoring of time series metrics
* New Log viewer
* Log viewer integration with faceted search
* Log time machine to go back in time to log state

#### CLI

* [logiqctl](broken-reference) is now GA with support for log tailing, historical queries and search

## 1.1.0 - 2020-02-27

### Fixed

* Fluentd sends error logs as info - fixed with grok patterns to extract proper severity strings from incoming messages

### Added

* Anomaly detection via Eventing with built-in and custom rules
* Built-in UI Help with Intercom chat
* Expand and collapse search facets

### Changed

* New AMI's for AWS marketplace

## 1.0.0 - 2020-01-21

Official GA of LOGIQ's Log Insights platform

### Added

* AWS Marketplace AMI for all regions including Gov cloud regions
* AWS CloudFormation 1-click deployment
* Rsyslog, Syslog protocol support for data ingest via Rsyslogd, syslogd, syslog-ng, logstash, fluentd, fluentbit, docker logging syslog driver.
* Built-in UI with SQL Queries, Faceted search, Alerts, Dashboards

