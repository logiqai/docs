---
description: This page describes configuring LOGIQ Insights alert destinations.
---

# Alert Destinations

When an alert triggers, LOGIQ Insights sends alert details to its designated alert destinations. LOGIQ Insights supports following types of alert destinations.

* **E-mail**
* **Slack**
* **PagerDuty **
* **Generic Webhook**

## Configuring Destinations

&#x20;To configure alert destinations navigate to **settings** and open **“Alert Destinations”** tab

![Alert Destinations](<../.gitbook/assets/Screen Shot 2020-08-11 at 1.20.39 PM.png>)

### Email

{% hint style="info" %}
&#x20;It’s required to [configure the e-mail](email-configuration-setup.md) server to receive e-mail notifications.
{% endhint %}

1. Click on + New Alert Destination”, pick Email.
2. Specify, recipient’s name & email address.
3. Subject is configurable. It’s recommended to use format: **Alert {alert\_name} changed status to {state}. **alert\_name and state are template parameters and will be replaced by the urls  to give more information about the alert that will have occurred.

![James Smith's Email configuration](<../.gitbook/assets/Screen Shot 2020-08-11 at 1.24.28 PM.png>)

&#x20;Email destination is created by clicking the save button.

![Email Alert Destination](<../.gitbook/assets/Screen Shot 2020-08-11 at 1.33.34 PM.png>)

### Slack

In your [slack](https://my.slack.com/services/new/incoming-webhook/) console, pick or create a channel such as #alerts-events in this example and create an incoming webhook by clicking on "Add Incoming Webhooks Integration"

![Slack Webhooks integration](<../.gitbook/assets/Screen Shot 2020-08-11 at 3.10.58 PM.png>)

In your LOGIQ Insight's UI, Open “Alert Destinations” tab in the settings screen, and click on ”+ New Alert Destination”. Pick “Slack” as the type. Set the name, channel, etc. and provide a “Slack Webhook URL”, from above

![Slack Destination Configuration](<../.gitbook/assets/Screen Shot 2020-08-11 at 1.39.49 PM.png>)

### Pager Duty

Obtain the PagerDuty Integration Key from your PagerDuty service. Use Events API v2 Integration Type.

![](<../.gitbook/assets/Screen Shot 2020-08-11 at 4.31.41 PM.png>)

After obtaining the Integration Key:

1. Open “Alert Destinations” tab in the settings screen, and click on ”+ New Alert Destination”.
2. Pick “PagerDuty” as the type.
3. Populate mandatory fields are Name and Integration Key obtained earlier.

![PagerDuty Configuration](<../.gitbook/assets/Screen Shot 2020-08-11 at 5.02.05 PM.png>)

### Associating alert destinations to alert

Once the Alert destinations are created, one or more alert destinations can be configured in alert create or edit ui. Each configured destination is notified whenever that alert triggers.

![](<../.gitbook/assets/Screen Shot 2020-08-11 at 5.11.15 PM.png>)
