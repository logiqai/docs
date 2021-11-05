# Table of contents

* [Overview](README.md)
* [Releases](release-notes.md)

## EULA

* [End User License Agreement](eula/eula.md)

## Deploying LOGIQ

* [LOGIQ SaaS](deploying-logiq/logiq-saas.md)
* [LOGIQ PaaS Quickstart](deploying-logiq/quickstart-guide.md)
* [LOGIQ PaaS Community Edition](deploying-logiq/logiq-paas-community-edition.md)
* [Deploying LOGIQ PaaS on Kubernetes](deploying-logiq/k8s-quickstart-guide.md)
* [Deploying LOGIQ PaaS on MicroK8s](deploying-logiq/deploying-logiq-paas-on-microk8s.md)
* [Deploying LOGIQ PaaS on AWS](deploying-logiq/aws-cloudformation.md)

## INTEGRATIONS

* [Overview](integrations/overview.md)
* [Generating a secure ingest token](integrations/generating-a-secure-ingest-token.md)
* [Logstash](integrations/logstash.md)
* [Fluent Bit](integrations/fluent-bit/README.md)
  * [Forwarding Amazon-Linux logs to LOGIQ using Fluent Bit](integrations/fluent-bit/forwarding-amazon-linux-logs-to-logiq-using-fluent-bit.md)
  * [Fluent Bit installation on Ubuntu](integrations/fluent-bit/fluent-bit-installation-on-ubuntu.md)
* [Fluentd](integrations/fluentd.md)
* [Rsyslogd](integrations/rsyslogd.md)
* [AWS CloudWatch](integrations/aws-cloudwatch-exporter.md)
* [Palo Alto Firewall](integrations/palo-alto-firewall.md)
* [Azure Event Hubs](integrations/azure-event-hubs.md)
* [Configuring Prometheus](integrations/prometheus.md)
* [Docker Syslog log driver](integrations/docker-syslog-log-driver.md)

## Log Insights <a href="logiq-server" id="logiq-server"></a>

* [Data extraction](logiq-server/data-extraction.md)
* [Log Data Rewrite](logiq-server/data-rewrite.md)
* [Timestamp handling](logiq-server/timestamp-handling.md)

## LOGIQ Monitoring

* [Prometheus Data source](querying-data/README.md)
  * [Application Monitoring](querying-data/application-monitoring/README.md)
    * [Spring Boot](querying-data/application-monitoring/spring-boot.md)
* [Elasticsearch Data source](elasticsearch-data-source.md)
* [JSON Data source](json-data-source.md)

## Vewing Logs

* [The LOGIQ UI](vewing-logs/the-logiq-ui.md)
* [Terminology](vewing-logs/logs-terminology.md)
* [Logs Page](vewing-logs/logs-page.md)
* [Search Page](vewing-logs/search-page/README.md)
  * [Share Search Results](vewing-logs/search-page/share-search-results.md)
  * [LOGIQ Search Cheat Sheet](vewing-logs/search-page/search-cheat-sheet.md)
* [Metrics and Custom Indices](vewing-logs/metrics-and-custom-indices.md)
* [Reports](vewing-logs/reports/README.md)
  * [Accessing Reports results via API](vewing-logs/reports/accessing-api-results-via-api.md)
* [logiqctl](vewing-logs/logiqctl/README.md)
  * [Configuring logiqctl](vewing-logs/logiqctl/configuring-logiqctl.md)
  * [Obtaining API Key](vewing-logs/logiqctl/obtaining-api-key.md)
* [Role-Based Access Control (RBAC)](vewing-logs/role-based-access-control.md)
* [Configuring RBAC](vewing-logs/configuring-rbac.md)

## ANOMALY DETECTION <a href="logiq-events" id="logiq-events"></a>

* [Events](logiq-events/events.md)
* [Event Rules](logiq-events/event-rules.md)
* [Alertable Events](logiq-events/alerts.md)
* [Logs to time series event visualization](logiq-events/logs-to-time-series-event-visualization.md)

## COMPLIANCE

* [Audit Trail](compliance/audit-trail.md)

## LOGIQ STREAMING

* [Query API](logiq-streaming/historical-data.md)

## LOGIQ Configuration <a href="logiq-ui-configuration" id="logiq-ui-configuration"></a>

* [E-Mail Configuration](logiq-ui-configuration/email-configuration-setup.md)
* [Alert Destinations](logiq-ui-configuration/alert-destinations.md)
* [Single Sign-On with SAML](logiq-ui-configuration/single-sign-on-configuration.md)

## Log Ingest configuration <a href="logiq-log-ingest-server-configuration" id="logiq-log-ingest-server-configuration"></a>

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

## RUNNING ON AWS

* [Getting started](running-on-aws/getting-started.md)
* [AWS IAM Resources](running-on-aws/aws-iam-resources.md)
* [1-Click deployment using CloudFormation](running-on-aws/ami-using-cloudformation.md)
