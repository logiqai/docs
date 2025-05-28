# Using the OpenTelemetry Demo

## What is the OpenTelemetry (OTel) Demo?

The OTel Demo is a microservices-based application created by OpenTelemetry's community to demonstrate its capabilities in a realistic, distributed system environment. This demo application, known as the OpenTelemetry Astronomy Shop, simulates an e-commerce website composed of over 10 interconnected microservices (written in multiple languages), and communicates via HTTP and gRPC. Each service is fully instrumented with OTel, generating comprehensive traces, metrics, and logs.&#x20;

The demo serves as an invaluable resource for understanding how to implement and use OpenTelemetry in real-world applications. Using the Ascent platform with the OTel Demo enables you to converge all of the IT data, manage the telemetry data, and monitor and troubleshoot the operational data in real-time. The following steps guide you through the process of using the OTel Demo application with Ascent.

<figure><img src="../../.gitbook/assets/image (20) (1) (1).png" alt=""><figcaption><p>Ascent Quick Start Process</p></figcaption></figure>

## Quick Start Process for Using the OTel Demo app with Ascent

For all users that want to get started with Ascent should follow these five (5) simple steps:

1. [Deploy the OTEL Demo App](using-the-opentelemetry-demo.md#step-1-deploy-otel-demo-ap)
2. [Setup and Configure Pipeline](using-the-opentelemetry-demo.md#step-2-setup-and-configure-pipeline)
3. [Design Queries](using-the-opentelemetry-demo.md#step-3-design-queries)
4. [Create Dashboards](using-the-opentelemetry-demo.md#step-4-create-dashboards)
5. [Setup Alerts and Workflow](using-the-opentelemetry-demo.md#step-5-setup-alerts-and-workflow)

In this guide, we cover the key goals and related activities of each step to ensure a quick and easy setup of Ascent.

### How to Deploy the OTEL Demo App

The goal is to ingest telemetry data (logs, metrics, traces) from relevant systems.

**Key actions include:**&#x20;

* Accessing and deploying the public OpenTelemetry (OTEL) Demo App
* Configure data collection setup, frequency and granularity
* Ensure data normalization

This guide aims to walk you through the steps required to deploy the OpenTelemetry Demo app and begin sending data to Ascent.

**NOTE**: We will deploy the OTEL demo app using Docker for this guide.

## Prerequisites:

* Docker
* [Docker Compose v2.0.0+](https://docs.docker.com/compose/install/)
* 6 GB of RAM for the application

### Step 1: Get and Clone the OTEL demo app repository:

`$ git clone https://github.com/open-telemetry/opentelemetry-demo.git`

### Step 2: Go to the demo folder:

`$ cd opentelemetry-demo/`

### Step 3: Start the demo app in Docker:

`$ docker compose up --force-recreate --remove-orphans --detach`

### Step 4: (Optional) Enable API observability-driven testing:

`$ docker compose up --force-recreate --remove-orphans --detach`

### Step 5: Test and access the OTEL demo application:

Once the images are built and containers are started, you can now access the following Opentelemetry components on the demo app web store:

* Web store: [http://localhost:8080/](http://localhost:8080/)
* Grafana: [http://localhost:8080/grafana/](http://localhost:8080/grafana/)
* Load Generator UI: [http://localhost:8080/loadgen/](http://localhost:8080/loadgen/)
* Jaeger UI: [http://localhost:8080/jaeger/ui/](http://localhost:8080/jaeger/ui/)
* Tracetest UI: [http://localhost:11633/](http://localhost:11633/), only when using `make run-tracetesting`
* Flagd configurator UI: [http://localhost:8080/feature](http://localhost:8080/feature)

### Optional: Changing the demo’s primary port number <a href="#changing-the-demos-primary-port-number" id="changing-the-demos-primary-port-number"></a>

By default, the demo application will start a proxy for all browser traffic bound to port 8080. To change the port number, set the `ENVOY_PORT` environment variable before starting the demo.

* For example to use port 8081:

`$ ENVOY_PORT=8081 docker compose up --force-recreate --remove-orphans --detach`

### Step 6: Update the OTEL config file:

* /src/otel-collector/otelcol-config-extras.yml

Paste the following into the config file, overwriting it completely:

1.  Copy

    ```
    receivers:
      hostmetrics:
        collection_interval: 10s
        scrapers:
          cpu:
            metrics:
              system.cpu.utilization:
                enabled: true
          load:
          memory:
          filesystem:
          network:
          disk:
          paging:
          processes:

    processors:
      batch:
        timeout: 5s

    exporters:
      debug:
        verbosity: detailed
      prometheusremotewrite:
        endpoint: https://<YOUR-ASCENT-ENV>/api/v1/receive
        headers:
          Authorization: Bearer <YOUR-INGEST-TOKEN>
        tls:
          insecure: false
          insecure_skip_verify: true

    service:
      pipelines:
        metrics:
          receivers: [hostmetrics]
          processors: [batch]
          exporters: [prometheusremotewrite, debug]
    ```
2. Replace \<YOUR-ASCENT-ENV>with your Ascent domain, e.g. company.apica.io
3. Replace \<YOUR-INGEST-TOKEN>with your Ascent Ingest Token, e.g. eyXXXXXXXXXXX...
   1. See 'Step 7' to get your 'ingest-token'

### Step 7: Get Your Ingest Token from Ascent:

* [https://docs.apica.io/integrations/overview/generating-a-secure-ingest-token](https://docs.apica.io/integrations/overview/generating-a-secure-ingest-token)
* Restart OpenTelemetry collector:



## Verify Data Ingestion in Ascent:

**Detailed steps to start ingesting data:**

### Log into Ascent

<figure><img src="../../.gitbook/assets/image (458).png" alt=""><figcaption></figcaption></figure>





**Additional Links to helpful docs include:**

* [Data sources overview](https://docs.apica.io/data-sources/overview)
* [Integrations overview](https://docs.apica.io/integrations/overview)

### Step 2 - Setup and Configure Pipeline

The goal is to transport and process the collected data.

**Key actions include:**

* Select or configure a data pipeline
* Define data routing rules
* Apply transformations, filtering, or enrichment if needed

**Links to related docs include:**

* [Configure pipelines](https://docs.apica.io/flow/pipeline-management/data-flow-pipelines-new)
* [Visualize pipelines](https://docs.apica.io/flow/pipeline-management/data-flow-pipelines)
* [Forwarding data](https://docs.apica.io/flow/pipeline-management/mapping-applications)

### Step 3 - Design Queries

The goal is to enable insights by querying telemetry data.

**Key actions include:**

* Understand the query language used
* Create baseline queries for system health
* Optimize queries for performance and cost
* Validate query results

**Links to related docs include:**

* [Data explorer overview](https://docs.apica.io/data-management/overview-1)
* [Query builder](https://docs.apica.io/data-management/overview-1/query-builder)
* [Widget](https://docs.apica.io/data-management/overview-1/widget)

### Step 4 - Create Dashboards

The goal is to visualize system performance and behavior in real time.

**Key actions include:**

* Use visual components
* Organize dashboards by domain
* Incorporate filters
* Enable drill-down for troubleshooting.

**Links to related docs include:**

* [Dashboards overview](https://docs.apica.io/getting-started/overview)

### Step 5 - Setup Alerts and Workflow

The goal is to detect anomalies and automate response actions.

**Key actions include:**

* Define alerting rules
* Set up alert destinations
* Establish escalation policies and on-call schedules
* Integrate with incident management workflows and postmortem tools

**Links to related docs include:**

* [Alerts overview](https://docs.apica.io/logiq-events/alerts)
* [Alerting on queries](https://docs.apica.io/logiq-events/alerts-simple-anomaly)
* [Alerting on logs](https://docs.apica.io/logiq-events/alerts-1)

## Additional Resources

Here are helpful links to other "Getting Started" technical guides:

* [Getting Started with Metrics](getting-started-with-metrics.md)
* [Getting Started with Logs](getting-started-with-logs/)
* [Get acquainted with the Apica Ascent UI](../../product-overview/the-logiq-ui.md)
* [Configure your data sources](../../integrations/overview/)
* [Configure Apica Ascent to send alerts to your email server](../../logiq-ui-configuration/email-configuration-setup.md)
* [Add and configure alert destinations like email, Slack, and PagerDuty](../../integrations/list-of-integrations/alert-destinations/)
* [Configure SSO using SAML](../../logiq-ui-configuration/single-sign-on-configuration.md)
* [Configure RBAC](../../log-management/configuring-rbac.md)
