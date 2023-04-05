---
description: 'Version: v3.5.9.1'
---

# Release Notes 🚀

#### Version: v3.5.9.1 <a href="#uversionv359u" id="uversionv359u"></a>

**📅 Fri, Mar 24, 2023**

*   **Topology-powered root-cause analysis**.

    Visualize your data streams as a topology with drill down to errors and warnings for faster root causes. Helps visualize the health of your applications. Users can quickly investigate the issues by clicking errors or alerts.
*   **Data flow Pipelines**.

    The pipeline is a series of processes or stages through which data flow systematically and efficiently. Helps to visualize the flow between nodes, rules, and filters applied for the data flow. Shows the inflow and outflow information of data, and also helps in identifying the data loss or optimizing the data flow to forward destinations.
*   **Search results aggregates**.

    Buit-in Pivot table makes it easy to analyze large data sets from search queries. Summarize or Visualize a set of data points for instant analysis. Some common examples of aggregation functions include(Count, Value, Sum, Count Unique Values, List Unique Values, Average, Median, Min, Max). Aggregation functions are used to summarize large datasets into a more manageable form for further analysis and visualization. And includes different types of visualizations (Table, Line chart, Area chart, Scatter chart, Dot chart, and Multiple pie chart).
*   **Re-designed Landing page**.

    Instantly get access to valuable insights when you login into our redesigned Explore page. Users now log in and directly land on the Explore page with quick summaries at their fingertips.

    1. Introduced counter widgets for EPS, Total Flows, Total Events, Forwarders, and Source Extensions.
    2. Added a new Event Statistics column, which has counts of (Errors, Alerts, Critical, Emergency), (Warnings) and (Total) events.
*   **OSSEC HIDS Mappings**

    Automatically map OSSEC HIDS event severity and log messages for Linux and Windows environments.
* **Added support for exporting events and metrics from** [**Apache Beam**](https://docs.logiq.ai/integrations/apache-beam) **to LOGIQ**.
*   **OpenTelemetry `otel.status_code` Mapping**

    Detect OpenTelemetry severity and level embeddings and map them into severity levels.
* **Memory and performance improvements**.
* **Automated agent installation for Linux and Windows**.

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
  * ****[**Azure EventHub**](https://docs.logiq.ai/integrations/azure-eventhub)****
  * ****[**GCP PubSub**](https://docs.logiq.ai/integrations/gcp-pubsub)****
  * ****[**AWS Kinesis**](https://docs.logiq.ai/integrations/kinesis)****
  * ****[**S3 Compatible object storage**](https://docs.logiq.ai/integrations/object-store-s3-compatible)****
  * ****[**Splunk S2S cooked mode**](https://docs.logiq.ai/integrations/splunk-heavy-forwarder#splunk-cooked-mode)****
  * ****[**IBM QRadar**](https://docs.logiq.ai/integrations/ibm-qradar)****
  * ****[**OSSEC**](https://docs.logiq.ai/integrations/ossec-variants-ossec-wazuh-atomic#starting-the-manager-ossec-server)****
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
