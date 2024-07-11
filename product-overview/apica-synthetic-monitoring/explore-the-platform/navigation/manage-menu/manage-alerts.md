# Manage Alerts

From the **Manage Alerts** view, you can assign individual or group alerts for each check, which will notify them of any status change according to the preferred severity.



In Manage Alerts, checks are displayed by Top Level Group and Subgroup, much as they appear in Manage checks, but with an icon along the right side with which Alerts can be assigned.

In the upper right, you can toggle between Alerts and Recipients.

## Workflow <a href="#managealerts-workflow" id="managealerts-workflow"></a>

The general workflow for creating alerts is:

* Create Recipient Users to receive the alerts
* Create Targets for the delivery method to the recipients
* (Optional) Create Recipient Groups containing multiple recipients
* Create the Alerts themselves, by selecting checks and assigning recipients

## Adding a New Alert <a href="#managealerts-addinganewalert" id="managealerts-addinganewalert"></a>

You can add alerts for any checks and select one or several severities to include in the alert. Each alert can have multiple Alert Recipients, and each recipient can have multiple Targets.



To add an alert:

* Find the checks you want to create alerts for
* Search for checks with the **Filter** search box

Or:

* Expand the Monitor Groups as needed
* Mark the Checks you want to include in the alert and **click** on the **Selected alerts** button:
* Mark the levels of **Severity** you want to send alerts for
* Mark the users or groups your want to send alerts to
* Click the **Create Alert** button

## Adding Alert Recipients <a href="#managealerts-addingalertrecipients" id="managealerts-addingalertrecipients"></a>

Recipients are the endpoints for an alert, typically a team (Group) or an individual (User). The Users and Groups you set to receive Alerts are set up in the **Recipients** tab. &#x20;



### Add Group <a href="#managealerts-addgroup" id="managealerts-addgroup"></a>

Recipient groups are collections of user targets you select to receive the alerts.



**Note:** You need to create the users and targets before you can add them to a group.

**Create Group**

To add a recipient group:



* Click the **Add Group** button



* Enter a **name** for the group
* Find the **Users** you want to include in the group
* Click the checkbox next to each **Target**



* Click **Create Group**

The group is created, containing the selected user/targets.



### Add User <a href="#managealerts-adduser" id="managealerts-adduser"></a>

Recipients are the users or groups of users you select to receive the alerts.



**Add User**



* Click the **Add User** button



* Enter the basic user information:
* User **Name**
* User **Description**
* User **Phone Number** (doubles as Targets)
* User **Email** (doubles as Targets)



* Click the **Create User** button

The user is created, containing the two default targets.



## Adding Alert Targets <a href="#managealerts-addingalerttargets" id="managealerts-addingalerttargets"></a>

In this example we set up two targets for different events with different messages.

* A `Fail` target with a message containing status information and timestamp and location.
* A `Success` target with a message containing timestamp.

**Add Targets**

We start in the Alert Recipients tab, with a recipient we want to add the targets to:



**Fail Target**



* Click **Add Email Target**



* Enter a **Target Name** (`Fail`)
* Enter an **Email**
* Uncheck the **Use Default Message** box



* Edit the the text in the **Message** box (you can use [Message Placeholders](https://apica-kb.atlassian.net/wiki/spaces/ASMDOCS/pages/2150563916/Configuring+Alerts#Message-Placeholders))

In this case we use this message:

```
The check %CHECK_NAME% (id %CHECK_ID%)
failed with status %SEV% at %TT% (%UTC% UTC)
from %LOCATION%.
```

* Click **Add Email Target**

The target is added to the recipient.



**Success Target**



* Click **Add Email Target**
* Enter a **Target Name** (`Success`)
* Enter an **Email**
* Uncheck the **Use Default Message** box



* Edit the the text in the **message** box (you can use [Message Placeholders](https://apica-kb.atlassian.net/wiki/spaces/ASMDOCS/pages/2150563916/Configuring+Alerts#Message-Placeholders))

In this case we use this message:

```
The check %CHECK_NAME% (id %CHECK_ID%)
returned to normal at %TT% (%UTC% UTC).
```

* Click **Add Email Target**

The target is added to the recipient.



We now have the targets we need for the alerts. Navigate back to the Alerts tab to verify that the configured was done correctly:



\
