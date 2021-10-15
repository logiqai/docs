# Logs to time series event visualization

With LOGIQ insights in a matter of a few clicks, you can create time series visualizations for events that matter for effective monitoring. This section describes the details on how to create visualizations from logs or search pages.

You may choose to create a dedicated dashboard for event time series visualizations. Click on "create" and choose "dashboard".

![](<../.gitbook/assets/Screen Shot 2020-08-17 at 2.57.36 PM.png>)

Proceed to logs tab or search tab. Once the log-line is narrowed down either from the search page or from logs page, LOGIQ Insight’s event user interface makes it almost effortless to generate events, alerts and visualizations for efficient monitoring of your infrastructure.

From the search UI, choose a log-line that is of interest to generate events, and/or alerts and/or visualization. On the right hand side of the log-line click on “create new event”

![](<../.gitbook/assets/Screen Shot 2020-08-17 at 9.09.17 PM.png>)

Similarly, You may choose to find the log-line of interest from Logs UI. On the left hand side of the log-line click on “create new event”

![](<../.gitbook/assets/Screen Shot 2020-08-17 at 2.26.03 PM.png>)

This pops up the “Create alertable event rule” modal window. It enables the user to

* **Create an event rule**
* **Create the corresponding Visualization**
* **Create an Alert trigger (optional)**

Events are generated when a log-line satisfies event rule criteria. Event rule consists of a list of key, operator and value combinations that could be connected by AND conditions. Each combination consists of standard parameters such as Message, Application, Severity String, Facility String, Sender or some facet parameters which are specific to that log-line.

![Create alertable event rule modal window](<../.gitbook/assets/Screen Shot 2020-08-17 at 2.50.34 PM.png>)

By pressing the "Create event" Button, LOGIQ generates an event rule, a query & visualization graph for the time series DB and an alert trigger if the "create and activate alert on event rule" checkbox is checked.\
In this example, the event is generated when the message matches the regular expression “GET /V1/license” and other additional parameter criteria are met. Each triggered event is recorded by LOGIQ insights in the time series database. It helps to generate a visualization graph of the frequency of the events with respect to time. 

In this example, the query and time series visualizations can be found in the queries page as license_check query and license_check-vis visualization.\
****

![](<../.gitbook/assets/Screen Shot 2020-08-17 at 10.33.07 PM.png>)

Since the dashboard “EventTimeSeriesCharts” is selected in the above example the visualization will be embedded in that dashboard. Click on the dashboard and pick ”EventTimeSeriesCharts”

![Time series visualization](<../.gitbook/assets/Screen Shot 2020-08-17 at 2.58.55 PM.png>)

If required by selecting the checkbox “create and activate alert on event rule” and specifying a preconfigured destination for notifications the alert trigger is conveniently created.
