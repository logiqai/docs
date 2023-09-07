---
description: 'Latest release: v3.6'
---

# Release Notes 🚀

### 🎉 LOGIQ.AI is now Apica 🎉

### v3.6

#### 📅 Mon, Sept 11, 2023

#### Welcome to the latest update of our product! We're excited to introduce several new features and improvements designed to enhance user experience.

* ALIVE (Autonomous Log Interaction Visual Explorer): ALIVE is a powerful interactive visualization tool designed to empower users in identifying issues and patterns within their applications. This innovative tool offers a rich and insightful representation of unstructured logs. Key features includes:
  * Autonomous Log Analysis: ALIVE autonomously analyzes logs, saving users time and effort.
  * Interactive Visualization: Enjoy an interactive and engaging experience when exploring log data.
  * Flow Representation: Understand the flow of log events with clear and intuitive visualizations.
  * Insightful Representation: Gain deep insights into your log data through meaningful visual representations.
  * Multivariate Analysis: Easily pinpoint issues across vast datasets at a glance.
  * Scalability: ALIVE scales effortlessly to accommodate your growing data needs, ensuring consistent performance.
  * Improved pattern compaction (PC) workload: With this release, we've enhanced the pattern compaction feature. Now, as the number of patterns increases, selected patterns can be further aggregated into the same group to prevent pattern count explosion. This process is called compaction. We've also added a button in the ingestion settings that allows you to disable or enable pattern compaction. Please note that this feature is not intended for use with static or small pattern sets, and excessive use of the PC action can result in pattern aliasing.
* Enhanced Onboarding Experience with App Tour: Introducing App Tour, designed to provide both new and returning users with a seamless introduction to our platform's key features. This guided tour ensures a smooth and intuitive navigation experience right from the start, helping you quickly become familiar with our app's functionalities and empowering you to make the most of our platform.
  * App tour coverage:
    * Explore (Data, Topology, Flows)
    * Dashboards
    * Source Extensions
    * Search
    * Rules
    * Forwarder
    * Queries
    * Create Rule
* Moved Source Extensions, Forwarders, Rule Packs and Import dashboards to new Integrations page.
* New Source Extensions
  * [SNMP Source Extension](https://docs.logiq.ai/integrations/snmp)
  * [Apica Source Extension](https://docs.logiq.ai/integrations/apica-synthetic-monitoring): The Apica Source Extension is a component designed to integrate with the Apica Synthetics and Load test platform. Its main purpose is to retrieve check results from the Apica platform and make them available for further processing or analysis within another system or tool.
* New Forwarders which can help users selectively send specific log data to downward destinations based on their filtering criteria, thereby reducing the amount of data stored and analyzed. This can lead to cost optimization as it allows users to focus their resources on the most relevant and important log data, rather than storing and processing unnecessary or redundant information.
  * [Coralogix](https://logflow-docs.logiq.ai/forwarding-to-monitoring-tools/coralogix-forwarding)
  * [GCP BigQuery](https://logflow-docs.logiq.ai/forwarding-to-data-warehouse/gcp-bigquery)
  * [Azure Log Analytics](https://logflow-docs.logiq.ai/forwarding-to-monitoring-tools/azure-log-analytics-forwarding)
* Topology view Enhancements ✨ Recent enhancements in the topology view is the inclusion of the total events information. This improvement provides users with a clearer understanding of the overall event activity within the system or network.
* Pipeline Changes:
  * Pipeline Application Filtering Support
    * We're excited to introduce support for pipeline application filtering in this release. With this enhancement, users can efficiently filter log data when managing multiple applications, streamlining their data management processes.
  * Error Indicator
    * We've also added an error indicator to the Pipeline View. This indicator serves as a valuable visual cue when forwarding logs to destinations, helping users quickly identify and address any issues in their data flow to downward destinations.
* Faster Reports
  * In this release, we've significantly improved report generation speed by removing the 10-second polling delay.

#### Search

* Optimized Search
  * We've enhanced search performance by further optimizing the search query parallelism, ensuring quicker and more efficient results retrieval.
* Faster Search
  * In this release, we've enhanced the speed of our search functionality.
* Added Support for More than 10 Tabs in Search Page
  * Now, you can enjoy greater flexibility with our Search Page as we've added support for more than 10 tabs, allowing you to organize and manage your search tasks more effectively.
* Enhancement in Search feature by adding Regex for Extract.
  * Get a holistic taxonomy of logs by automatically categorizing them based on their content, context and other characteristics. This capability provides users with a way to extract and classify logs automatically, improving the speed and accuracy of log-analysis. This saves time and effort by automating the process of field extraction, eliminating the need for users to manually identify and extract fields .

#### Other Enhancements:

* Aggregate Settings Persistence
  * We've introduced the convenience of persistent aggregate settings. Now, when users select an aggregate, the system will remember their choice, ensuring that their selection remains consistent across sessions.
* Table View for Structured Data
  * We've deprecated the Tree view and introduced a more user-friendly Table View for structured data derived from log lines.
* Revamped Forwarder Selection UX
  * Experience an enhanced user interface when selecting forwarders during creation. Our redesigned forwarder selection process is more intuitive and efficient.
* Log-to-Traces Proxy
  * We've built a versatile proxy that can seamlessly convert logs into traces. This allows logs to be stitched into multiple spans, forming a comprehensive trace for improved monitoring and analysis.
* Multiple Widgets in Dashboards
  * Enhance your dashboards with ease. Users can now add multiple visualizations related to various queries in a single step, providing more flexibility in dashboard creation.
* Distribution Flow
  * We've deprecated the distribution flow feature from the forwarders page, making it even more accessible. Users can now access distribution flow directly from the explore page.

#### Bug Fixes

* Increased gRPC Recovery Limits
  * We've addressed an issue that could sometimes result in partial search results. By increasing the gRPC recovery limits, we've improved the reliability of search operations in our platform.
* Various Bug fixes, UI and Performance Improvements ✨.

### We Value Your Feedback

If you have any questions, encounter issues, or want to share your thoughts, please don't hesitate to contact our [support team](mailto:support@apica.io). Thank you for choosing Apica as your data fabric partner. We look forward to continuously improving your experience.

***

***

## v3.5.9.1 <a href="#uversionv359u" id="uversionv359u"></a>

### **📅 Fri, Mar 24, 2023**

*   **Topology-powered root-cause analysis**.

    Visualize your data streams as a topology with drill down to errors and warnings for faster root causes. Helps visualize the health of your applications. Users can quickly investigate the issues by clicking errors or alerts.
*   **Data flow Pipelines**.

    The pipeline is a series of processes or stages through which data flow systematically and efficiently. Helps to visualize the flow between nodes, rules, and filters applied for the data flow. Shows the inflow and outflow information of data, and also helps in identifying the data loss or optimizing the data flow to forward destinations.
*   **Search results aggregates**.

    Buit-in Pivot table makes it easy to analyze large data sets from search queries. Summarize or Visualize a set of data points for instant analysis. Some common examples of aggregation functions include(Count, Value, Sum, Count Unique Values, List Unique Values, Average, Median, Min, Max). Aggregation functions are used to summarize large datasets into a more manageable form for further analysis and visualization. And includes different types of visualizations (Table, Line chart, Area chart, Scatter chart, Dot chart, and Multiple pie chart).
*   **Re-designed Landing page**.

    Instantly get access to valuable insights when you login into our redesigned Explore page. Users now log in and directly land on the Explore page with quick summaries at their fingertips.

    1. Introduced counter widgets for EPS, Total Flows, Total Events, Forwarders, and Source Extensions.
    2. Added a new Event Statistics column, which has counts of (Errors, Alerts, Critical, Emergency), (Warnings) and (Total) events.
*   **OSSEC HIDS Mappings**

    Automatically map OSSEC HIDS event severity and log messages for Linux and Windows environments.
* **Added support for exporting events and metrics from** [**Apache Beam**](https://docs.logiq.ai/integrations/apache-beam) **to Apica Ascent**.
*   **OpenTelemetry `otel.status_code` Mapping**

    Detect OpenTelemetry severity and level embeddings and map them into severity levels.
* **Memory and performance improvements**.
* **Automated agent installation for Linux and Windows**.
