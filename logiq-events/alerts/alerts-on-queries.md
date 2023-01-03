# Alerts On Queries

##

## Create an Alert On Query

1. Press on the create header caret and select alert to navigate to create a new alert page.
2. select a query.
3. select the type of alert.

Based on the baselining feature enabled on the query previously, different types of alerts are visible in the dropdown. types of alerts include:

* simple alert ( visible by default )
* anomaly alert ( visible if anomaly detection AI/ML feature is enabled )
* LCL or UCL alert ( visible if STD feature is enabled )
* week comparison alert ( visible if the week comparison feature is enabled  )

<figure><img src="../../.gitbook/assets/alert-types.png" alt=""><figcaption><p>alert types drop down</p></figcaption></figure>

provide all the fields and save the alert.

#### Fields

* **Name**: A name for the alert, should be alphanumeric.
* **Destination**: This is a user-specified selection where the alerts will be delivered. Only [user-defined alert destinations](../../integrations/alert-destinations.md) will be available for selection. Users can configure alert destinations in the Alert Destinations Section
* **Operation**: one of the comparators: `>` `>=` `<` `<=` `==` `!=` `=~` `!~`
* **Reference:** set the threshold value for the alert condition**.**
* **Rearm**: how frequently you will receive notifications when your query meets the Alert criteria and does not change, must be a valid number (seconds) minimum `300` seconds.
* **Value Column:**  The data column upon which the alert is configured.
* **Selection Condition**:  one of the options `Any` `All` `None.`Select All to alert only if all rows meet the condition. Select Any to alert if at least one row meets the condition.
* **Time Column**: select the time column if the data has a time column. <mark style="color:blue;">**( optional )**</mark>
* **Track Duration**:  This is enabled only if Time Column is provided. provide time in minutes to track the data in the given amount of minutes. if given 5m, it tracks the latest 5 minutes of data.

<figure><img src="../../.gitbook/assets/alert config.png" alt=""><figcaption><p>sample alert configuration</p></figcaption></figure>

The above picture is an example of an alert configuration where it tracks the last 5 minutes of the column "value" and is triggered when any row of the data is greater than the value 1.5.

If the time column is not selected entire dataset is tracked instead of the given track duration.

