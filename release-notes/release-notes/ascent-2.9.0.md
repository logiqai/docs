# Ascent 2.9.0

#### Release Notes - Ascent November and December 2024

**New Features and Enhancements**

* **Data Explorer Graph Enhancements**: Enhanced GroupBy plotting with multiple Y-axis selection.
* **Widgets Enhancements**: Added delete functionality and improved widget load time.
* **New Chart Type**: Introduced Pie and HoneyComb charts for visualization.
* **React Page Migration**: Login, Setup, Signup, Reset, and Forgot Password pages migrated to React (TSX), reducing tech debt.
* **Ascent Invitation Feature**: Implemented invitation feature for new users via Casdoor.
* **Casdoor Sync**: Synced Casdoor users and groups with the Ascent database.
* **Fleet Agent Limits**: Enforced license-based agent limits.
* **Kubernetes Agent Status**: Fleet UI now displays Kubernetes agent statuses.
* **Grafana to Data Explorer**: Added Grafana JSON conversion support in Data Explorer.
* **Port Management**: Resolved open TCP/UDP port issues.
* **GenAI Enhancements**: Integrated "Log Explain" feature for enhanced log analysis in ALIVE.
* **Fleet UI Revamp**: Major UI improvements, better agent configuration management, and pagination fixes.
* **RCA Workbench**: Introduced diagnostics and debugging features based on DE widgets.
* **Casdoor Integration**: Enhanced authentication, session management, and email integration.
* **Telemetry Enhancements**: Added telemetry support for Fleet agents.
* **Data Explorer Enhancements**: Improved metrics screen and query list support.
* **Fleet Summary Table**: Redesigned the summary table for better usability.
* **API Key Support**: Added API key support for Casdoor in Ascent.
* **Dashboard Optimization**: Reduced load times for Data Explorer dashboards and preserved widget data across tabs.
* **Dashboard Validation**: Added validation for Data Explorer dashboard creation.
* **Casdoor Mail Service**: Integrated Ascent mail service with Casdoor for email functionality.
* **Casdoor Signing Certificates**: Added support for Casdoor signing certificates to enhance security.

***

**Bug Fixes**

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

