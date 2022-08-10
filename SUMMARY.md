# Table of contents

## Introduction

* [Overview](README.md)
* [User Interface](log-management/the-logiq-ui.md)
* [Releases](release-notes.md)

## EULA

* [End User License Agreement](eula/eula.md)

## Deploying LOGIQ

* [Quickstart with Docker-Compose](deploying-logiq/quickstart-guide.md)
* [SaaS](deploying-logiq/logiq-saas.md)
* [PaaS deployment](deploying-logiq/logiq-paas-deployment/README.md)
  * [Deploying LOGIQ PaaS on Kubernetes](deploying-logiq/logiq-paas-deployment/k8s-quickstart-guide.md)
  * [Deploying LOGIQ PaaS on MicroK8s](deploying-logiq/deploying-logiq-paas-on-microk8s.md)
  * [Deploying LOGIQ PaaS on AWS](deploying-logiq/aws-cloudformation.md)
  * [Deploying LOGIQ EKS on AWS using CloudFormation](deploying-logiq/deploying-logiq-eks-on-aws-using-cloudformation.md)
  * [Deploying LOGIQ EKS on AWS using custom AMI](deploying-logiq/deploying-logiq-eks-on-aws-using-custom-ami.md)
  * [Deploying Logiq EKS with AWS ALB](deploying-logiq/deploying-logiq-eks-with-aws-alb.md)
  * [Deploying LOGIQ PaaS in Azure Kubernetes Service](deploying-logiq/deploying-logiq-paas-in-azure-kubernetes-service.md)
    * [Azure Blob Storage Lifecycle Management](deploying-logiq/deploying-logiq-paas-in-azure-kubernetes-service/azure-blob-storage-lifecycle-management.md)

## INTEGRATIONS

* [Overview](integrations/overview.md)
  * [Generating a secure ingest token](integrations/generating-a-secure-ingest-token.md)
* [AWS](integrations/aws/README.md)
  * [AWS CloudWatch](integrations/aws/aws-cloudwatch-exporter.md)
  * [AWS ECS](integrations/aws/aws-ecs/README.md)
    * [Forwarding AWS ECS logs to LOGIQ using AWS FireLens](integrations/aws/aws-ecs/forwarding-aws-ecs-logs-to-logiq-using-aws-firelens.md)
    * [ECS prometheus metrics to Logiq](integrations/aws/aws-ecs/ecs-prometheus-metrics-to-logiq.md)
  * [AWS S3](integrations/aws/aws-s3.md)
* [Azure](integrations/azure/README.md)
  * [Azure Databricks](integrations/azure-databricks.md)
  * [Azure Event Hubs](integrations/azure-event-hubs.md)
* [Docker Syslog log driver](integrations/docker-syslog-log-driver.md)
* [Docker Swarm logging](integrations/docker-swarm-logging.md)
* [Filebeat](integrations/filebeat.md)
* [Fluent Bit](integrations/fluent-bit/README.md)
  * [Forwarding Amazon-Linux logs to LOGIQ using Fluent Bit](integrations/fluent-bit/forwarding-amazon-linux-logs-to-logiq-using-fluent-bit.md)
  * [Fluent Bit installation on Ubuntu](integrations/fluent-bit/fluent-bit-installation-on-ubuntu.md)
  * [Enabling IoT(MQTT) Input  (PAAS)](integrations/fluent-bit/enabling-iot-mqtt-input-paas.md)
  * [IIS Logs on Windows](integrations/fluent-bit/iis-logs-on-windows.md)
* [Fluentd](integrations/fluentd.md)
* [FortiNet Firewalls](integrations/fortinet-firewalls.md)
* [GCP Cloud Logging](integrations/gcp-cloud-logging.md)
* [Incident management](logiq-ui-configuration/alert-destinations.md)
* [Jaeger](integrations/jaeger.md)
* [Kafka](integrations/kafka.md)
* [Kubernetes](integrations/kubernetes.md)
* [Logstash](integrations/logstash.md)
* [MQTT](integrations/mqtt.md)
* [OpenTelemetry](integrations/open-telemetry.md)
* [Palo Alto Firewall](integrations/palo-alto-firewall.md)
* [Prometheus](integrations/prometheus/README.md)
  * [Spring Boot](integrations/prometheus/spring-boot.md)
  * [Prometheus on Windows](integrations/prometheus/prometheus-on-windows.md)
  * [Prometheus Remote Write](monitoring/prometheus-remote-write.md)
* [Rsyslogd](integrations/rsyslogd.md)
* [Syslog-ng](integrations/syslog-ng.md)
* [Splunk Universal Forwarder](integrations/splunk-universal-forwarder.md)

## DATA MANAGEMENT

* [Overview](data-management/overview.md)
* [Rules](data-management/rule-types/README.md)
  * [Filter](data-management/rule-types/filter.md)
  * [Extract](data-management/rule-types/extract.md)
  * [Rewrite](data-management/rule-types/rewrite.md)
  * [SIEM and TAG](data-management/rule-types/siem-and-tag.md)
  * [Forward](data-management/rules/forward.md)
* [Timestamp handling](data-management/timestamp-handling.md)

## Infra & Application Monitoring

* [Overview](monitoring/prometheus/README.md)
  * [Connecting Prometheus](prometheus-monitoring/prometheus/connecting-prometheus.md)
  * [Connecting Amazon Managed Service for Prometheus](data-source-monitoring/prometheus/amazon-managed-service-for-prometheus.md)
* [Writing queries](monitoring/prometheus/querying-data.md)

## LOG MANAGEMENT

* [Terminology](log-management/logs-terminology.md)
* [Explore Logs](log-management/logs-page.md)
  * [LOGIQ Search Cheat Sheet](vewing-logs/search-page/search-cheat-sheet.md)
  * [Share Search Results](log-management/search-page/share-search-results.md)
* [Log2Metrics](log-management/metrics-and-custom-indices.md)
* [Reports](log-management/reports/README.md)
  * [Accessing Reports results via API](log-management/reports/accessing-api-results-via-api.md)
* [logiqctl](log-management/logiqctl/README.md)
  * [Configuring logiqctl](log-management/logiqctl/configuring-logiqctl.md)
  * [Obtaining API Key](log-management/logiqctl/obtaining-api-key.md)
* [Role-Based Access Control (RBAC)](log-management/role-based-access-control.md)
* [Configuring RBAC](log-management/configuring-rbac.md)

## Distributed Tracing

* [Overview](distributed-tracing/overview.md)
* [Traces](distributed-tracing/traces.md)
* [Logs](distributed-tracing/logs.md)

## AUTONOMOUS INSIGHTS <a href="#logiq-events" id="logiq-events"></a>

* [Log Pattern-Signature](logiq-events/log-pattern-signature.md)
* [Time Series Insights](logiq-events/time-series-insights/README.md)
  * [Anomaly Detection](logiq-events/time-series-insights/anomaly-detection.md)
  * [Averaging](logiq-events/time-series-insights/averaging.md)
  * [Standard Deviation(STD)](logiq-events/time-series-insights/standard-deviation-std.md)
  * [Forecasting](logiq-events/time-series-insights/forecasting.md)
* [Alerts On Logs](logiq-events/alerts.md)
* [Rule Packs](logiq-events/events.md)

## DATA SOURCES

* [Overview](data-sources/overview.md)
* [API](data-sources/api/README.md)
  * [JSON Data source](data-sources/api/json-data-source.md)
  * [RSS](data-sources/api/rss.md)
* [OLAP](data-sources/olap/README.md)
  * [Data Bricks](data-sources/olap/data-bricks.md)
  * [Druid](data-sources/olap/druid.md)
  * [Snowflake](data-sources/olap/snowflake.md)
  * [Amazon Redshift](data-sources/olap/amazon-redshift.md)
* [NoSQL Data Sources](data-sources/nosql-data-sources/README.md)
  * [MongoDB](data-sources/nosql-data-sources/mongodb.md)
  * [Amazon Elasticsearch Service](data-sources/nosql-data-sources/amazon-elasticsearch-service.md)
* [SQL Data Sources](data-sources/sql-data-sources/README.md)
  * [PostgreSQL](data-sources/sql-data-sources/postgresql.md)
  * [Amazon Athena](data-sources/sql-data-sources/amazon-athena.md)
  * [Microsoft SQL Server](data-sources/sql-data-sources/microsoft-sql-server.md)
  * [MySQL Server](data-sources/sql-data-sources/mysql-server.md)
  * [MySQL Server (Amazon RDS)](data-sources/sql-data-sources/mysql-server-amazon-rds.md)
  * [Amazon CloudWatch ( YAML )](data-sources/sql-data-sources/amazon-cloudwatch-yaml.md)
* [Time Series Databases](data-sources/time-series-databases/README.md)
  * [Prometheus Compatible](data-sources/time-series-databases/prometheus-compatible.md)
  * [Elasticsearch](data-sources/time-series-databases/elasticsearch-data-source.md)
  * [InfluxDB](data-sources/time-series-databases/influxdb.md)

## API

* [Query API](api/historical-data.md)

## Administration <a href="#logiq-ui-configuration" id="logiq-ui-configuration"></a>

* [E-Mail Configuration](logiq-ui-configuration/email-configuration-setup.md)
* [Single Sign-On with SAML](logiq-ui-configuration/single-sign-on-configuration.md)
* [Audit Trail](logiq-ui-configuration/audit-trail.md)
