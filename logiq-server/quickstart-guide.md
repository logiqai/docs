---
description: >-
  This document describes the steps needed to bring up the LOGIQ observability
  stack using docker-compose
---

# Quickstart guide

## Install Docker compose

You can spin-up LOGIQ using `docker-compose`. Install guide for `docker-compose` can be found here - [https://docs.docker.com/compose/install/](https://docs.docker.com/compose/install/)

## Running LOGIQ

The first step is to get the appropriate `docker-compose` YAML file from the URL below.

The Quickstart YAML include a bundled S3 compatible object store from [minio](https://min.io)

{% hint style="warning" %}
Please read and agree with the [EULA](https://docs.logiq.ai/eula/eula) before proceeding. 
{% endhint %}

{% hint style="warning" %}
_**NOTE:** the docker-compose quick-start YAML files are intended for demo and trial use only. If you want to run a production deployment, we recommend you use Kubernetes with HELM to deploy the LOGIQ stack. Please contact us at : s a l e s @ l o g i q . a i_
{% endhint %}

#### LOGIQ full-stack - Ingest server with UI

* ⬇ Download the YAML here - [https://logiqcf.s3.amazonaws.com/2.0.1/docker-compose.quickstart.yml](https://logiqcf.s3.amazonaws.com/2.0.1/docker-compose.quickstart.yml)

```bash
$ https://logiqcf.s3.amazonaws.com/2.0.1/docker-compose.quickstart.yml
```

{% hint style="warning" %}
NOTE: LOGIQ services use approximately 2GB of memory. Please have sufficient memory in your system when running the docker-compose bring up
{% endhint %}

You are now ready to bring up the LOGIQ stack.

```text
$docker-compose -f docker-compose.quickstart.yaml up -d
```

While the services are coming up, you can check for the service logs

```text
$docker-compose logs -f docker-compose.quickstart.yaml
```

## Firewall ports and URLs

### Ports

LOGIQ exposes the below ports

* **7514** - Syslog / TCP - TLS
* **514** - Syslog / TCP - Non TLS
* **2514** - RELP/Rsyslog / TCP - TLS
* **20514** - RELP/Rsyslog / TCP - Non TLS
* **9998** - Server administration web cli
* **9999** - REST API
* **8081** - GRPC \( needed for logiqctl CLI \)
* **80** - http
* **443** - https
* **24224/24225** - FluentForward protocol port / TLS

The ports used to bind are configurable via the server configuration file. See [Server options](../logiq-log-ingest-server-configuration/server-options.md) for more details.

The LOGIQ compose file brings up a Prometheus server as well along with a monitoring dashboard for LOGIQ.

## Test using LOGIQ UI

Once the LOGIQ server is up and running, the LOGIQ UI can be accessed as described above on port 80 on the server docker-compose. You will be presented with a login screen as shown below.

{% hint style="info" %}
Use _flash-admin@foo.com_ / _flash-password_ to login
{% endhint %}

![](../.gitbook/assets/screen-shot-2020-01-19-at-2.14.21-pm.png)

### Prometheus monitoring and alerting

LOGIQ server comes with embedded Prometheus container. Prometheus scrapes metrics from the LOGIQ server and can be configured to scrape targets from any monitoring endpoint. Additionally the LOGIQ stack has alertmanager and provides query and alerting mechanism as detailed in [https://docs.logiq.ai/logiq-events/alerts](https://docs.logiq.ai/logiq-events/alerts)

```text
https://<logiq-server-ip>:9998/metrics
```

### Event and Anamoly detection

LOGIQ supports automatic detection of relevant events in your log stream. Find details at [https://docs.logiq.ai/logiq-events/event-rules](https://docs.logiq.ai/logiq-events/event-rules)

## Ingesting data

Please refer to section on [data ingestion](agentless.md) for more details.

