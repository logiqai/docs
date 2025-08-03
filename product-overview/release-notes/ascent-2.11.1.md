---
hidden: true
---

# Ascent 2.11.1

### Observe <a href="#observe" id="observe"></a>

**Fixes and Improvements:**

* **Authentication Settings Saving**\
  Fixed an issue preventing changes to authentication settings in the Settings > Authentication area. You’ll now be able to save or toggle these configuration options reliably.
* **Published Status in Dashboards and Queries**\
  It’s now possible to see whether dashboards and queries are published or not. This visibility was missing in previous versions.
* **Special Character Searches in Queries**\

* **Batch Enforcement with Proper Pagination**\

* **Policy Save Error Feedback**\
  If saving a policy fails, you’ll receive a clear message explaining what action is needed to complete the process.
* **Resource Selection Modal Redesign**\

* **Attribute Fetching for Static Assets**\
  The application will no longer show an error when trying to find certain static asset attributes, thanks to a fix in how those paths are handled.
* **Fetching Tags with Cookies**\
  Improved reliability for fetching tags related to resources, by enhancing how authentication cookies are passed in requests.
* **Metadata Fetch for “Check as Datasource”**\
  Resolved an issue where changes to authentication broke metadata fetching for checks being used as a datasource.
* **SQL Errors with NULL Cluster/Tenant**\
  Addressed a bug that returned errors when the system encountered NULL values for tenant or cluster columns in the resources database. Resources now display even if certain metadata columns are empty.
* **Report Execution Reliability**\
  Reports now execute as expected, instead of ending immediately with no results.
* **Search Resilience While Loading Dashboards**\
  Now, if you start typing in the dashboard search bar before dashboard data loads, your search text will be preserved and the search will still run when the data is ready.

### Fleet <a href="#fleet" id="fleet"></a>

**Fixes and Improvements:**

* **Deployment Status for Agent Configs**\
  When you assign a new config file to an agent, its deployment state is updated correctly and won’t remain stuck as “new.”
* **Agents Page Search Optimization**\
  Searching on the Fleet Agents page now waits until you finish typing (not on every keystroke), which means faster searches and less load on the server.

### Flow <a href="#flow" id="flow"></a>

**Fixes and Improvements:**

* **Groups Not Populating in Pipeline Rules**\
  The group dropdown selector in the Rules tab for Pipelines rules now appears correctly.
* **Alerts Tab - Fixed Search Issue**\
  You can now search for alerts by name or keyword in the Alerts section of the Pipelines dashboard, and the results will update immediately.
* **Action Button Tooltips in Pipelines**\
  The action buttons under Pipelines now include explanatory tooltips. Hovering over an icon will show what it does.

### Synthetics <a href="#synthetics" id="synthetics"></a>

**Fixes and Improvements:**

*

### General Platform/Ascent <a href="#general-platformascent" id="general-platformascent"></a>

*

### Known Issues <a href="#known-issues" id="known-issues"></a>

* **Groups Not Visible in Check Analytics “Groups View”**\
  There’s a current limitation where no groups appear in Check Analytics > Groups View and the Manage Groups tab. This issue has been identified and will be addressed in an upcoming release.

***

### Component Versions - Ascent v2.11.1

<table><thead><tr><th>Components</th><th width="410">Version</th></tr></thead><tbody><tr><td>Flash</td><td>v3.16.0</td></tr><tr><td>Coffee</td><td>v3.17.0</td></tr><tr><td>ASM</td><td>13.36.1</td></tr><tr><td>NG Private Agent</td><td>1.0.9</td></tr><tr><td>Check Execution Container: Browser</td><td>fpr-c-130n-10.2.1-716-r-2025.04.02-0-base-2.0.0</td></tr><tr><td>Check Execution Container: Zebratester</td><td>zt-7.5a-p0-r-2025.04.02-0-base-1.2.0</td></tr><tr><td>Check Execution Container: Runbin</td><td>runbin-2025.04.17-0-base-2.2.1</td></tr><tr><td>Check Execution Container: Postman</td><td>postman-2025.04.17-0-base-1.4.1</td></tr><tr><td>Bnet (Chrome Version)</td><td>10.2.1 (Chrome 130)</td></tr><tr><td>Zebratester</td><td>7.0B</td></tr><tr><td>ALT</td><td>6.13.3.240</td></tr><tr><td>IronDB</td><td>1.5.0</td></tr></tbody></table>

