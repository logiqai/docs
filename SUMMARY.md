# Table of contents

## Introduction

* [Overview](README.md)
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
  * [AWS S3](integrations/aws/aws-s3.md)
  * [AWS CloudWatch](integrations/aws/aws-cloudwatch-exporter.md)
  * [AWS ECS](integrations/aws/aws-ecs/README.md)
    * [Forwarding AWS ECS logs to LOGIQ using AWS FireLens](integrations/aws/aws-ecs/forwarding-aws-ecs-logs-to-logiq-using-aws-firelens.md)
    * [ECS prometheus metrics to Logiq](integrations/aws/aws-ecs/ecs-prometheus-metrics-to-logiq.md)
* [Azure Databricks](integrations/azure-databricks.md)
* [Azure Event Hubs](integrations/azure-event-hubs.md)
* [Docker Syslog log driver](integrations/docker-syslog-log-driver.md)
* [Docker Swarm logging](integrations/docker-swarm-logging.md)
* [Filebeat](integrations/filebeat.md)
* [Fluent Bit](integrations/fluent-bit/README.md)
  * [Forwarding Amazon-Linux logs to LOGIQ using Fluent Bit](integrations/fluent-bit/forwarding-amazon-linux-logs-to-logiq-using-fluent-bit.md)
  * [Fluent Bit installation on Ubuntu](integrations/fluent-bit/fluent-bit-installation-on-ubuntu.md)
  * [Enabling IoT(MQTT) Input  (PAAS)](integrations/fluent-bit/enabling-iot-mqtt-input-paas.md)
* [Fluentd](integrations/fluentd.md)
* [FortiNet Firewalls](integrations/fortinet-firewalls.md)
* [GCP Cloud Logging](integrations/gcp-cloud-logging.md)
* [IIS Logs on Windows](integrations/iis-logs-on-windows.md)
* [Incident management](logiq-ui-configuration/alert-destinations.md)
* [Kafka](integrations/kafka.md)
* [Logstash](integrations/logstash.md)
* [MQTT](integrations/mqtt.md)
* [Open Telemetry](integrations/open-telemetry.md)
* [Palo Alto Firewall](integrations/palo-alto-firewall.md)
* [Prometheus](integrations/prometheus.md)
* [Prometheus on Windows](integrations/prometheus-on-windows.md)
* [Rsyslogd](integrations/rsyslogd.md)

## DATA MANAGEMENT

* [Data extraction](data-management/data-extraction.md)
* [Log Data Rewrite](data-management/data-rewrite.md)
* [Timestamp handling](data-management/timestamp-handling.md)

## Monitoring

* [Prometheus Data source](monitoring/querying-data/README.md)
  * [Application Monitoring](monitoring/querying-data/application-monitoring/README.md)
    * [Spring Boot](monitoring/querying-data/application-monitoring/spring-boot.md)
* [Elasticsearch Data source](monitoring/elasticsearch-data-source.md)
* [JSON Data source](monitoring/json-data-source.md)
* [Prometheus Remote Write](monitoring/prometheus-remote-write.md)

## LOG MANAGEMENT

* [The LOGIQ UI](log-management/the-logiq-ui.md)
* [Terminology](log-management/logs-terminology.md)
* [Logs Page](log-management/logs-page.md)
* [Search Page](log-management/search-page/README.md)
  * [Share Search Results](log-management/search-page/share-search-results.md)
  * [LOGIQ Search Cheat Sheet](log-management/search-page/search-cheat-sheet.md)
* [Metrics and Custom Indices](log-management/metrics-and-custom-indices.md)
* [Reports](log-management/reports/README.md)
  * [Accessing Reports results via API](log-management/reports/accessing-api-results-via-api.md)
* [logiqctl](log-management/logiqctl/README.md)
  * [Configuring logiqctl](log-management/logiqctl/configuring-logiqctl.md)
  * [Obtaining API Key](log-management/logiqctl/obtaining-api-key.md)
* [Role-Based Access Control (RBAC)](log-management/role-based-access-control.md)
* [Configuring RBAC](log-management/configuring-rbac.md)

## AUTONOMOUS INSIGHTS <a href="#logiq-events" id="logiq-events"></a>

* [Events](logiq-events/events.md)
* [Event Rules](logiq-events/event-rules.md)
* [Alertable Events](logiq-events/alerts.md)
* [Logs to time series event visualization](logiq-events/logs-to-time-series-event-visualization.md)
* [Example IIS Log Event Extraction Using Event Rules](logiq-events/example-iis-log-event-extraction-using-event-rules.md)

## API

* [Query API](api/historical-data.md)

## Administration <a href="#logiq-ui-configuration" id="logiq-ui-configuration"></a>

* [E-Mail Configuration](logiq-ui-configuration/email-configuration-setup.md)
* [Single Sign-On with SAML](logiq-ui-configuration/single-sign-on-configuration.md)
* [Audit Trail](logiq-ui-configuration/audit-trail.md)

## Glossary <a href="#logiq-log-ingest-server-configuration" id="logiq-log-ingest-server-configuration"></a>

* [Terminology](logiq-log-ingest-server-configuration/terminology.md)
* [Minimal server configuration](logiq-log-ingest-server-configuration/minimal-server-configuration.md)
* [Server options](logiq-log-ingest-server-configuration/server-options.md)
* [Sources](logiq-log-ingest-server-configuration/sources.md)
* [Destinations](logiq-log-ingest-server-configuration/destinations.md)
* [Filters](logiq-log-ingest-server-configuration/filters.md)
* [Groupings](logiq-log-ingest-server-configuration/groupings.md)
* [Rules](logiq-log-ingest-server-configuration/rules.md)
* [Credentials](logiq-log-ingest-server-configuration/credentials.md)
* [Partitions](logiq-log-ingest-server-configuration/partitions.md)
