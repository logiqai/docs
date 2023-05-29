# Table of contents

## Introduction

* [Overview](README.md)
* [User Interface](introduction/the-logiq-ui.md)
* [Release Notes 🚀](introduction/release-notes/README.md)
  * [Releases-old](introduction/release-notes/release-notes.md)

## EULA

* [End User License Agreement](eula/eula.md)

## Deploying LOGIQ

* [Quickstart with Docker-Compose](deploying-logiq/quickstart-with-docker-compose.md)
* [SaaS](deploying-logiq/logiq-saas.md)
* [PaaS deployment](deploying-logiq/logiq-paas-deployment/README.md)
  * [Deploying LOGIQ PaaS on Kubernetes](deploying-logiq/logiq-paas-deployment/k8s-quickstart-guide.md)
  * [Deploying LOGIQ PaaS on MicroK8s](deploying-logiq/logiq-paas-deployment/deploying-logiq-paas-on-microk8s.md)
  * [Deploying LOGIQ PaaS on AWS](deploying-logiq/logiq-paas-deployment/aws-cloudformation.md)
  * [Deploying LOGIQ EKS on AWS using CloudFormation](deploying-logiq/deploying-logiq-eks-on-aws-using-cloudformation.md)
  * [Deploying LOGIQ EKS on AWS using custom AMI](deploying-logiq/deploying-logiq-eks-on-aws-using-custom-ami.md)
  * [Deploying Logiq EKS with AWS ALB](deploying-logiq/logiq-paas-deployment/deploying-logiq-eks-with-aws-alb.md)
  * [Deploying LOGIQ PaaS in Azure Kubernetes Service](deploying-logiq/logiq-paas-deployment/deploying-logiq-paas-in-azure-kubernetes-service/README.md)
    * [Azure Blob Storage Lifecycle Management](deploying-logiq/logiq-paas-deployment/deploying-logiq-paas-in-azure-kubernetes-service/azure-blob-storage-lifecycle-management.md)

## Dashboards

* [Overview](dashboards/overview.md)
* [Create Your First Dashboard](dashboards/create-your-first-dashboard.md)
* [Building auto-refreshing Dashboard](dashboards/building-auto-refreshing-dashboard.md)
* [Adding widgets to the Dashboard](dashboards/adding-widgets-to-the-dashboard.md)
* [Using Pre-defined Dashboards](dashboards/using-pre-defined-dashboards.md)
* [Import Grafana Dashboards](dashboards/import-grafana-dashboards.md)

## COMMAND LINE INTERFACE

* [logiqctl Documentation](https://logiqctl.logiq.ai/)

## Logflow

* [Logflow Documentation](https://logflow-docs.logiq.ai/)

## INTEGRATIONS

* [Overview](integrations/overview/README.md)
  * [Generating a secure ingest token](integrations/overview/generating-a-secure-ingest-token.md)
* [Apache Beam](integrations/apache-beam/README.md)
  * [Export Metrics to Prometheus](integrations/apache-beam/export-metrics-to-prometheus/README.md)
    * [Pull Mechanism via Push-Gateway](integrations/apache-beam/export-metrics-to-prometheus/pull-mechanism-via-push-gateway.md)
  * [Export Events to LOGIQ](integrations/apache-beam/export-events-to-logiq.md)
* [AWS](integrations/aws/README.md)
  * [AWS CloudWatch](integrations/aws/aws-cloudwatch-exporter.md)
  * [AWS ECS](integrations/aws/aws-ecs/README.md)
    * [Forwarding AWS ECS logs to LOGIQ using AWS FireLens](integrations/aws/aws-ecs/forwarding-aws-ecs-logs-to-logiq-using-aws-firelens.md)
    * [ECS prometheus metrics to Logiq](integrations/aws/aws-ecs/ecs-prometheus-metrics-to-logiq.md)
  * [AWS S3](integrations/aws/aws-s3.md)
* [Azure Databricks](integrations/azure-databricks.md)
* [Azure Event Hubs](integrations/azure-event-hubs.md)
* [Docker Compose](integrations/docker-compose.md)
* [Docker Swarm logging](integrations/docker-swarm-logging.md)
* [Docker Syslog log driver](integrations/docker-syslog-log-driver.md)
* [Azure Eventhub](integrations/azure-eventhub.md)
* [Filebeat](integrations/filebeat.md)
* [Fluent Bit](integrations/fluent-bit/README.md)
  * [Forwarding Amazon-Linux logs to LOGIQ using Fluent Bit](integrations/fluent-bit/forwarding-amazon-linux-logs-to-logiq-using-fluent-bit.md)
  * [Fluent Bit installation on Ubuntu](integrations/fluent-bit/fluent-bit-installation-on-ubuntu.md)
  * [Enabling IoT(MQTT) Input (PAAS)](integrations/fluent-bit/enabling-iot-mqtt-input-paas.md)
  * [IIS Logs on Windows](integrations/fluent-bit/iis-logs-on-windows.md)
* [Fluentd](integrations/fluentd.md)
* [FortiNet Firewalls](integrations/fortinet-firewalls.md)
* [GCP PubSub](integrations/gcp-pubsub.md)
* [GCP Cloud Logging](integrations/gcp-cloud-logging.md)
* [Incident management](integrations/alert-destinations.md)
* [Jaeger](integrations/jaeger.md)
* [Kafka](integrations/kafka.md)
* [Kinesis](integrations/kinesis.md)
* [IBM QRadar](integrations/ibm-qradar.md)
* [Kubernetes](integrations/kubernetes.md)
* [Logstash](integrations/logstash.md)
* [MQTT](integrations/mqtt.md)
* [Network Packets](integrations/network-packets.md)
* [OpenTelemetry](integrations/opentelemetry.md)
* [Object store (S3 Compatible)](integrations/object-store-s3-compatible.md)
* [OSSEC Variants (OSSEC/WAZUH/ATOMIC)](integrations/ossec-variants-ossec-wazuh-atomic/README.md)
  * [LOGIQ-OSSEC Agent for Windows](integrations/ossec-variants-ossec-wazuh-atomic/logiq-ossec-agent-for-windows.md)
* [Palo Alto Firewall](integrations/palo-alto-firewall.md)
* [Prometheus](integrations/prometheus/README.md)
  * [Spring Boot](integrations/prometheus/spring-boot.md)
  * [Prometheus on Windows](integrations/prometheus/prometheus-on-windows.md)
  * [Prometheus Remote Write](integrations/prometheus/prometheus-remote-write.md)
  * [MongoDB Exporter](integrations/prometheus/mongodb-exporter.md)
  * [JMX Exporter](integrations/prometheus/jmx-exporter.md)
* [Rsyslogd](integrations/rsyslogd.md)
* [Syslog-ng](integrations/syslog-ng.md)
* [Splunk Universal Forwarder](integrations/splunk-universal-forwarder.md)
* [Splunk Heavy Forwarder](integrations/splunk-heavy-forwarder.md)

***

* [LOGIQ.AI Observability Data Collector Agent](logiq.ai-observability-data-collector-agent.md)

## DATA MANAGEMENT

* [Overview](data-management/overview.md)
* [Rules](data-management/rules.md)
* [Extract](data-management/extract.md)
* [Filter](data-management/filter.md)
* [Rewrite](data-management/rewrite.md)
* [SIEM and TAG](data-management/siem-and-tag.md)
* [Forward](data-management/forward.md)
* [Rename Attributes](data-management/rename-attributes.md)
* [Timestamp handling](data-management/timestamp-handling.md)
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
* [LOGIQ Search Cheat Sheet](log-management/search-cheat-sheet.md)
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

* [Log Pattern-Signature](logiq-events/log-pattern-signature.md)
* [Autonomous Log Interactive Visual Explorer (ALIVE)](logiq-events/autonomous-log-interactive-visual-explorer-alive.md)
* [Time Series (AI/ML)](logiq-events/time-series-ai-ml/README.md)
  * [Anomaly Detection](logiq-events/time-series-ai-ml/anomaly-detection.md)
  * [Averaging](logiq-events/time-series-ai-ml/averaging.md)
  * [Standard Deviation(STD)](logiq-events/time-series-ai-ml/standard-deviation-std.md)
  * [Forecasting](logiq-events/time-series-ai-ml/forecasting.md)
* [Alerts](logiq-events/alerts.md)
* [Alerts (Simple/Anomaly)](logiq-events/alerts-simple-anomaly.md)
* [Alerts On Logs](logiq-events/alerts-1.md)
* [Rule Packs](logiq-events/rule-packs.md)

## DATA SOURCES

* [Overview](data-sources/overview.md)
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

## API

* [Query API](api/historical-data.md)

## Administration <a href="#logiq-ui-configuration" id="logiq-ui-configuration"></a>

* [E-Mail Configuration](logiq-ui-configuration/email-configuration-setup.md)
* [Single Sign-On with SAML](logiq-ui-configuration/single-sign-on-configuration.md)
* [Audit Trail](logiq-ui-configuration/audit-trail/README.md)
  * [Events Trail](logiq-ui-configuration/audit-trail/events-trail.md)
  * [Alerts Trail](logiq-ui-configuration/audit-trail/alerts-trail.md)
