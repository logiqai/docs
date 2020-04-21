# Releases

## 1.2.0 - 2020-04-21

### Added

#### K8S

* Scale-out and HA deployment for Kubernetes via HELM 3 chart \( [https://github.com/logiqai/helm-charts](https://github.com/logiqai/helm-charts) \)

#### UI

* New Log viewer in the masthead
* Logs viewer integration with faceted search
* Logs time machine to go back in time to log state of the infrastructure

#### CLI

* [logiqctl](logiqctl/logiq-box.md) is now GA with support for log tailing, historical queries and search

## 1.1.0 - 2020-02-27

### Fixed

* Fluentd sends error logs as info - fixed with grok patterns to extract proper severity strings from incoming messages

### Added

* Anomaly detection via Eventing with built-in and custom rules
* Built-in UI Help with Intercomm chat
* Expand and collapse search facets

### Changed

* New AMI's for AWS marketplace

## 1.0.0 - 2020-01-21

### Added

* AWS Marketplace AMI for all regions including Gov cloud regions
* AWS CloudFormation 1-click deployment
* Rsyslog, Syslog protocol support for data ingest via Rsyslogd, syslogd, syslog-ng, logstash, fluentd, fluentbit, docker logging syslog driver.
* Built-in UI with SQL Queries, Faceted search, Alerts, Dashboards



