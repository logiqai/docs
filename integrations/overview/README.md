# Integrations Overview

Apica Ascent comes with a number of integration options for ingest and incident management.

### Ingest

Ingest lets you connect with and securely ingest data from popular log forwarding agents, cloud services, operating systems, container applications, and on-premise infrastructure. You can secure data ingestion from your endpoints into Apica Ascent by [generating a secure ingest token](generating-a-secure-ingest-token.md).

Apica Ascent currently integrates with over 150+ data sources via support for popular open source agents and open protocols. See below for links on how to enable specific integrations.

* [Logstash](../list-of-integrations/logstash.md)
* [Filebeat](../list-of-integrations/filebeat.md)
* [Fluent Bit](../list-of-integrations/fluent-bit/)
* [Fluentd](../list-of-integrations/fluentd.md)
* [Rsyslogd](../list-of-integrations/rsyslogd.md)
* [AWS CloudWatch](../list-of-integrations/aws/aws-cloudwatch-exporter.md)
* [Palo Alto Firewall](../list-of-integrations/palo-alto-firewall.md)
* [Azure Event Hubs](../list-of-integrations/azure/azure-event-hubs.md)
* [Prometheus](../list-of-integrations/prometheus/)
* [Docker Syslog log driver](../list-of-integrations/docker-syslog-log-driver.md)
* [Docker swarm logging](../list-of-integrations/docker-swarm-logging.md)
* [Elasticsearch](../../data-sources/time-series-databases/elasticsearch-data-source.md)
* [GCP Cloud logging](../list-of-integrations/gcp-cloud-logging.md)
* [IIS Logging](../list-of-integrations/fluent-bit/iis-logs-on-windows.md)
* [JSON endpoints](../../data-sources/api/json-data-source.md)
* [MQTT](../list-of-integrations/mqtt.md)

You can also ingest logs from endpoint devices running:

* [Windows](../list-of-integrations/fluent-bit/#fluent-bit-for-windows)
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
