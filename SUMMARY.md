# Table of contents

* [Welcome to Apica Docs!](README.md)

## PRODUCT OVERVIEW

* [Ascent Overview](product-overview/ascent-overview.md)
* [Ascent User Interface](product-overview/the-logiq-ui.md)
* [Synthetic Monitoring](https://apica-kb.atlassian.net/wiki/spaces/ASMDOCS/pages/2177269761/ASM+Platform+Overview)
* [Loadtesting](https://apica-kb.atlassian.net/wiki/spaces/ALTDOCS/pages/5538148/Overview+of+the+Apica+Load+Test+Solution)
* [Advanced Scripting Engine](https://apica-kb.atlassian.net/wiki/spaces/DAZT/pages/5674203/What+is+ZebraTester)

## GETTING STARTED

* [Deploying Apica Ascent](getting-started/deploying-apica-ascent/README.md)
  * [Quickstart with Docker-Compose](getting-started/deploying-apica-ascent/quickstart-with-docker-compose.md)
  * [SaaS](getting-started/deploying-apica-ascent/logiq-saas.md)
  * [PaaS Deployment Architecture](getting-started/deploying-apica-ascent/paas-deployment-architecture.md)
  * [PaaS deployment](getting-started/deploying-apica-ascent/logiq-paas-deployment/README.md)
    * [Deploying Apica Ascent PaaS on Kubernetes](getting-started/deploying-apica-ascent/logiq-paas-deployment/k8s-quickstart-guide.md)
    * [Deploying Apica Ascent PaaS on MicroK8s](getting-started/deploying-apica-ascent/logiq-paas-deployment/deploying-logiq-paas-on-microk8s.md)
    * [Deploying Apica Ascent PaaS on AWS](getting-started/deploying-apica-ascent/logiq-paas-deployment/aws-cloudformation.md)
    * [Deploying Apica Ascent EKS on AWS using CloudFormation](getting-started/deploying-apica-ascent/logiq-paas-deployment/deploying-logiq-eks-on-aws-using-cloudformation.md)
    * [Deploying Ascent on AWS EKS with Aurora PostgreSQL and ElastiCache Redis using Cloud Formation](getting-started/deploying-apica-ascent/logiq-paas-deployment/deploying-ascent-on-aws-eks-with-aurora-postgresql-and-elasticache-redis-using-cloud-formation/README.md)
      * [Deploying Apica Ascent on AWS EKS with Aurora PostgreSQL and ElastiCache Redis using CloudFormation](getting-started/deploying-apica-ascent/logiq-paas-deployment/deploying-ascent-on-aws-eks-with-aurora-postgresql-and-elasticache-redis-using-cloud-formation/deploying-apica-ascent-on-aws-eks-with-aurora-postgresql-and-elasticache-redis-using-cloudformation.md)
      * [Apica Ascent on AWS EKS (Private Endpoint) with Aurora PostgreSQL and ElastiCache Redis on prod VPC](getting-started/deploying-apica-ascent/logiq-paas-deployment/deploying-ascent-on-aws-eks-with-aurora-postgresql-and-elasticache-redis-using-cloud-formation/apica-ascent-on-aws-eks-private-endpoint-with-aurora-postgresql-and-elasticache-redis-on-prod-vpc.md)
    * [Deploying Apica Ascent EKS on AWS using custom AMI](getting-started/deploying-apica-ascent/logiq-paas-deployment/deploying-logiq-eks-on-aws-using-custom-ami.md)
    * [Deploying Apica Ascent EKS with AWS ALB](getting-started/deploying-apica-ascent/logiq-paas-deployment/deploying-logiq-eks-with-aws-alb.md)
    * [Deploying Apica Ascent PaaS in Azure Kubernetes Service](getting-started/deploying-apica-ascent/logiq-paas-deployment/deploying-logiq-paas-in-azure-kubernetes-service/README.md)
      * [Azure Blob Storage Lifecycle Management](getting-started/deploying-apica-ascent/logiq-paas-deployment/deploying-logiq-paas-in-azure-kubernetes-service/azure-blob-storage-lifecycle-management.md)

## RELEASE NOTES

* [Release Notes](release-notes/release-notes/README.md)
  * [Ascent 2.3.0](release-notes/release-notes/ascent-2.3.0.md)
  * [Ascent 2.2.0](release-notes/release-notes/load-test.md)
  * [Ascent 2.1.0](release-notes/release-notes/ascent-2.1.0/README.md)
    * [Data Fabric](release-notes/release-notes/ascent-2.1.0/release-notes/README.md)
      * [Releases-old](release-notes/release-notes/ascent-2.1.0/release-notes/release-notes.md)
    * [Synthetic Monitoring](release-notes/release-notes/ascent-2.1.0/synthetic-monitoring.md)
    * [Advanced Scripting Engine](release-notes/release-notes/ascent-2.1.0/advanced-scripting-engine.md)
    * [IRONdb](release-notes/release-notes/ascent-2.1.0/irondb.md)
  * [Synthetic Monitoring](https://apica-kb.atlassian.net/wiki/spaces/ASMDOCS/pages/2140241932/Release+Notes)

## DATA SOURCES

* [Integrations Overview](data-sources/overview/README.md)
  * [Generating a secure ingest token](data-sources/overview/generating-a-secure-ingest-token.md)
  * [Data Ingest Ports](data-sources/overview/data-ingest-ports.md)
* [Data Source Details](data-sources/data-source-details/README.md)
  * [Apache Beam](data-sources/data-source-details/apache-beam/README.md)
    * [Export Metrics to Prometheus](data-sources/data-source-details/apache-beam/export-metrics-to-prometheus/README.md)
      * [Pull Mechanism via Push-Gateway](data-sources/data-source-details/apache-beam/export-metrics-to-prometheus/pull-mechanism-via-push-gateway.md)
    * [Export Events to Apica Ascent](data-sources/data-source-details/apache-beam/export-events-to-logiq.md)
  * [Apica ASM](data-sources/data-source-details/apica-asm.md)
  * [Apica Ascent Observability Data Collector Agent](data-sources/data-source-details/logiq.ai-observability-data-collector-agent.md)
  * [AWS](data-sources/data-source-details/aws/README.md)
    * [AWS CloudWatch](data-sources/data-source-details/aws/aws-cloudwatch-exporter.md)
    * [AWS ECS](data-sources/data-source-details/aws/aws-ecs/README.md)
      * [Forwarding AWS ECS logs to Apica Ascent using AWS FireLens](data-sources/data-source-details/aws/aws-ecs/forwarding-aws-ecs-logs-to-logiq-using-aws-firelens.md)
      * [ECS prometheus metrics to Apica Ascent](data-sources/data-source-details/aws/aws-ecs/ecs-prometheus-metrics-to-logiq.md)
    * [AWS S3](data-sources/data-source-details/aws/aws-s3.md)
  * [Azure Databricks](data-sources/data-source-details/azure-databricks.md)
  * [Azure Eventhub](data-sources/data-source-details/azure-eventhub.md)
  * [Azure Event Hubs](data-sources/data-source-details/azure-event-hubs.md)
  * [Docker Compose](data-sources/data-source-details/docker-compose.md)
  * [Docker Swarm logging](data-sources/data-source-details/docker-swarm-logging.md)
  * [Docker Syslog log driver](data-sources/data-source-details/docker-syslog-log-driver.md)
  * [F5 Big-Ip System](data-sources/data-source-details/f5-big-ip-system.md)
  * [Filebeat](data-sources/data-source-details/filebeat.md)
  * [Fluent Bit](data-sources/data-source-details/fluent-bit/README.md)
    * [Forwarding Amazon-Linux logs to Apica Ascent using Fluent Bit](data-sources/data-source-details/fluent-bit/forwarding-amazon-linux-logs-to-logiq-using-fluent-bit.md)
    * [Fluent Bit installation on Ubuntu](data-sources/data-source-details/fluent-bit/fluent-bit-installation-on-ubuntu.md)
    * [Enabling IoT(MQTT) Input (PAAS)](data-sources/data-source-details/fluent-bit/enabling-iot-mqtt-input-paas.md)
    * [IIS Logs on Windows](data-sources/data-source-details/fluent-bit/iis-logs-on-windows.md)
  * [Fluentd](data-sources/data-source-details/fluentd.md)
  * [FortiNet Firewalls](data-sources/data-source-details/fortinet-firewalls.md)
  * [GCP PubSub](data-sources/data-source-details/gcp-pubsub.md)
  * [GCP Cloud Logging](data-sources/data-source-details/gcp-cloud-logging.md)
  * [IBM QRadar](data-sources/data-source-details/ibm-qradar.md)
  * [Incident management](data-sources/data-source-details/alert-destinations.md)
  * [Jaeger](data-sources/data-source-details/jaeger.md)
  * [Kafka](data-sources/data-source-details/kafka.md)
  * [Kinesis](data-sources/data-source-details/kinesis.md)
  * [Kubernetes](data-sources/data-source-details/kubernetes.md)
  * [Logstash](data-sources/data-source-details/logstash.md)
  * [MQTT](data-sources/data-source-details/mqtt.md)
  * [Network Packets](data-sources/data-source-details/network-packets.md)
  * [OpenTelemetry](data-sources/data-source-details/opentelemetry.md)
  * [Object store (S3 Compatible)](data-sources/data-source-details/object-store-s3-compatible.md)
  * [OSSEC Variants (OSSEC/WAZUH/ATOMIC)](data-sources/data-source-details/ossec-variants-ossec-wazuh-atomic/README.md)
    * [Apica Ascent-OSSEC Agent for Windows](data-sources/data-source-details/ossec-variants-ossec-wazuh-atomic/logiq-ossec-agent-for-windows.md)
  * [Palo Alto Firewall](data-sources/data-source-details/palo-alto-firewall.md)
  * [Prometheus](data-sources/data-source-details/prometheus/README.md)
    * [Spring Boot](data-sources/data-source-details/prometheus/spring-boot.md)
    * [Prometheus on Windows](data-sources/data-source-details/prometheus/prometheus-on-windows.md)
    * [Prometheus Remote Write](data-sources/data-source-details/prometheus/prometheus-remote-write.md)
    * [MongoDB Exporter](data-sources/data-source-details/prometheus/mongodb-exporter.md)
    * [JMX Exporter](data-sources/data-source-details/prometheus/jmx-exporter.md)
  * [Rsyslogd](data-sources/data-source-details/rsyslogd.md)
  * [Syslog](data-sources/data-source-details/syslog.md)
  * [Syslog-ng](data-sources/data-source-details/syslog-ng.md)
  * [Splunk Universal Forwarder](data-sources/data-source-details/splunk-universal-forwarder.md)
  * [Splunk Heavy Forwarder](data-sources/data-source-details/splunk-heavy-forwarder.md)
  * [SNMP](data-sources/data-source-details/snmp.md)

## Dashboards

* [Dashboards & Visualizations](dashboards/overview.md)
* [Create Your First Dashboard](dashboards/create-your-first-dashboard.md)
* [Building auto-refreshing Dashboard](dashboards/building-auto-refreshing-dashboard.md)
* [Adding widgets to the Dashboard](dashboards/adding-widgets-to-the-dashboard.md)
* [Using Pre-defined Dashboards](dashboards/using-pre-defined-dashboards.md)
* [Import Grafana Dashboards](dashboards/import-grafana-dashboards.md)

***

* [Data Explorer Overview](overview/README.md)
  * [Query Builder](overview/query-builder.md)
  * [Widget](overview/widget.md)
  * [Create a Dashboard](overview/create-a-dashboard.md)

## COMMAND LINE INTERFACE

* [apicactl Documentation](https://logiqctl.logiq.ai/)

## TBD

## Logflow

* [Logflow Documentation](https://logflow-docs.logiq.ai/)

## Fleet

* [Fleet](fleet/fleet.md)

## DATA MANAGEMENT

* [Overview](data-management/overview.md)
* [Rules](data-management/rules/README.md)
  * [FILTER](data-management/rules/filter.md)
  * [EXTRACT](data-management/rules/extract.md)
  * [SIEM and TAG](data-management/rules/siem-and-tag.md)
  * [REWRITE](data-management/rules/rewrite.md)
  * [CODE](data-management/rules/code.md)
  * [FORWARD](data-management/rules/forward/README.md)
    * [Rename Attributes](data-management/rules/forward/rename-attributes.md)
* [Timestamp handling](data-management/timestamp-handling/README.md)
  * [Timestamp bookmark](data-management/timestamp-handling/timestamp-bookmark.md)
* [Large log/events/metrics/traces](data-management/large-log-events-metrics-traces.md)

## Infra & Application Monitoring

* [Overview](infra-and-application-monitoring/prometheus/README.md)
  * [Connecting Prometheus](infra-and-application-monitoring/prometheus/connecting-prometheus.md)
  * [Connecting Amazon Managed Service for Prometheus](infra-and-application-monitoring/prometheus/connecting-amazon-managed-service-for-prometheus.md)
* [Writing queries](infra-and-application-monitoring/querying-data.md)
* [Windows Redis Monitoring](infra-and-application-monitoring/windows-redis-monitoring.md)

## LOG MANAGEMENT

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

* [Data Flow Pipelines](data-flow-pipelines.md)

## Distributed Tracing

* [Overview](distributed-tracing/overview.md)
* [Traces](distributed-tracing/traces.md)
* [Logs](distributed-tracing/logs.md)

## AUTONOMOUS INSIGHTS <a href="#logiq-events" id="logiq-events"></a>

* [Pattern-Signature (PS)](logiq-events/log-pattern-signature/README.md)
  * [Log PS Explained](logiq-events/log-pattern-signature/log-ps-explained/README.md)
    * [Unstructured Logs](logiq-events/log-pattern-signature/log-ps-explained/unstructured-logs.md)
    * [Semi-structured JSON](logiq-events/log-pattern-signature/log-ps-explained/semi-structured-json.md)
    * [Reduce Logs Based on PS](logiq-events/log-pattern-signature/log-ps-explained/reduce-logs-based-on-ps.md)
    * [Log PS Use Cases](logiq-events/log-pattern-signature/log-ps-explained/log-ps-use-cases/README.md)
      * [Log Outlier Isolation](logiq-events/log-pattern-signature/log-ps-explained/log-ps-use-cases/log-outlier-isolation.md)
      * [Log Trending Analysis](logiq-events/log-pattern-signature/log-ps-explained/log-ps-use-cases/log-trending-analysis.md)
      * [Log Compare](logiq-events/log-pattern-signature/log-ps-explained/log-ps-use-cases/log-compare.md)
      * [Pattern Compare](logiq-events/log-pattern-signature/log-ps-explained/log-ps-use-cases/pattern-compare.md)
  * [Config PS](logiq-events/log-pattern-signature/config-ps/README.md)
    * [Config JSON PS](logiq-events/log-pattern-signature/config-ps/config-json-ps.md)
* [ALIVE Log Visualizer](logiq-events/autonomous-log-interactive-visual-explorer-alive.md)
* [Time Series AI-ML](logiq-events/time-series-ai-ml/README.md)
  * [Anomaly Detection](logiq-events/time-series-ai-ml/anomaly-detection.md)
  * [Averaging](logiq-events/time-series-ai-ml/averaging.md)
  * [Standard Deviation(STD)](logiq-events/time-series-ai-ml/standard-deviation-std.md)
  * [Forecasting](logiq-events/time-series-ai-ml/forecasting.md)
  * [AI-ML on PromQL Query Data Set](logiq-events/time-series-ai-ml/ai-ml-on-promql-query-data-set.md)
* [Alerts](logiq-events/alerts.md)
* [Alerts (Simple/Anomaly)](logiq-events/alerts-simple-anomaly.md)
* [Alerts On Logs](logiq-events/alerts-1.md)
* [Rule Packs](logiq-events/rule-packs.md)

## DATA SOURCES

* [Overview](data-sources-1/overview.md)
* [API](data-sources-1/api/README.md)
  * [JSON Data source](data-sources-1/api/json-data-source.md)
  * [RSS](data-sources-1/api/rss.md)
* [AWS](data-sources-1/aws/README.md)
  * [Amazon Athena](data-sources-1/aws/amazon-athena.md)
  * [Amazon CloudWatch ( YAML )](data-sources-1/aws/amazon-cloudwatch-yaml.md)
  * [Amazon Elasticsearch Service](data-sources-1/aws/amazon-elasticsearch-service.md)
  * [Amazon Redshift](data-sources-1/aws/amazon-redshift.md)
  * [MySQL Server (Amazon RDS)](data-sources-1/aws/mysql-server-amazon-rds.md)
* [NoSQL Data Sources](data-sources-1/nosql-data-sources/README.md)
  * [MongoDB](data-sources-1/nosql-data-sources/mongodb.md)
* [OLAP](data-sources-1/olap/README.md)
  * [Data Bricks](data-sources-1/olap/data-bricks.md)
  * [Druid](data-sources-1/olap/druid.md)
  * [Snowflake](data-sources-1/olap/snowflake.md)
* [SQL Data Sources](data-sources-1/sql-data-sources/README.md)
  * [PostgreSQL](data-sources-1/sql-data-sources/postgresql.md)
  * [Microsoft SQL Server](data-sources-1/sql-data-sources/microsoft-sql-server.md)
  * [MySQL Server](data-sources-1/sql-data-sources/mysql-server.md)
* [Time Series Databases](data-sources-1/time-series-databases/README.md)
  * [Prometheus Compatible](data-sources-1/time-series-databases/prometheus-compatible.md)
  * [Elasticsearch](data-sources-1/time-series-databases/elasticsearch-data-source.md)
  * [InfluxDB](data-sources-1/time-series-databases/influxdb.md)

## API

* [Query API](api/historical-data.md)
* [Use Apica API to ingest JSON data](api/use-apica-api-to-ingest-json-data.md)

## Administration <a href="#logiq-ui-configuration" id="logiq-ui-configuration"></a>

* [E-Mail Configuration](logiq-ui-configuration/email-configuration-setup.md)
* [Single Sign-On with SAML](logiq-ui-configuration/single-sign-on-configuration.md)
* [Audit Trail](logiq-ui-configuration/audit-trail/README.md)
  * [Events Trail](logiq-ui-configuration/audit-trail/events-trail.md)
  * [Alerts Trail](logiq-ui-configuration/audit-trail/alerts-trail.md)
