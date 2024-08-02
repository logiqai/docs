# Table of contents

* [Welcome to Apica Docs!](README.md)

## PRODUCT OVERVIEW

* [Ascent Overview](product-overview/ascent-overview.md)
* [Ascent User Interface](product-overview/the-logiq-ui.md)
* [Synthetic Monitoring](https://apica-kb.atlassian.net/wiki/spaces/ASMDOCS/pages/2177269761/ASM+Platform+Overview)
* [Loadtesting](https://apica-kb.atlassian.net/wiki/spaces/ALTDOCS/pages/5538148/Overview+of+the+Apica+Load+Test+Solution)
* [Advanced Scripting Engine](https://apica-kb.atlassian.net/wiki/spaces/DAZT/pages/5674203/What+is+ZebraTester)

## GETTING STARTED

* [Ascent Deployment Overview](getting-started/ascent-deployment-overview.md)
* [Quickstart with Docker-Compose](getting-started/quickstart-with-docker-compose.md)
* [Cloud - SaaS Deployment](getting-started/logiq-saas.md)
* [On-Premise PaaS Deployment Architecture](getting-started/paas-deployment-architecture.md)
* [On-Premise PaaS deployment](getting-started/logiq-paas-deployment/README.md)
  * [Deploying Apica Ascent PaaS on Kubernetes](getting-started/logiq-paas-deployment/k8s-quickstart-guide.md)
  * [Deploying Apica Ascent PaaS on MicroK8s](getting-started/logiq-paas-deployment/deploying-logiq-paas-on-microk8s.md)
  * [Deploying Apica Ascent PaaS on AWS](getting-started/logiq-paas-deployment/aws-cloudformation.md)
  * [Deploying Apica Ascent EKS on AWS using CloudFormation](getting-started/logiq-paas-deployment/deploying-logiq-eks-on-aws-using-cloudformation.md)
  * [Deploying Ascent on AWS EKS with Aurora PostgreSQL and ElastiCache Redis using Cloud Formation](getting-started/logiq-paas-deployment/deploying-ascent-on-aws-eks-with-aurora-postgresql-and-elasticache-redis-using-cloud-formation/README.md)
    * [Deploying Apica Ascent on AWS EKS with Aurora PostgreSQL and ElastiCache Redis using CloudFormation](getting-started/logiq-paas-deployment/deploying-ascent-on-aws-eks-with-aurora-postgresql-and-elasticache-redis-using-cloud-formation/deploying-apica-ascent-on-aws-eks-with-aurora-postgresql-and-elasticache-redis-using-cloudformation.md)
    * [Apica Ascent on AWS EKS (Private Endpoint) with Aurora PostgreSQL and ElastiCache Redis on prod VPC](getting-started/logiq-paas-deployment/deploying-ascent-on-aws-eks-with-aurora-postgresql-and-elasticache-redis-using-cloud-formation/apica-ascent-on-aws-eks-private-endpoint-with-aurora-postgresql-and-elasticache-redis-on-prod-vpc.md)
  * [Deploying Apica Ascent EKS on AWS using custom AMI](getting-started/logiq-paas-deployment/deploying-logiq-eks-on-aws-using-custom-ami.md)
  * [Deploying Apica Ascent EKS with AWS ALB](getting-started/logiq-paas-deployment/deploying-logiq-eks-with-aws-alb.md)
  * [Deploying Apica Ascent PaaS in Azure Kubernetes Service](getting-started/logiq-paas-deployment/deploying-logiq-paas-in-azure-kubernetes-service/README.md)
    * [Azure Blob Storage Lifecycle Management](getting-started/logiq-paas-deployment/deploying-logiq-paas-in-azure-kubernetes-service/azure-blob-storage-lifecycle-management.md)

## DATA SOURCES

* [Data Source Overview](data-sources/overview.md)
* [API](data-sources/api/README.md)
  * [JSON Data source](data-sources/api/json-data-source.md)
  * [RSS](data-sources/api/rss.md)
* [AWS](data-sources/aws/README.md)
  * [Amazon Athena](data-sources/aws/amazon-athena.md)
  * [Amazon CloudWatch ( YAML )](data-sources/aws/amazon-cloudwatch-yaml.md)
  * [Amazon Elasticsearch Service](data-sources/aws/amazon-elasticsearch-service.md)
  * [Amazon Redshift](data-sources/aws/amazon-redshift.md)
  * [MySQL Server (Amazon RDS)](data-sources/aws/mysql-server-amazon-rds.md)
* [NoSQL Data Sources](data-sources/nosql-data-sources/README.md)
  * [MongoDB](data-sources/nosql-data-sources/mongodb.md)
* [OLAP](data-sources/olap/README.md)
  * [Data Bricks](data-sources/olap/data-bricks.md)
  * [Druid](data-sources/olap/druid.md)
  * [Snowflake](data-sources/olap/snowflake.md)
* [SQL Data Sources](data-sources/sql-data-sources/README.md)
  * [PostgreSQL](data-sources/sql-data-sources/postgresql.md)
  * [Microsoft SQL Server](data-sources/sql-data-sources/microsoft-sql-server.md)
  * [MySQL Server](data-sources/sql-data-sources/mysql-server.md)
* [Time Series Databases](data-sources/time-series-databases/README.md)
  * [Prometheus Compatible](data-sources/time-series-databases/prometheus-compatible.md)
  * [Elasticsearch](data-sources/time-series-databases/elasticsearch-data-source.md)
  * [InfluxDB](data-sources/time-series-databases/influxdb.md)

## INTEGRATIONS

* [Integrations Overview](integrations/overview/README.md)
  * [Generating a secure ingest token](integrations/overview/generating-a-secure-ingest-token.md)
  * [Data Ingest Ports](integrations/overview/data-ingest-ports.md)
* [Page](integrations/page.md)
* [List of Integrations](integrations/list-of-integrations/README.md)
  * [Apache Beam](integrations/list-of-integrations/apache-beam/README.md)
    * [Export Metrics to Prometheus](integrations/list-of-integrations/apache-beam/export-metrics-to-prometheus/README.md)
      * [Pull Mechanism via Push-Gateway](integrations/list-of-integrations/apache-beam/export-metrics-to-prometheus/pull-mechanism-via-push-gateway.md)
    * [Export Events to Apica Ascent](integrations/list-of-integrations/apache-beam/export-events-to-logiq.md)
  * [Apica ASM](integrations/list-of-integrations/apica-asm.md)
  * [Apica Ascent Observability Data Collector Agent](integrations/list-of-integrations/logiq.ai-observability-data-collector-agent.md)
  * [AWS](integrations/list-of-integrations/aws/README.md)
    * [AWS CloudWatch](integrations/list-of-integrations/aws/aws-cloudwatch-exporter.md)
    * [AWS ECS](integrations/list-of-integrations/aws/aws-ecs/README.md)
      * [Forwarding AWS ECS logs to Apica Ascent using AWS FireLens](integrations/list-of-integrations/aws/aws-ecs/forwarding-aws-ecs-logs-to-logiq-using-aws-firelens.md)
      * [ECS prometheus metrics to Apica Ascent](integrations/list-of-integrations/aws/aws-ecs/ecs-prometheus-metrics-to-logiq.md)
    * [AWS S3](integrations/list-of-integrations/aws/aws-s3.md)
  * [Azure](integrations/list-of-integrations/azure/README.md)
    * [Azure Databricks](integrations/list-of-integrations/azure/azure-databricks.md)
    * [Azure Eventhub](integrations/list-of-integrations/azure/azure-eventhub.md)
    * [Azure Event Hubs](integrations/list-of-integrations/azure/azure-event-hubs.md)
  * [Docker Compose](integrations/list-of-integrations/docker-compose.md)
  * [Docker Swarm logging](integrations/list-of-integrations/docker-swarm-logging.md)
  * [Docker Syslog log driver](integrations/list-of-integrations/docker-syslog-log-driver.md)
  * [F5 Big-Ip System](integrations/list-of-integrations/f5-big-ip-system.md)
  * [Filebeat](integrations/list-of-integrations/filebeat.md)
  * [Fluent Bit](integrations/list-of-integrations/fluent-bit/README.md)
    * [Forwarding Amazon-Linux logs to Apica Ascent using Fluent Bit](integrations/list-of-integrations/fluent-bit/forwarding-amazon-linux-logs-to-logiq-using-fluent-bit.md)
    * [Fluent Bit installation on Ubuntu](integrations/list-of-integrations/fluent-bit/fluent-bit-installation-on-ubuntu.md)
    * [Enabling IoT(MQTT) Input (PAAS)](integrations/list-of-integrations/fluent-bit/enabling-iot-mqtt-input-paas.md)
    * [IIS Logs on Windows](integrations/list-of-integrations/fluent-bit/iis-logs-on-windows.md)
  * [Fluentd](integrations/list-of-integrations/fluentd.md)
  * [FortiNet Firewalls](integrations/list-of-integrations/fortinet-firewalls.md)
  * [GCP PubSub](integrations/list-of-integrations/gcp-pubsub.md)
  * [GCP Cloud Logging](integrations/list-of-integrations/gcp-cloud-logging.md)
  * [IBM QRadar](integrations/list-of-integrations/ibm-qradar.md)
  * [Incident management](integrations/list-of-integrations/alert-destinations.md)
  * [Jaeger](integrations/list-of-integrations/jaeger.md)
  * [Kafka](integrations/list-of-integrations/kafka.md)
  * [Kinesis](integrations/list-of-integrations/kinesis.md)
  * [Kubernetes](integrations/list-of-integrations/kubernetes.md)
  * [Logstash](integrations/list-of-integrations/logstash.md)
  * [MQTT](integrations/list-of-integrations/mqtt.md)
  * [Network Packets](integrations/list-of-integrations/network-packets.md)
  * [OpenTelemetry](integrations/list-of-integrations/opentelemetry.md)
  * [Object store (S3 Compatible)](integrations/list-of-integrations/object-store-s3-compatible.md)
  * [OSSEC Variants (OSSEC/WAZUH/ATOMIC)](integrations/list-of-integrations/ossec-variants-ossec-wazuh-atomic/README.md)
    * [Apica Ascent-OSSEC Agent for Windows](integrations/list-of-integrations/ossec-variants-ossec-wazuh-atomic/logiq-ossec-agent-for-windows.md)
  * [Palo Alto Firewall](integrations/list-of-integrations/palo-alto-firewall.md)
  * [Prometheus](integrations/list-of-integrations/prometheus/README.md)
    * [Spring Boot](integrations/list-of-integrations/prometheus/spring-boot.md)
    * [Prometheus on Windows](integrations/list-of-integrations/prometheus/prometheus-on-windows.md)
    * [Prometheus Remote Write](integrations/list-of-integrations/prometheus/prometheus-remote-write.md)
    * [MongoDB Exporter](integrations/list-of-integrations/prometheus/mongodb-exporter.md)
    * [JMX Exporter](integrations/list-of-integrations/prometheus/jmx-exporter.md)
  * [Rsyslogd](integrations/list-of-integrations/rsyslogd.md)
  * [Syslog](integrations/list-of-integrations/syslog.md)
  * [Syslog-ng](integrations/list-of-integrations/syslog-ng.md)
  * [Splunk Universal Forwarder](integrations/list-of-integrations/splunk-universal-forwarder.md)
  * [Splunk Heavy Forwarder](integrations/list-of-integrations/splunk-heavy-forwarder.md)
  * [SNMP](integrations/list-of-integrations/snmp.md)
  * [Splunk Forwarding Proxy](integrations/list-of-integrations/splunk-forwarding-proxy.md)

## Dashboards

* [Dashboards & Visualizations](dashboards/overview.md)
* [Create Your First Dashboard](dashboards/create-your-first-dashboard.md)
* [Building auto-refreshing Dashboard](dashboards/building-auto-refreshing-dashboard.md)
* [Adding widgets to the Dashboard](dashboards/adding-widgets-to-the-dashboard.md)
* [Using Pre-defined Dashboards](dashboards/using-pre-defined-dashboards.md)
* [Import Grafana Dashboards](dashboards/import-grafana-dashboards.md)

## DATA MANAGEMENT

* [Data Management Overview](data-management/overview.md)
* [Data Explorer Overview](data-management/overview-1/README.md)
  * [Query Builder](data-management/overview-1/query-builder.md)
  * [Widget](data-management/overview-1/widget.md)
  * [Create a Dashboard](data-management/overview-1/create-a-dashboard.md)
  * [Alerts](data-management/overview-1/alerts.md)
  * [JSON Import](data-management/overview-1/json-import.md)
* [Timestamp handling](data-management/timestamp-handling/README.md)
  * [Timestamp bookmark](data-management/timestamp-handling/timestamp-bookmark.md)
* [Large log/events/metrics/traces](data-management/large-log-events-metrics-traces.md)

## COMMAND LINE INTERFACE

* [apicactl Documentation](https://github.com/ApicaSystem/apicactl)

## Flow

* [Flow Documentation](https://logflow-docs.logiq.ai/)
* [Data Flow Pipelines](flow/data-flow-pipelines.md)
* [Rules](flow/rules/README.md)
  * [FILTER](flow/rules/filter.md)
  * [EXTRACT](flow/rules/extract.md)
  * [SIEM and TAG](flow/rules/siem-and-tag.md)
  * [REWRITE](flow/rules/rewrite.md)
  * [CODE](flow/rules/code.md)
  * [FORWARD](flow/rules/forward/README.md)
    * [Rename Attributes](flow/rules/forward/rename-attributes.md)

## FLEET MANAGEMENT

* [Fleet Management Overview](fleet-management/fleet.md)

## Infra & Application Monitoring

* [Monitoring Overview](infra-and-application-monitoring/prometheus/README.md)
  * [Connecting Prometheus](infra-and-application-monitoring/prometheus/connecting-prometheus.md)
  * [Connecting Amazon Managed Service for Prometheus](infra-and-application-monitoring/prometheus/connecting-amazon-managed-service-for-prometheus.md)
* [Writing queries](infra-and-application-monitoring/querying-data.md)
* [Windows Redis Monitoring](infra-and-application-monitoring/windows-redis-monitoring.md)

## LOG MANAGEMENT

* [Log Management Overview](log-management/log-management-overview.md)
* [Terminology](log-management/logs-terminology.md)
* [Explore Logs](log-management/explore-logs.md)
* [Apica Ascent Search Cheat Sheet](log-management/search-cheat-sheet.md)
* [Share Search Results](log-management/share-search-results.md)
* [Severity Metrics](log-management/severity-metrics.md)
* [Log2Metrics](log-management/metrics-and-custom-indices.md)
* [Reports](log-management/reports/README.md)
  * [Accessing Reports results via API](log-management/reports/accessing-api-results-via-api.md)
* [Role-Based Access Control (RBAC)](log-management/role-based-access-control.md)
* [Configuring RBAC](log-management/configuring-rbac.md)
* [Topology](log-management/topology.md)

***

* [CHECK MANAGEMENT](check-management/README.md)
  * [Check Management Overview](check-management/check-management-overview.md)
  * [Map View](check-management/map-view.md)
  * [List View](check-management/list-view.md)

## Distributed Tracing

* [Distributed Tracing Overview](distributed-tracing/overview.md)
* [Traces](distributed-tracing/traces.md)
* [Logs](distributed-tracing/logs.md)

## AUTONOMOUS INSIGHTS <a href="#logiq-events" id="logiq-events"></a>

* [Time Series AI-ML](logiq-events/time-series-ai-ml/README.md)
  * [Anomaly Detection](logiq-events/time-series-ai-ml/anomaly-detection.md)
  * [Averaging](logiq-events/time-series-ai-ml/averaging.md)
  * [Standard Deviation(STD)](logiq-events/time-series-ai-ml/standard-deviation-std.md)
  * [Forecasting](logiq-events/time-series-ai-ml/forecasting.md)
  * [AI-ML on PromQL Query Data Set](logiq-events/time-series-ai-ml/ai-ml-on-promql-query-data-set.md)
  * [Statistical Data Description](logiq-events/time-series-ai-ml/statistical-data-description.md)
* [Pattern-Signature (PS)](logiq-events/log-pattern-signature/README.md)
  * [Log PS Explained](logiq-events/log-pattern-signature/log-ps-explained/README.md)
    * [Unstructured Logs](logiq-events/log-pattern-signature/log-ps-explained/unstructured-logs.md)
    * [Semi-structured JSON](logiq-events/log-pattern-signature/log-ps-explained/semi-structured-json.md)
    * [Reduce Logs Based on PS](logiq-events/log-pattern-signature/log-ps-explained/reduce-logs-based-on-ps.md)
    * [Log PS Use Cases](logiq-events/log-pattern-signature/log-ps-explained/log-ps-use-cases/README.md)
      * [Log Outlier Isolation](logiq-events/log-pattern-signature/log-ps-explained/log-ps-use-cases/log-outlier-isolation.md)
      * [Log Trending Analysis](logiq-events/log-pattern-signature/log-ps-explained/log-ps-use-cases/log-trending-analysis.md)
      * [Simple Log Compare](logiq-events/log-pattern-signature/log-ps-explained/log-ps-use-cases/log-compare.md)
  * [Config PS](logiq-events/log-pattern-signature/config-ps/README.md)
    * [Config JSON PS](logiq-events/log-pattern-signature/config-ps/config-json-ps.md)
* [ALIVE Log Visualization](logiq-events/autonomous-log-interactive-visual-explorer-alive/README.md)
  * [ALIVE Pattern Signature Summary](logiq-events/autonomous-log-interactive-visual-explorer-alive/alive-pattern-signature-summary.md)
  * [ALIVE Log Compare](logiq-events/autonomous-log-interactive-visual-explorer-alive/pattern-compare.md)
* [Alerts](logiq-events/alerts.md)
* [Alerts (Simple/Anomaly)](logiq-events/alerts-simple-anomaly.md)
* [Alerts On Logs](logiq-events/alerts-1.md)
* [Rule Packs](logiq-events/rule-packs.md)

## API

* [Query API](api/historical-data.md)
* [Use Apica API to ingest JSON data](api/use-apica-api-to-ingest-json-data.md)

## RELEASE NOTES

* [Release Notes](release-notes/release-notes/README.md)
  * [Ascent 2.4.0](release-notes/release-notes/ascent-2.4.0.md)
  * [Ascent 2.3.0](release-notes/release-notes/ascent-2.3.0.md)
  * [Ascent 2.2.0](release-notes/release-notes/load-test.md)
  * [Ascent 2.1.0](release-notes/release-notes/ascent-2.1.0/README.md)
    * [Data Fabric](release-notes/release-notes/ascent-2.1.0/release-notes/README.md)
      * [Releases-old](release-notes/release-notes/ascent-2.1.0/release-notes/release-notes.md)
    * [Synthetic Monitoring](release-notes/release-notes/ascent-2.1.0/synthetic-monitoring.md)
    * [Advanced Scripting Engine](release-notes/release-notes/ascent-2.1.0/advanced-scripting-engine.md)
    * [IRONdb](release-notes/release-notes/ascent-2.1.0/irondb.md)
  * [Synthetic Monitoring](https://apica-kb.atlassian.net/wiki/spaces/ASMDOCS/pages/2140241932/Release+Notes)

## Administration <a href="#logiq-ui-configuration" id="logiq-ui-configuration"></a>

* [E-Mail Configuration](logiq-ui-configuration/email-configuration-setup.md)
* [Single Sign-On with SAML](logiq-ui-configuration/single-sign-on-configuration.md)
* [Audit Trail](logiq-ui-configuration/audit-trail/README.md)
  * [Events Trail](logiq-ui-configuration/audit-trail/events-trail.md)
  * [Alerts Trail](logiq-ui-configuration/audit-trail/alerts-trail.md)

## TBD
