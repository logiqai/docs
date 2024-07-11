---
description: >-
  This document describes the steps needed to bring up the Apica Ascent observability
  stack using docker-compose
---

# Quickstart guide

## Install Docker compose

You can spin-up Apica Ascent using `docker-compose`. Install guide for `docker-compose` can be found here - [https://docs.docker.com/compose/install/](https://docs.docker.com/compose/install/)

{% hint style="info" %}
_**NOTE:** the docker-compose quick-start YAML files are intended for demo and trial use only. If you want to run a production deployment, we recommend you use Kubernetes with HELM to deploy the Apica Ascent stack. Please contact us at : s a l e s @ l o g i q . a i_
{% endhint %}

## Running Apica Ascent

{% hint style="info" %}
NOTE: Apica Ascent services use approximately 2GB of memory. Please have sufficient memory in your system before proceeding
{% endhint %}

The first step is to get the appropriate `docker-compose` YAML file from the URL below.

### Download Apica Ascent compose file

The latest version of Apica Ascent quickstart docker compose image is **2.3.1**

{% hint style="info" %}
⬇ Download the YAML here - [https://logiqcf.s3.amazonaws.com/2.3.1/docker-compose.quickstart.yml](https://logiqcf.s3.amazonaws.com/2.3.1/docker-compose.quickstart.yml)
{% endhint %}

You are now ready to bring up the Apica Ascent stack.

### Download container images

```text
$docker-compose -f docker-compose.quickstart.yml pull
```

### Bring up the stack

```text
$docker-compose -f docker-compose.quickstart.yml up -d
```

{% hint style="info" %}
**NOTE:** If you have been running previous versions of Apica Ascent docker-compose, you should stop and remove the existing containers by running docker-compose -f docker-compose.quickstart.yml down and remove any older docker volume via docker-compose -f docker-compose.quickstart.yml rm && docker-compose -f docker-compose.quickstart.yml rm -v
{% endhint %}

## Test using Apica Ascent UI

Once the Apica Ascent server is up and running, the Apica Ascent UI can be accessed as described above on port 80 on the server docker-compose. You will be presented with a login screen as shown below.

{% hint style="info" %}
Use _flash-admin@foo.com_ / _flash-password_ to login
{% endhint %}

![](../.gitbook/assets/screen-shot-2020-01-19-at-2.14.21-pm.png)

![](../.gitbook/assets/screen-shot-2021-01-03-at-5.06.08-pm.png)

## Ingesting data

Please refer to [section](agentless/) on [data ingestion](agentless/) for more details.

### Prometheus monitoring and alerting

The Apica Ascent quickstart file includes Prometheus and Alertmanager services.

## Firewall ports and URLs

### Ports

Apica Ascent exposes the below ports

* **7514** - Syslog / TCP - TLS
* **514** - Syslog / TCP - Non TLS
* **2514** - RELP/Rsyslog / TCP - TLS
* **20514** - RELP/Rsyslog / TCP - Non TLS
* **9998** - Server administration web cli
* **9999** - REST API
* **8081** - GRPC \( needed for apicactl CLI \)
* **80** - http
* **443** - https
* **24224/24225** - FluentForward protocol port / TLS
* **3000** - Grafana instance \(optional\), not available with quickstart

The ports used to bind are configurable via the server configuration file. See [Server options](../logiq-log-ingest-server-configuration/server-options.md) for more details.

