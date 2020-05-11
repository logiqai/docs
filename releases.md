# Releases

## 1.2.1 - 2020-05-11

### Added

#### K8S

* Add support for ingress with http and optionally have https
* ServiceMonitor for ingest server if prometheus is installed

#### UI

* Logs modal ordering to match how developers view logs from a file
* Highlight log line from search

## 1.2.0 - 2020-04-28

Official GA of LOGIQ's complete Observability platform with support for metrics and log analytics

### Added

#### K8S

* Scale-out and HA deployment for Kubernetes via HELM 3 chart \( [https://github.com/logiqai/helm-charts](https://github.com/logiqai/helm-charts) \)

#### UI

* Monitoring of time series metrics
* New Log viewer
* Log viewer integration with faceted search
* Log time machine to go back in time to log state

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

Official GA of LOGIQ's Log Insights platform

### Added

* AWS Marketplace AMI for all regions including Gov cloud regions
* AWS CloudFormation 1-click deployment
* Rsyslog, Syslog protocol support for data ingest via Rsyslogd, syslogd, syslog-ng, logstash, fluentd, fluentbit, docker logging syslog driver.
* Built-in UI with SQL Queries, Faceted search, Alerts, Dashboards



