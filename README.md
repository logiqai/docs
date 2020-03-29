# Overview

LOGIQ server is a logging, streaming and analytics server that uses any _S3 compatible store_ as its primary data store.

It is best suited for ingesting log and time series data directly into your S3 compatible store. The ingested data is written in an open format for ready consumption by other software. Examples of common uses are ingesting log and time-series data from Rsyslogd, Syslog, Syslog-ng, Logstash, Fluentd, Docker and ECS logging drivers, Kafka, influxDB etc.

The LOGIQ server is natively written in Go programming language and compiles into a single binary. This makes it light enough to be bundled with any application stack. The server also can be configured to run in clustered, HA mode that can tolerate 1 or 2 node failures making it ideal for creating larger clusters.

