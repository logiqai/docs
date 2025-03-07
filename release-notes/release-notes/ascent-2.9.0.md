# Ascent 2.9.0

#### **ASM 13.31.0**

Features

Automation for Checks and Alerts&#x20;

• Added support for CI/CD pipeline to streamline the check creation and maintenance process through ASM APIs, reduce manual efforts, and ensure consistency across different environments through automation.&#x20;

• Ability to perform CRUD operations for ZebraTester, Browser and URL checks&#x20;

• Ability to create, upload and assign Zebratester and Browser scenarios for checks&#x20;

• Ability to create and assign Email, SMS and Webhook alert targets or alert groups

Chrome 130 upgrade of Browser checks&#x20;

• All existing Browser checks have been upgraded from Chrome 115 to Chrome 130

• All new Browser checks run on Chrome 130

NG Private locations&#x20;

• Private locations/agents can be shared among sub customer accounts to run checks

• User's own CA certificates can be used for checks in Private locations to monitor customer's internal applications

Apica Grafana Plugin&#x20;

• Apica Grafana plugin has been upgraded to 2.0.11&#x20;

• Added support for page metrics which allows users to see response time for specific pages instead of the entire scenario metrics

**Bug Fixes**

• Fixed the bug where invalid "acceptedCodes" were being accepted for URL checks in POST /checks/url-v2 API

#### Release Notes - Ascent 2.9.0

Ascent Synthetics (ASM+)

Features

Check Management&#x20;

• New check types introduced: Browser, Postman, Traceroute, Mobile Device and Compound&#x20;

• Added support for full workflow of check management: Edit, Delete, Clone and Run Check • Added support for Bulk Edit, Run and Delete checks&#x20;

• Inclusion and Exclusion periods can be added in check schedule

Private Location and Agent Management&#x20;

• Introduced full self-service (Add, Edit, Delete, Reissue Certificate) of new check-type agnostic Private agents which can be grouped into Private locations&#x20;

• Introduced the ability to Add, Edit, Delete, Enable, and Disable Private locations and associate Private repositories, giving more control over location and check execution.&#x20;

• Added a "Private Locations" section in the UI, allowing easy navigation and management of these locations.

Check Analytics&#x20;

• Enabled alerting and reporting on checks&#x20;

• Alerts and reports for a particular check can be created directly from the check page&#x20;

• Screenshots taken during a Browser check execution can be viewed in Check Analysis page

Bugs&#x20;

• Fixed a bug where filter criteria was not working correctly in the Checks page&#x20;

• Fixed a bug where some check results were missing in the Check Details page

**New Features and Enhancements**

### Fleet

* **Fleet Agent Limits**: Enforced license-based agent limits.&#x20;
* **Telemetry Enhancements**: Added telemetry support for Fleet agents.
* **Fleet UI Revamp**: Major UI improvements, better agent configuration management, and pagination fixes.
* **Fleet Summary Table**: Redesigned the summary table for better usability.
* **Kubernetes Agent Status**: Fleet UI now displays Kubernetes agent statuses.

**Flow**

**Observe**

* **Data Explorer Graph Enhancements**: Enhanced GroupBy plotting with multiple Y-axis selection.
* **Widgets Enhancements**: Added delete functionality and improved widget load time.
* **New Chart Type**: Introduced Pie and HoneyComb charts for visualization.
* **Grafana to Data Explorer**: Added Grafana JSON conversion support in Data Explorer.
* **GenAI Enhancements**: Integrated "Log Explain" feature for enhanced log analysis in ALIVE.
* **Data Explorer Enhancements**: Improved metrics screen and query list support.
* **Dashboard Optimization**: Reduced load times for Data Explorer dashboards and preserved widget data across tabs.
* **RCA Workbench**: Introduced diagnostics and debugging features based on DE widgets.
* **Dashboard Validation**: Added validation for Data Explorer dashboard creation.
* **React Page Migration**: Login, Setup, Signup, Reset, and Forgot Password pages migrated to React (TSX), reducing tech debt.
* **Ascent Invitation Feature**: Implemented invitation feature for new users via Casdoor.
* **Casdoor Sync**: Synced Casdoor users and groups with the Ascent database.
* **Port Management**: Resolved open TCP/UDP port issues.
* **Casdoor Integration**: Enhanced authentication, session management, and email integration.
* **API Key Support**: Added API key support for Casdoor in Ascent.
* **Casdoor Mail Service**: Integrated Ascent mail service with Casdoor for email functionality.
* **Casdoor Signing Certificates**: Added support for Casdoor signing certificates to enhance security.

***

**Ascent Bug Fixes**

* **GCP PubSub Plugin**: File loading issue resolved.
* **ResizeObserver Compatibility**: Fixed compatibility with the latest Chrome version.
* **Alert Email Output**: Query output truncated in triggered alert emails for better readability.
* **Agent Sorting**: Fixed sorting functionality by "Last Modified" in Fleet UI.
* **Incorrect Trace Volume**: Fixed trace volume display on the Ascent landing page.
* **Alert Bug Fix**: Fixed discrepancies in triggered alert counts displayed in the navbar.
* **Pipeline View**: Resolved visual bugs in forwarder mapping and improved rule persistence.
* **Fleet Improvements**: Enhanced Fleet installer, improved Kubernetes token creation, and fixed pagination issues.
* **Password Generation Visuals**: Improved user interface for password generation in Ascent.
* **Query Save Fix**: Resolved unknown error when saving queries in the Freemium tier.
* **Moving Average Bug**: Fixed ADF Query creation issues with AI-based algorithms (Moving Average).
* **Alert UNKNOWN Issue**: Resolved alerts triggering with an UNKNOWN state.
* **Alert Evaluation Issues**: Fixed issues with alerts not evaluating after the first trigger.
* **SNMP Source Bug**: Fixed SNMP ingest source extension bugs.
* **Fluent-Bit Installation**: Addressed issues with Fluent-Bit post-agent manager installation.
* **Dual Active Packages**: Resolved the issue of showing two active packages in Fleet.
* **Inclusion/Exclusion Fixes**: Addressed syntax and period-saving issues.
* **Certificate Upload**: Fixed certificate upload issues and removed the feature from Freemium.
* **Default Otel Configuration**: Updated default Otel configuration for metric ingestion.
* **Platform Validation**: Enhanced platform validation in Fleet.
* **Fleet Assign Package Error**: Fixed package assignment issues.
* **Disable Pattern Signature**: Disabled pattern signature functionality in Freemium.
* **Namespace Bug**: Resolved incorrect namespace selection in Data Explorer.
* **Fleet Advanced Search**: Fixed bugs and added improvements to advanced search functionality.
* **Dark Mode**: Fixed UI inconsistencies in dark mode, including Waterfall statistics and button styling.
* **Fleet Installation**: Resolved installation errors on Linux and Windows.
* **Kubernetes Dropdown Fix**: Fixed duplicate Kubernetes entries in Fleet dropdowns.
* **Configuration Refresh**: Addressed package reassignment and configuration refresh issues.
* **Documentation Updates**: Updated user and technical documentation.

