---
description: configure email destination
---

# Email

click on **New Alert Destination > Email** to add new email destination

<figure><img src="../../.gitbook/assets/image (582).png" alt=""><figcaption></figcaption></figure>

fill in **Name** of destination and **Email Address** to receive email notifications on that email.

You can also configure **Subject Template** to configure the content of the email. default value: `Alert {alert_name} changed status to {state}`

You can use keywords enclosed in **{}** to access the following variables: **alert\_name, state, severity, alert\_url, query\_url.**

After entering the details, click **Create** to add the destination. This new destination will be available as an optional choice when creating or editing alerts.

