---
icon: browsers
---

# Ascent User Interface

The Apica Ascent UI is your window to your IT data, logs, and metrics - ingested from all of your data sources and converged onto a single layer. The Apica Ascent UI enables you to perform a wide range of operations – from simple uptime monitoring and error troubleshooting to capacity planning, real-time forensics, performance studies, and many more.

You can access the Apica Ascent UI by logging into your Apica Ascent instance URL using your account credentials.

![](../.gitbook/assets/windows-monitoring.png)

The navigation bar at the right side of the UI allows you to access your:

* Dashboards
* Queries
* Alerts
* Explore
* Events
* Rules
* Settings

The following sections in this article describe the various elements of the Apica Ascent UI and their purposes.

## Dashboards

A dashboard is a collection of visualizations and queries that you've created against your log data. You could create dashboards to house visualizations and queries for specific as well as multiple data sources. Everything contained within a dashboard is updated in real-time.

The **Dashboards** page on the Apica Ascent UI lists all the dashboards you've created within Apica Ascent. Dashboards that you've favorited are marked with a yellow star icon and are also listed under the **Dashboards** dropdown menu for quick access in the navigation bar. The following images depict dashboards that you can create using Apica Ascent.

![Dashboards Page shows list of dashboards.](../.gitbook/assets/dashboard-list.png)

![A typical monitoring dashboard on Apica Ascent](../.gitbook/assets/security-monitoring.png)

![Another example of a Apica Ascent dashboard](../.gitbook/assets/aws-cloudtrail.png)

## **Queries**

Apica Ascent enables you to write custom queries to analyze log data, display metrics and events, view and customize events and alerts, and create custom dashboards. The **Queries** page lists all of the queries you've created on Apica Ascent. You can mark some of them as favorites or archive the ones, not in use. Your favorite queries also appear in the drop-down menu of the **Queries** tab for quick access.

![](../.gitbook/assets/queries-list.png)

## **Alerts**

Apica Ascent enables you to set alerts against events, data, or metrics of interest derived from your log data. The **Alerts** page on the UI lists all of the alerts you've configured on Apica Ascent. You can sort and display the list of alerts by their name, message, state, and the time they were last updated or created. Depending on your user permissions within Apica Ascent, you can click an alert to view more information or reconfigure the alert based on your need.

The following image depicts a typical **Alerts** page on the Apica Ascent UI.

![](../.gitbook/assets/alerts-list.png)

## Explore

The Explore page lists all of the log streams generated across your IT environment that are being ingested into Apica Ascent. The Explore page lists and categorizes logs based on Namespace, Application, ProcID, and when they were last updated. By default, logs are listed by the time they were ingested with the most recent applications appearing on the top. You can filter log streams by namespaces, applications, and ProcIDs. You can also filter them by custom time ranges.

You can also click into a specific application or ProcID to view logs in more detail and to search through or identify patterns within your log data.

The following image depicts a typical Explore page on the Apica Ascent UI.

![The Explore Page](../.gitbook/assets/explore-list.png)

## Events

The **Events** page lists all the important events that have occurred in the Apica Ascent Platform. Events are listed by their Name, Message, and the time they were created. The Event page tracks important service notifications like service restarts, license expiry, etc...

## Create

The **Create** dropdown menu enables you to create new reports, queries, dashboards, and alerts, as shown in the following image.

<figure><img src="../.gitbook/assets/image (325).png" alt=""><figcaption></figcaption></figure>

A function-specific modal appears based on what you select from this dropdown menu.
