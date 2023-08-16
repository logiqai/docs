# Overview

Apica Ascent comes with a number of integration options for ingest and incident management.

### Ingest

Ingest lets you connect with and securely ingest data from popular log forwarding agents, cloud services, operating systems, container applications, and on-premise infrastructure. You can secure data ingestion from your endpoints into Apica Ascent by [generating a secure ingest token](generating-a-secure-ingest-token.md). &#x20;

Apica Ascent currently integrates with over 150+ data sources via support for popular open source agents and open protocols. See below for links on how to enable specific integrations.&#x20;

* [Logstash](../logstash.md)
* [Filebeat](../filebeat.md)
* [Fluent Bit](../fluent-bit/)
* [Fluentd](../fluentd.md)
* [Rsyslogd](../rsyslogd.md)
* [AWS CloudWatch](../aws/aws-cloudwatch-exporter.md)
* [Palo Alto Firewall](../palo-alto-firewall.md)
* [Azure Event Hubs](../azure-event-hubs.md)
* [Prometheus](../prometheus/)
* [Docker Syslog log driver](../docker-syslog-log-driver.md)
* [Docker swarm logging](../docker-swarm-logging.md)
* [Elasticsearch](../../data-sources/time-series-databases/elasticsearch-data-source.md)
* [GCP Cloud logging](../gcp-cloud-logging.md)
* [IIS Logging](../fluent-bit/iis-logs-on-windows.md)
* [JSON endpoints](../../data-sources/api/json-data-source.md)
* [MQTT](../mqtt.md)

You can also ingest logs from endpoint devices running:

* [Windows](../fluent-bit/#fluent-bit-for-windows)
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

Multiple data collection packages are combined and automate the installation and management using the script from tarball logiqcoll.tgz.  The data collection agent consists of

* Prometheus metrics data collector
* Fluent-bit log data collector
* Prometheus node exporter that produces Linux system OS metrics data
* OSSEC agent

