# Ascent 2.7.0

### **ADF** <a href="#adf" id="adf"></a>

#### **New Features & Enhancements** <a href="#new-features-and-enhancements" id="new-features-and-enhancements"></a>

1. **Fleet Management Improvements:**
   * **Fleet UI Enhancements:** Redesigned Fleet management screens, including Agents and Configuration, with consolidated controls for improved usability and support for Dark Theme.
   * [**Kubernetes Environment Support**](https://docs.apica.io/fleet-management/list-of-agents/opentelemetry-kubernetes)**:** Introduced support for Kubernetes environments in Fleet, enabling better agent management and installation flexibility.
   * **Fleet Agent Support for** [**OpenTelemetry Collectors**](https://docs.apica.io/fleet-management/list-of-agents/opentelemetry-collector)**,** [**Datadog**](https://docs.apica.io/fleet-management/list-of-agents/datadog-agent) **and** [**Grafana Alloy**](https://docs.apica.io/fleet-management/list-of-agents/grafana-alloy): Expanded the ecosystem of supported agents with compatibility for OpenTelemetry Collector, Datadog and Grafana Alloy agents.
   * [**Agent Liveness Status Metrics**](https://docs.apica.io/fleet-management/overview)**:** Implemented new metrics to monitor the liveness status of each Fleet agent, ensuring better visibility and alerting.
2. [**Data Explorer**](https://docs.apica.io/data-management/overview-1/creating-json-schema) **Enhancements:**
   * **Y-Axis Multi-Column Plotting:** Enhanced Y-axis plotting, allowing for the selection and visualization of multiple columns, making complex data analysis simpler.
   * **Time Range in Headers:** Added time range indicators in the header, improving context and navigation during data exploration.
   * **Custom Chart Integration:** New customizable charts, such as Counters, are available for Data Explorer, providing enhanced visualization options.
   * **Color Selection for Widgets:** Users can now select colors for each widget on the Data Explorer page, making it easier to personalize and distinguish visual components.
3. **UI/UX Improvements:**
   * **Advanced Search for Fleet:** Enhanced search capabilities with a new advanced search feature, making it easier to locate specific data and agents.
   * **Dark Mode Icons & Design Adjustments:** Optimized icon sets and UI components for a more consistent experience in dark mode.
   * **New Toggle & Theme Options:** Added a toggle for switching between Dark and Light modes, giving users more control over their viewing experience.
4. **Integration & API Updates:**
   * **Grafana Integration:** Implemented a converter to transform Grafana JSON into Data Explorer JSON format, simplifying the migration of dashboards.&#x20;
   * [**Gitbook AI Powered Search**](https://docs.apica.io/logiq-events/ai-powered-search)**:** Users can now ask questions directly in the search bar using Gitbook AI and receive answers instantly, enhancing accessibility to documentation and support. :brain:
5. **Performance & Optimization:**
   * **Lazy Loading Implementation:** Optimized the application by implementing lazy loading, improving initial load times, and reducing resource consumption.
   * **Custom Hooks for Skipping Component Mount Calls:** Enhanced performance by introducing custom React hooks to skip unnecessary component mounts, minimizing UI lag.
6. **User Onboarding:**
   * **Improved Onboarding Experience:** A dedicated onboarding screen for new users has been added to streamline the setup process and introduce key features.

#### **Bug Fixes** <a href="#bug-fixes" id="bug-fixes"></a>

1. **Fleet Management:**
   * Fixed issues where disconnected Fleet agents could not be deleted.
   * Resolved problems with log collection on Windows machines.
   * Addressed duplicate agent entries when reinstalling Fleet agents.
2. **Data Explorer:**
   * Corrected data inconsistency issues when switching between dashboards.
   * Fixed bugs related to alert tabs being incorrectly linked across dashboards.
   * Resolved intermittent behavior where data from one dashboard was erroneously stored in another.
3. **ALIVE:**
   * Improved the alignment and visualization of PS compare graphs and log comparisons.
   * Added zoom-in and enlarge options for better graph analysis.
   * Enhanced visual feedback for log loading during comparisons.
4. **UI Bug Fixes:**
   * Resolved AI button shadow and sizing issues for a more polished interface.
   * Corrected modal rendering in header dropdowns for persistent selections across tabs.
