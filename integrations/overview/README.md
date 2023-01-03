# Overview

LOGIQ comes with a number of integration options for ingest and incident management.

### Ingest

lets you connect with and securely ingest data from popular log forwarding agents, cloud services, operating systems, container applications, and on-premise infrastructure. You can secure data ingestion from your endpoints into LOGIQ by [generating a secure ingest token](generating-a-secure-ingest-token.md). &#x20;

LOGIQ currently integrates with over 150+ data sources via support for popular open source agents and open protocols. See below for links on how to enable specific integrations.&#x20;

* [Logstash](../logstash.md)
* [Filebeat](../filebeat.md)
* [Fluent Bit](../fluent-bit/)
* [Fluentd](../fluentd.md)
* [Rsyslogd](../rsyslogd.md)
* [AWS CloudWatch](../aws/aws-cloudwatch-exporter.md)
* [Palo Alto Firewall](../palo-alto-firewall.md)
* [Azure Event Hubs](../azure/azure-event-hubs.md)
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

LOGIQ's support for logs based HIDS enables data ingest directly from log based hids agents. Supported agents are as follows

* OSSEC
* Atomic
* Wazuh

### Incident management

Users can choose a variety of i[ncident management integrations](../alert-destinations.md) to bring reliability into your production operations.

* Email
* Slack
* OpsGenie
* PagerDuty
* ServiceNow
