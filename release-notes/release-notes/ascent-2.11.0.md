# Ascent 2.11.0

### **Platform-Wide Highlight: Casdoor Integration**

This release introduces full integration with **Casdoor**, our new authentication and authorization system -  a foundational upgrade to Apica’s identity and access management model.

#### Key Benefits:

* **Centralized Login & Session Management**: Secure, unified authentication across all modules.
* **Fine-Grained Policy Enforcement**: Access control enforced at the resource level for dashboards, alerts, plugins, and more.
* **Enhanced Security**:
  * Secure, HTTP-only cookies
  * Configurable idle timeouts (default 20 mins)
  * Rate-limiting and account lockout after failed logins
  * Restriction on concurrent sessions
* **Future-Ready**: Lays the groundwork for SSO, impersonation workflows, and compliance-aligned access control.

***

### **Observe**

#### New Features

* Added in-built YAML-based creation for alerts, queries, and data sources.

**Policy Management**

* A brand-new **Policy Management** screen is now available under the **IAM** section in Settings.
* Admins can create, assign, and manage policies directly from the UI.
* Resources such as users, dashboards, alerts, data sources, and plugins can now be managed via policies.
* A new **resource table** with search and a **Select All** option improves policy creation workflows.

**Security Enhancements**

* Casdoor sessions now use secure, HTTP-only cookies.
* Idle session timeout is configurable; all cookies are cleared upon logout.
* Accounts are locked after 3 failed login attempts.
* Concurrent logins with the same credentials are blocked.
* Sessions now terminate explicitly during logout.
* TLS/SSL usage enforced across the board.
* Session login ID is rotated after each login to prevent fixation attacks.

**Expanded Role and Permission Enforcement**

* Policies and permissions are now enforced for key entities including:
  * Dashboards, queries, metrics, alerts, input plugins, and services.
* Backend access control is fully enforced using Casdoor's policy engine.

**API and Documentation Improvements**

* Flash API Swagger documentation is now complete and publicly accessible.
* Enhanced Swagger docs for pipelines, dashboards, widgets, events, and more.
* Tags and Resources APIs now support **pagination and search**.

**User Experience**

* The UI now handles session expiration and logout scenarios gracefully.
* The app can now follow your system’s dark/light mode automatically.

***

#### &#x20;Changes and Improvements

**Performance and Usability**

* Route-level authorization prevents access via direct URLs for unauthorized users.
* UI animations optimized for faster load times.
* Font download size reduced by 40%.
* Minor improvements to batch enforcement logic on the user list page.

**API and Backend**

* Tag and resource syncing refactored for data integrity.
* Migration scripts now clean up deprecated dashboards and migrate datasource groups to policies.
* Oracle DB is now supported as a data source.

**UI and Visualization**

* Dashboard and pipeline pages updated with better grouping and detail views.
* Widgets now support:
  * Full-screen mode
  * Exponential value formatting
* Visual fixes for cancel buttons, logo alignment in shared dashboards, and widget resizing.

***

#### Bug Fixes

* Fixed issue where API key field was reset after editing user groups.
* `/users/me` no longer crashes if permissions are missing; user is redirected cleanly.
* Dashboard API now correctly honors Casdoor-based permissions.
* Check group view shows accurate check counts for all levels.
* Counter visualizations now support text color changes and unselection behavior.
* Data Explorer no longer hangs when a saved query is deleted.
* Visual fixes for dark mode, Y-axis labels, and widget resizing.
* Logout message now shown properly; session timeouts handled smoothly.
* Alerts page behaves predictably when data is missing; no more random column rendering.
* Email formatting fixed in “Generate Password” emails.
* Reduced redundant calls to `/api/alerts`.
* Corrected role-to-group linkage.

***

### **Fleet**

#### New Features

**Policy Management for Fleet**

* Policies can now be applied to **package applications** and fleet-specific actions based on user roles.
* A streamlined UI makes it easier to manage fleet permissions via Casdoor integration.

**Agent Management**

* Agents can be filtered by hostname, version, type, or name.
* Agent detail pages now cache responses with defined stale times for faster loading.
* Added **force refresh** option to pull the latest agent data.

**Configuration and Packages**

* Deployed agents auto-refresh every 30 seconds for real-time status.
* YAML-based support added for defining:
  * Alerts
  * Queries
  * Data sources
  * Dashboards (via DataExplorer)

**Security and Access**

* Concurrent logins now blocked via Casdoor.
* **Casbin now supports multiple roles per user**, enabling more flexible access models.
* Vault and certificate access now uses IDs instead of names.

***

#### Changes and Improvements

* Admin check removed for `get/set account repo` endpoint.
* Agent detail performance improved with caching and backend load reduction.
* Agent-related tables now reload in real time.
* Fleet entities are now registered in the resource table for consistent access control.
* CI pipeline enhancements with mandatory test coverage.

***

#### Bug Fixes

* Fixed CPU spikes when agents are stopped.
* Fixed Kubernetes agent package import failures.
* GUI now properly supports creating configs for Kubernetes.

***

### **Ascent Synthetics**

#### New Features

**Scenario Management**

* GitLab integration added for repo profiles (joins GitHub, Azure, Bitbucket support).
* Browser Scenario updates:
  * Drag & drop steps
  * Real-time progress updates
  * Cancel during test run
  * Bulk step deletion
  * Improved tooltips

**UI/UX Enhancements**

* Auto-refresh added to all check views (Map, List, Grouped).
* Upload buttons and labels better aligned.
* Improved error handling for certificate creation.
* Icons and padding polished across scenario views.

**Policy & Permissions**

* Tag management and private location access now governed by policies.
* SLA alignment and group filters improved on check visualizations.
* Checks data source now supports multi-check results.

***

#### Changes and Improvements

* Improved validation for certificate management.
* Button labels and filter UI match latest design guidelines.
* Refined scenario group management and conditional rendering.
* Kafka client updated to use **franz**.
* Check runner supports host exclusions for proxy cases.
* Extended function support: `encode`, `decode`, `text`, `mask`, `net`, `time`.

***

#### Bug Fixes

* Removed duplicate entries in `casbin_user_rule` and fixed group mismatch.
* Fixed persistence issue with permission-role mappings on Flash restart.
* Addressed check runner bugs with self-signed certs and resource URL normalization.
* Zebratester checks now render all expected steps.
* Various fixes for compound checks, location rendering, and UI spacing.

***

### **Flow**

#### New Features

* Forward rules now integrated into pipeline processing.
* Enriched Swagger documentation for pipelines with examples.
* New **Visualize** mode added to the pipeline management page.

***

#### Changes and Improvements

* Build process updated with stricter test enforcement.
* Server-side filtering and execution order support for pipelines.
* Grouping enhancements for shared rules by namespace and app.

***

#### Bug Fixes

* Fixed graph rendering issues in pipeline metrics.
* Resolved certificate creation and encrypted secret issues in Vault.

***

### **IronDB**

#### New Features

* Grafana plugin updates:
  * Cleaned up IRONdb datasource links
  * Updated signing and deployment instructions
  * (Planned) support for React-based plugin development

***

#### Changes and Improvements

* Lowered broker startup memory footprint.
* Upgraded Flatbuffers for security.
* Enhanced Kafka config via `librdkafka`.

***

#### Bug Fixes

* Fixed Coverity and ASAN build issues.
* Resolved Prometheus ingestion problems during IRONdb reconstitute.
* Fixed Graphite Web handling of empty arrays.
* Addressed logging and dropped message scenarios in IRONdb Relay.
* Fixed compilation with GCC 13 and Ubuntu 24.04.

***

### **ASM Legacy**

#### New Features

* New API endpoints added for check management in Ascent On-Prem.
* Improved support for editing and viewing all check types.

***

#### Changes and Improvements

* Updated default RTSE settings.
* Improved integration profile and webhook handling.

***

#### Bug Fixes

* Fixed visibility issues for Videnca reports on specific silos.
* Fixed filtering and interval behavior for manual mobile app checks.
* ASM API fixes for check config and host exclusions.
* SSL handshake and script execution issues resolved.
* Fixed deprecated URL references and UI bugs in JSONPath extractor.

***

### **General Improvements**

* **Documentation**: Swagger specs enhanced across the platform.
* **Performance**: Backend syncing tasks are faster and more stable.
* **Accessibility**: UI improvements for dark mode, screen responsiveness, and keyboard navigation.
* **Reliability**: Better handling of long agent names, check filters, and data alignment across pages.
