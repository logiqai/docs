# Ascent 2.6.0

### **Apica Ascent** <a href="#adf-one-platform-ascent_august_2024" id="adf-one-platform-ascent_august_2024"></a>

***

**Features**

* **React-grid-layout Integration**: React-grid-layout has been integrated into Data Explorer for widget flexibility.
* **Legend Component**: A separate component for displaying legends in Data Explorer widgets was implemented which shows statistics of the data that is being rendered in the widget.
* **Port Management via UI**: Added support for enabling and disabling k8s cluster ports via the UI.
* **Ping Checks**: Implemented Ping Checks in Check Management.
* **Port Checks**: Implemented Port Checks in Check Management.
* **Logs as a Data Source**: Apica logs can now be integrated as a data source for Data Explorer and users can create/run queries on top of logs. This also allows a new way to do alerting in the platform on top of logs.
* **File Compare Graph Y-axis Scale**: The Y-axis of the File Compare graph now supports two modes: PS count and percentage.
* **PS Compare Anomaly Marker**: Added anomaly marker for better visualization in PS Compare.
* **Dashboard Data Migration**: Dashboard data is now formatted into Data Explorer and moved from LogiqHub to ApicaHub.
* **Legacy Dashboard Converter**: A converter was implemented to convert legacy Dashboard JSON to Data Explorer JSON format.
* **Data Explorer: Editing Controls and Breakpoints**: Added editing controls and breakpoints in Data Explorer.
* **Scatter Chart Support**: Data Explorer now supports scatter chart visualizations.
* **Dark Theme**: Improved dark themes for multiple screens, including Logs & Insights, Dashboards, Topology, and Pipelines.
* **Dashboard Import in Data Explorer Format**: Frontend changes implemented to import dashboards in Data Explorer format.
* **Check Analytics Integration**: Enhanced check analytics by integrating it with a reports page.

#### **Improvements** <a href="#improvements" id="improvements"></a>

* **Check Status Widget**: Added custom configuration options for the check status widget.
* **Performance Improvements**: Extended efforts to improve the performance of Data Explorer for smoother usage.
* **Gauge Chart Design**: Modified the Gauge chart design, providing more user-configurable options and units for charts.
* **New Visualizations in Data Explorer**: New widget types added, including Check Status, Stat, Size, Date/Time, and Scatter chart visualizations.
* **Statistical Data in Legends**: Introduced statistical data to the new legend component in Data Explorer.
* **Auto Gradient Colors**: Implemented an automatic gradient color generator for area charts in Data Explorer.
* **Grafana Dashboard Converter**: Developed a converter for Grafana Dashboards to be compatible with Data Explorer.

#### **Bugs** <a href="#bugs" id="bugs"></a>

* **Invalid Log Timestamp**: Fixed an issue where log timestamps were invalid.
* **Tracing Volume Query Issue**: Addressed an issue affecting tracing volume queries.
* **File Compare Graph Display**: Resolved issues with the display of the file compare graph summary.
* **Data Explorer Page Crashing**: Fixed errors causing the Data Explorer page to break due to undefined values.
* **Widgets Deletion Handling**: Implemented proper handling for widget deletion to prevent crashes.
* **Tab Loss on Reload**: Resolved the issue where Data Explorer page tabs were lost on reload.
* **Chart Label Issues**: Fixed chart label issues and made improvements to chart rendering.
