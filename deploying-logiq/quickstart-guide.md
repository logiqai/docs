---
description: >-
  This document describes the steps needed to bring up the LOGIQ observability
  stack using docker-compose for trial and demo use
---

# LOGIQ Quickstart

{% hint style="warning" %}
Please read and agree with the [EULA](https://docs.logiq.ai/eula/eula) before proceeding.
{% endhint %}

## Install Docker compose

You can spin-up LOGIQ using `docker-compose`. Install guide for `docker-compose` can be found here - [https://docs.docker.com/compose/install/](https://docs.docker.com/compose/install/)

{% hint style="info" %}
_**NOTE:** the docker-compose quick-start YAML files are intended for demo and trial use only. If you want to run a production deployment, LOGIQ uses Kubernetes with HELM to deploy the stack. Please contact us at : s a l e s @ l o g i q . a i_
{% endhint %}

## Running LOGIQ

{% hint style="info" %}
NOTE: LOGIQ services use approximately 2GB of memory. Please have sufficient memory in your system before proceeding
{% endhint %}

The first step is to get the `docker-compose` YAML file from the URL below.

### Download LOGIQ compose file

{% hint style="info" %}
⬇ Download the YAML at the URL - [https://logiqcf.s3.amazonaws.com/releases/docker-compose.quickstart.yml](https://logiqcf.s3.amazonaws.com/releases/docker-compose.quickstart.yml)
{% endhint %}

You are now ready to bring up the LOGIQ stack.

### Download container images

```
$docker-compose -f docker-compose.quickstart.yml pull
```

### Bring up the stack

```
$docker-compose -f docker-compose.quickstart.yml up -d
```

{% hint style="info" %}
**NOTE:** If you have been running previous versions of LOGIQ docker-compose, you should stop and remove the existing containers by running docker-compose -f docker-compose.quickstart.yml down and remove any older docker volume via docker-compose -f docker-compose.quickstart.yml rm && docker-compose -f docker-compose.quickstart.yml rm -v
{% endhint %}

### Delete the stack

If you are done with your evaluation and want to cleanup your environment, please run the following command to stop and delete the LOGIQ stack and free up the used system resources.

```
$docker-compose -f docker-compose.quickstart.yml down
$docker volume prune
```

## Test using LOGIQ UI

Once the LOGIQ server is up and running, the LOGIQ UI can be accessed as described above on <mark style="color:green;">**port 80**</mark> on the server docker-compose. You will be presented with a login screen as shown below.

{% hint style="info" %}
Use _flash-admin@foo.com_ / _flash-password_ to login
{% endhint %}

![](<../.gitbook/assets/Screen Shot 2022-03-19 at 8.11.14 AM.png>)

![](<../.gitbook/assets/Screen Shot 2022-03-19 at 9.27.01 AM.png>)

## Ingesting data

For setting up data ingestion from your endpoints and applications into LOGIQ.AI, please refer to the [Integrations section](../integrations/overview.md).

**The quickstart compose file includes a test data tool** that will generate test log data and also has a couple of dashboards that show LOGIQ's APM capabilities.

The test log data can be view under logs&#x20;

![](<../.gitbook/assets/Screen Shot 2022-03-19 at 9.32.49 AM.png>)

Running search across logs can be initiated under Logs > Search

![](<../.gitbook/assets/Screen Shot 2022-03-19 at 9.34.11 AM.png>)

### Prometheus monitoring and alerting

The LOGIQ quickstart file includes Prometheus and Alertmanager services. 2 APM Dashboards to monitor the quickstart environments are included.



## Firewall ports and URLs

### Ports

LOGIQ service exposes the below ports

* **7514** - Syslog / TCP - TLS
* **514** - Syslog / TCP - Non TLS
* **2514** - RELP/Rsyslog / TCP - TLS
* **20514** - RELP/Rsyslog / TCP - Non TLS
* **9998** - Server administration web cli
* **9999** - REST API
* **8081** - GRPC ( needed for logiqctl CLI )
* **80** - http
* **443** - https
* **24224/24225** - FluentForward protocol port / TLS
* **3000** - Grafana instance (optional), not available with quickstart

The ports used to bind are configurable via the server configuration file. See [Server options](../logiq-log-ingest-server-configuration/server-options.md) for more details.
