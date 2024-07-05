# Integrations Overview

Apica Ascent comes with a number of integration options for ingest and incident management.

### Ingest

Ingest lets you connect with and securely ingest data from popular log forwarding agents, cloud services, operating systems, container applications, and on-premise infrastructure. You can secure data ingestion from your endpoints into Apica Ascent by [generating a secure ingest token](generating-a-secure-ingest-token.md).

Apica Ascent currently integrates with over 150+ data sources via support for popular open source agents and open protocols. See below for links on how to enable specific integrations.

* [Logstash](../list-of-data-sources/logstash.md)
* [Filebeat](../list-of-data-sources/filebeat.md)
* [Fluent Bit](../list-of-data-sources/fluent-bit/)
* [Fluentd](../list-of-data-sources/fluentd.md)
* [Rsyslogd](../list-of-data-sources/rsyslogd.md)
* [AWS CloudWatch](../list-of-data-sources/aws/aws-cloudwatch-exporter.md)
* [Palo Alto Firewall](../list-of-data-sources/palo-alto-firewall.md)
* [Azure Event Hubs](../list-of-data-sources/azure/azure-event-hubs.md)
* [Prometheus](../list-of-data-sources/prometheus/)
* [Docker Syslog log driver](../list-of-data-sources/docker-syslog-log-driver.md)
* [Docker swarm logging](../list-of-data-sources/docker-swarm-logging.md)
* [Elasticsearch](../../data-sources/time-series-databases/elasticsearch-data-source.md)
* [GCP Cloud logging](../list-of-data-sources/gcp-cloud-logging.md)
* [IIS Logging](../list-of-data-sources/fluent-bit/iis-logs-on-windows.md)
* [JSON endpoints](../../data-sources/api/json-data-source.md)
* [MQTT](../list-of-data-sources/mqtt.md)

You can also ingest logs from endpoint devices running:

* [Windows](../list-of-data-sources/fluent-bit/#fluent-bit-for-windows)
* [macOS](https://github.com/logiqai/logiq-installation/tree/main/fluent-bit/macos)
* [Linux](https://github.com/logiqai/logiq-installation/tree/main/fluent-bit/linux)

### Log based HIDS

Apica Ascent's support for logs based HIDS enables data ingest directly from log based hids agents. Supported agents are as follows

* [OSSEC](https://docs.logiq.ai/integrations/ossec-variants-ossec-wazuh-atomic)
* [Atomic](https://docs.logiq.ai/integrations/ossec-variants-ossec-wazuh-atomic)
* [Wazuh](https://docs.logiq.ai/integrations/ossec-variants-ossec-wazuh-atomic)

### Incident management

Users can choose a variety of [incident management integrations](https://docs.logiq.ai/integrations/alert-destinations) to bring reliability into your production operations.

* [Email](https://docs.logiq.ai/integrations/alert-destinations#email)
* [Slack](https://docs.logiq.ai/integrations/alert-destinations#slack)
* [OpsGenie](https://docs.logiq.ai/integrations/alert-destinations#opsgenie)
* [PagerDuty](https://docs.logiq.ai/integrations/alert-destinations#pagerduty)
* ServiceNow

### Apica Ascent data collect agent - _logiqcoll_

Multiple data collection packages are combined and automate the installation and management using the script from tarball logiqcoll.tgz. The data collection agent consists of

* Prometheus metrics data collector
* Fluent-bit log data collector
* Prometheus node exporter that produces Linux system OS metrics data
* OSSEC agent
