# Health & Events

## Overview of Health & Events <a href="#health-and-events-overviewofhealth-and-events" id="health-and-events-overviewofhealth-and-events"></a>

The **Health & Events** view shows your configured checks' status and allows you to add Custom Events for important changes.



## Chart View <a href="#health-and-events-chartview" id="health-and-events-chartview"></a>

The Health & Events Chart shows an overview of check statuses, according to the Filter Items settings. On the Y-axis is the **number of checks**, with **time** on the X-axis. Check status Severity is indicated by color.

Events display all severity changes that have occurred for all the checks in your account.



## Events Table View <a href="#health-and-events-eventstableview" id="health-and-events-eventstableview"></a>

According to the Filter Items settings (or for the time period selected in the Chart), the event table shows a list of events. Events display all severity changes that have occurred for all the checks in your account.

![](../../../.gitbook/assets/2133691188.png)

### Column Descriptions <a href="#health-and-events-columndescriptions" id="health-and-events-columndescriptions"></a>

* **Severity:** Check status Severity.
* **Time:** The timestamp for when the event occurred.
* **Check:** Name of the check.
* **Type:** Type of check.
* **Location:** This location reported the event.
* **Event:** Description of the event. This allows you to identify monitored services that are experiencing issues.

## Custom Events <a href="#health-and-events-customevents" id="health-and-events-customevents"></a>

Use Custom Events to indicate external events such as maintenance windows, power outages, and other events that affect performance.

### Adding Custom Event <a href="#health-and-events-addingcustomevent" id="health-and-events-addingcustomevent"></a>

You can manually add Custom Events from the Manage Events view.

| **Step**                                                                                                                                                                                                                      | **Screenshot**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <p>Click <strong>Add Custom Event</strong></p><p>Add information to the <strong>Add Custom Event</strong> dialog about the event, as needed.</p><p>Click <strong>Save</strong> to add the custom event to the event list.</p> | <p></p><h4 id="health-and-events-eventinformation">Event Information</h4><ul><li><strong>Name:</strong> The identifier for the event for display purposes.</li><li><strong>Description:</strong> Explanation of what the event entails.</li><li><strong>From</strong>: The start date for the event</li><li><strong>To</strong>: End date for the event, or <strong>Same as From</strong></li><li><strong>Severity</strong>: Indicates the Severity of the event.</li></ul><p><em><strong>AFFECTED CHECKS</strong></em></p><p>List of names for specific checks, or All Checks</p> |

You can [view Custom Events](https://apica-kb.atlassian.net/wiki/spaces/ASMDOCS/pages/2134213568/Understanding+the+Check+Details+View#Show-Custom-Events) after you have created them on the Check Details page.

***

## Filtering Items <a href="#health-and-events-filteringitems" id="health-and-events-filteringitems"></a>

At the top of the window are a number of filtering options that allow you to define which events to display in the graph and list.



For each item, you can select to either **Include** (show) or **Exclude** (hide) the selected in Chart and Event Table. You can combine different excludes with includes to achieve your desired result.

### Filtering Health & Events <a href="#health-and-events-filteringhealth-and-events" id="health-and-events-filteringhealth-and-events"></a>

* Enter filter item(s) as needed
* Select a time period
* Click **Apply Filter**

| **Item**               | **Description**                                                                                                                                        |
| ---------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Search**             | Search for check names.                                                                                                                                |
| **Check Type**         | Type of check.                                                                                                                                         |
| **Location**           | Check location.                                                                                                                                        |
| **Group**              | The Monitor Group.                                                                                                                                     |
| **Tag**                | The Tag(s) attached to each check.                                                                                                                     |
| **Severity**           | Check status Severity.                                                                                                                                 |
| **Show Custom Events** | Include Custom Events in the filter.                                                                                                                   |
| **Period**             | <p>Desired Time period.</p><p>Quick Picks include, <strong>Last Day</strong>, Last <strong>7 Days</strong>, and <strong>Last Month</strong></p><p></p> |
| **Apply Filter**       | Applies the filter to the display.                                                                                                                     |

### Filtering With the Chart <a href="#health-and-events-filteringwiththechart" id="health-and-events-filteringwiththechart"></a>

#### Select time period <a href="#health-and-events-selecttimeperiod" id="health-and-events-selecttimeperiod"></a>

You can choose a particular time period by clicking a bar in the Chart:

This will make the event table display information for the selected time period:

&#x20;



### Details <a href="#health-and-events-details" id="health-and-events-details"></a>



Pointing at the Type or Location icons in a row in the table will show a detailed graph for the event:

* The graph shows information about the time surrounding the event.
*   Hovering the mouse over a point in the curve in the graph reveals information about that point:

    The information shown is the **timestamp**, **check name,** and **response time** for the selected point, with **time** on the X-axis.

![](../../../.gitbook/assets/2187132977.png)

* Clicking on the icon will open up the check details.
  * Check Name
  * Check Type
  * Check Location
  * Test Start Date
  * History
    * Severity
    * Result Value
    * Attempts
    * Result Code
    * Message
