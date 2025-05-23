---
icon: cloud
---

# Getting Started with Ascent

The Ascent platform enables you to converge all of your IT data from disparate sources, manage your telemetry data, and monitor and troubleshoot your operational data in real-time. The following guide assumes that you have signed up for Apica Ascent in the cloud. **If you are not yet a registered user, please** [**follow this link and the defined steps**](https://app.gitbook.com/o/-LmzGjHypGkPBzYc0fF0/s/-LmzGprckLqwd5v6bs6m/~/changes/1553/getting-started/logiq-saas/register-and-gain-access). Once registered, use this guide to get started.

<figure><img src="../../.gitbook/assets/image (20) (1) (1).png" alt=""><figcaption><p>Ascent Quick Start Process</p></figcaption></figure>

## Quick Start Process for Using Ascent

For all users that want to get started with Ascent should follow these five (5) simple steps:

1. [Collect Data from Input Sources](./#step-1-collect-data-from-input-sources)
2. [Setup and Configure Pipeline](./#step-2-setup-and-configure-pipeline)
3. [Design Queries](./#step-3-design-queries)
4. [Create Dashboards](./#step-4-create-dashboards)
5. [Setup Alerts and Workflow](./#step-5-setup-alerts-and-workflow)

In this guide, we cover the key goals and related activities of each step to ensure a quick and easy setup of Ascent.

### Step 1 - Collect Data from Input Sources

The goal is to ingest telemetry data (logs, metrics, traces) from relevant systems.

**Key actions include:**&#x20;

* Identify all sources
* Choose agents appropriate for each data type
* Configure data collection frequency and granularity
* Ensure data normalization

**Links to related docs include:**

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
