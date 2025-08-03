# Ascent 2.8.0

#### Release Notes - Ascent October 2024

**Overview**\
This release introduces a host of updates to enhance user experience, streamline operations, and address known issues across Fleet, Data Explorer, the Ascent platform, and ASM+. New features and improvements focus on usability, performance, and customization, while bug fixes enhance platform stability and reliability.

***

#### **New Features and Enhancements**

**OpenTelemetry**

OpenTelemetry Collectors can now be configured to use the standard ingest endpoints when pushing data to Apica Ascent
1. Traces - /v1/traces
2. Logs - /v1/logs
3. Metrics - /v1/metrics

**Telemetry Pipelines**

1. New forwarders added for Oracle Cloud
   * OCI Buckets
   * OCI Observability & Monitoring - Logs

**Freemium Support**

Experience Apica Ascent with the Freemium release. The Freemium is a **FREE FOREVER** release which includes all the capabilities of the Apica Ascent Intelligent Data Management Platform available as a convenient SaaS offering
1. Fleet Management
2. Telemetry Pipelines with support for platforms such as **Splunk**, **Elasticsearch**, **Kafka**, **Datadog** among others
3. Digital Experience Monitoring (Synthetic Monitoring for URL, Ping, Port and SSL Checks)
4. Log Management
5. Distributed Tracing
6. Infrastructure Monitoring
7. Enterprise ready with features such as SAML based SSO
8. ITOM integration with platforms such as **PagerDuty**, **ServiceNow**, and **OpsGenie**

**Fleet Updates**

1. **Agent Management**:\
   &#x20;  \- Introduced controls for managing agents within the Fleet UI for better administration.\
   &#x20;  \- A summary table was added to display agent statistics, providing quick insights.\
   &#x20;  \- Enabled rules for assigning configurations or packages to agents.\
   &#x20;  \- User-defined Fleet resource types (rules, alerts, agent\_types, configurations, and packages) can now be imported via Git.\
   &#x20;  \- Fleet REST API search endpoints now support the `?summary` query parameter for result summarization.\
   &#x20;  \- Expanded fleetctl CLI tool capabilities to manage Fleet API resources directly.
2. **Advanced Search and Customization**:\
   &#x20;  \- Users can save and retrieve advanced search queries in the Fleet Advanced Search Modal.

**Data Explorer Enhancements**

1. **Improved Analytics Options**:\
   &#x20;  \- Added support for PostgreSQL, expanding data integration capabilities.\
   &#x20;  \- Enhanced GroupBy functionality and a “Select All” label for better data analysis.\
   &#x20;  \- Enabled parameterized queries for dashboards, allowing dynamic user input for real-time customization.\
   &#x20;  \- Users can edit the dashboard header query and set the dropdown type (query, enum, or text) for customization.
2. **Visualization Improvements**:\
   &#x20;  \- Introduced a DenseStatusType chart to monitor active and inactive pods/instances in real time.\
   &#x20;  \- Added time zone customization for chart displays.\
   &#x20;  \- Optimized dark theme UI components with updated icons and design assets.

**Ascent Platform Enhancements**

1. **ASM UI Enhancements**:\
   &#x20;  \- Integrated repository and certificate management for streamlined admin controls.\
   &#x20;  \- Implemented a persistent last-view setting on the Check Management page.
2. **General Improvements**:\
   &#x20;  \- Enhanced navigation with streamlined redirection flows for faster page loads.

**AI/ML and GenAI Enhancements**

1. **Pattern-Signature Processing**:\
   &#x20;  \- Improved compaction with meaningful aliasing during pattern-signature (PS) merging.\
   &#x20;  \- Enhanced performance through PS coding representation for faster processing and UI responsiveness.\
   &#x20;  \- Fixed functionality for PS compaction at the backend.
2. **GenAI Features**:\
   &#x20;  \- GenAI document search functionality was added to the NavBar.

***

#### **Bug Fixes**

**Fleet UI and Backend Fixes**

1. **UI and Agent Issues**:\
   &#x20;  \- Resolved banner display inconsistencies during agent updates.\
   &#x20;  \- Fixed errors in anonymous report generation for Grafana Alloy.\
   &#x20;  \- Fixed agent-manager token refresh failures on Windows hosts.
2. **Backend and API**:\
   &#x20;  \- Fixed errors preventing default configuration/package assignments via the install endpoint.\
   &#x20;  \- Resolved OpAMP client failures and Windows socket exhaustion issues.\
   &#x20;  \- Corrected lookup errors for agents by instance ID during OpAMP registration.

**Data Explorer Fixes**

1. **Performance and Stability**:\
   &#x20;  \- Resolved crashes on the Data Explorer page.\
   &#x20;  \- Corrected schema issues and bugs affecting `*`-based queries and widget calculations.\
   &#x20;  \- Fixed default date-type inputs and adjusted other input defaults for smoother workflows.
2. **UI Updates**:\
   &#x20;  \- Fixed CSS and overflow issues in modals and alert render pages.

**General UI and Usability Fixes**

* Resolved usability regressions from the v3.11.2 update, improving input defaults and widget updates.

***

#### **Miscellaneous Enhancements**

1. **Fleet-Specific Improvements**:\
   &#x20;  \- Improved response times in Fleet views for queries involving large datasets.
2. **Ascent Platform**:\
   &#x20;  \- Resolved permission issues for non-admin users in the Namespace endpoint.

***

These updates reflect our commitment to delivering a robust and user-friendly platform. As always, we value your feedback to enhance our services further.
