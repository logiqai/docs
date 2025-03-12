---
icon: chart-line
---

# Dashboards & Visualizations - staging

Apica Ascent comes with tools to monitor your applications and infrastructure. With the help of our monitoring tools, you can visualize the metrics, detect anomalies, and get notified before any potential incident.

## Tools for Monitoring <a href="#tools-for-monitoring" id="tools-for-monitoring"></a>

* Monitoring Dashboards
* Queries
* Alerts

## Create Dashboard <a href="#create-dashboard" id="create-dashboard"></a>

* Expand `Create` from the navbar and click `dashboard`. A popup will be displayed by prompting the dashboard name
* Enter a name for the dashboard
* Click on `Create`. You will be navigated to the dashboard

### Add Widget <a href="#add-widget" id="add-widget"></a>

> On creating a new dashboard it will not have any widgets. Widgets are created on top of the queries. If you don't have any queries created, Please follow the documentation for [queries](https://docs.apica.io/observe/prometheus/querying-data) to create one.

* Click `Add Widget` button at the bottom of the page
* Select a query that you want to visualize
* Select a visualization for the selected query
* Click `Add to Dashboard`
* Click `Apply changes`

<figure><img src="../.gitbook/assets/Screenshot 2025-03-12 121613.png" alt=""><figcaption><p>Adding a widget to the Dashboard</p></figcaption></figure>

## Publish your dashboard&#x20;

* Click the publish button on the top right corner of the dashboard page&#x20;

After your dashboard is published, you can share it with anyone using the share option&#x20;

## &#x20;Build an auto-refreshing Dashboard&#x20;

The dashboard widgets execute the queries and visualize the results. You can configure all the widgets to automatically refresh to get the latest results. &#x20;

Steps to make an auto-refreshing dashboard&#x20;

* Navigate to any dashboard&#x20;
* Click the down arrow button in the refresh button, which is available in the top right corner&#x20;
* Select the time interval in which all the widgets in the dashboard will be refreshed automatically&#x20;
* No,w the dashboard widgets will be refreshed on every selected time interval&#x20;

<figure><img src="../.gitbook/assets/Screenshot 2025-03-12 121826.png" alt=""><figcaption></figcaption></figure>

## Adding widgets to the Dashboard&#x20;

### Steps to add a widget &#x20;

* Navigate to the dashboard for which you need to add a widget&#x20;
* Click the More Options icon in the top right corner of the dashboard page&#x20;
* Click edit from the dropdown&#x20;
* Click the Add Widget button at the bottom of the page&#x20;
* Select a query that you want to visualize&#x20;
* Select a visualization for the selected query&#x20;
* Click Add to Dashboard&#x20;

<figure><img src="../.gitbook/assets/Screenshot 2025-03-12 121613.png" alt=""><figcaption></figcaption></figure>

## Using Pre-defined Dashboards&#x20;

## Overview&#x20;

You can get more out of the monitoring dashboard when it monitors various aspects of your target. Building that kind of dashboard with more tricky queries can be time-consuming and delay you from knowing more about your application and infrastructure.&#x20;

We help you to build a viable dashboard with a few clicks by providing you with pre-defined dashboards for some of the most common use cases.&#x20;

Import Dashboard&#x20;

* Expand the dashboard option from the navigation bar&#x20;
* Click on the Import dashboard&#x20;
* You will be navigated to the import dashboard page, where you will be provided with some of the pre-defined dashboards&#x20;
* Click the import button for the dashboard&#x20;
* You will be displayed with a pop-up that will ask you to provide the dashboard name and data source which will be used by the queries in the dashboard widgets&#x20;
* After providing the inputs, click Import. You will be navigated to the dashboard page&#x20;

<figure><img src="../.gitbook/assets/Screenshot 2025-03-12 122124.png" alt=""><figcaption><p>Import Dashboard</p></figcaption></figure>

Apica Ascent also includes a Grafana dashboard import section where popular Grafana dashboards can be directly imported into Apica Ascent. See the section on [Grafana Dashboard import](https://docs.apica.io/dashboards/import-grafana-dashboards) for how to use that capability.&#x20;

## Import Grafana Dashboards&#x20;

Grafana is an open-source tool for building monitoring and visualization tools. It has a public repository with thousands of dashboards published and maintained by its community, which is being used by millions of people to monitor its infrastructure.&#x20;

We are providing some popular dashboards from their public repository for you to monitor. &#x20;

## Steps to Import Grafana Dashboard&#x20;

* Navigate to the import dashboard page&#x20;
* Click the Import Button under the grafana dashboard&#x20;
* Select the type of target that you want to monitor. You will be provided with the list of dashboards available for the selected target&#x20;
* Click the view button to get details of that dashboard&#x20;
* Click select to import the dashboard&#x20;
* Provide a name for the dashboard and select the datasource that will be used by the widgets&#x20;
* Click Import. You will be redirected to the dashboard&#x20;

<figure><img src="../.gitbook/assets/Screenshot 2025-03-12 122237.png" alt=""><figcaption><p>Grafana Dashboard Import</p></figcaption></figure>

## Supported Monitoring Targets&#x20;

* FluentBit&#x20;
* Go Application&#x20;
* Kafka&#x20;
* Kubernetes&#x20;
* Redis&#x20;
* Postgres&#x20;
* Prometheus&#x20;
* Node&#x20;
