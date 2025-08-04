---
hidden: true
---

# Ascent 2.11.1

### Observe <a href="#observe" id="observe"></a>

#### Improvements & General Changes

* **Resource Selection Modal Enhancement**: The resource selection modal in the policy management page has been improved. Users now benefit from a clearer layout, added search bar, multi-selection support, resource preview, responsive design, and clearer call-to-action buttons.
* **Batch Enforcement with Pagination for Ascent Resources**: Pagination has been implemented in batch enforcement for resources, helping users navigate and enforce policies efficiently. User feedback and loading indicators have also been added to enhance the experience.
* **Banner for Policy Save Errors**: Users now see an appropriate banner with actionable messages when saving a policy fails, guiding them on how to successfully save their changes.
* **Revert Pagination Fixes**: Pagination-related changes were reverted as tracked in internal change 13119.

#### Bug Fixes

* **Authentication Settings Save Failure**: Fixed an issue where changes to authentication settings in Apica Ascent could not be saved. Now the settings are reliably updated.
* **Dashboard/Query Publish Visibility**: Resolved a problem where users could not see if dashboards or queries were published.
* **Fix for Missing Attribute (STATIC\_ASSETS\_PATH)**: Addressed a bug where the application could not find the required attribute, ensuring smoother operation.
* **SQL Scan Error for NULL Tenant/Cluster Values**: Fixed issues in the resources table that caused API failures when tenant or cluster values were NULL, ensuring stable resource queries.
* **Check Analytics Split View Error**: Clicking "Split View" in Check Analytics no longer throws a generic error.
* **Metadata Fetching for Check as a Datasource**: Ensured metadata fetching works as expected after Casdoor-related changes.
* **Flawed Sorting in Scenario Management**: Sorting by scenario name now works correctly in Scenario Management.
* **Cannot Search for % in Queries**: Searching using the "%" character in Queries is now supported.
* **Dashboard Searchbar Text Removal**: Fixed an issue where typed text in the dashboard search bar was removed while dashboards were loading.
* **Report Execution Failure**: Users can now successfully execute reports; previously, reports would erroneously finish in 0 seconds.

### Synthetics <a href="#synthetics" id="synthetics"></a>

#### Bug Fixes

* **Groups Not Visible in Check Analytics**: Resolved the issue where monitor groups were not visible in the Groups View or Manage Groups tab under Check Analytics.

### Flow <a href="#flow" id="flow"></a>

#### Bug Fixes

* **Group Dropdown Empty in Rules**: The group dropdown in the rules tab within Pipelines now displays correctly, allowing selection as expected.
* **Action Button Suggestions**: Hovering over action buttons in Ascent Pipelines now shows a tooltip suggesting the corresponding action, improving user guidance.

### Fleet <a href="#fleet" id="fleet"></a>

#### Bug Fixes

* **Config Files Shown as New**: Config files assigned to an agent no longer incorrectly show as "new" after assignment.
* **Fleet Agents Page Unnecessary API Calls**: Improved the Fleet Agents page to reduce unnecessary API calls on every keystroke and resolved related issues with the filters API.

### Ascent <a href="#ascent" id="ascent"></a>

#### Bug Fixes

* **Role Deletion not Cleaning Up in Casdoor**: Deleting a role in Ascent now also removes associated user-role and policy mappings in Casdoor as expected.

***

### Component Versions - Ascent v2.11.1

<table><thead><tr><th>Components</th><th width="410">Version</th></tr></thead><tbody><tr><td>Flash</td><td>v3.16.3</td></tr><tr><td>Coffee</td><td>v3.17.7</td></tr><tr><td>ASM</td><td>13.36.3</td></tr><tr><td>NG Private Agent</td><td>1.0.9</td></tr><tr><td>Check Execution Container: Browser</td><td>fpr-c-130n-10.2.1-716-r-2025.04.02-0-base-2.0.0</td></tr><tr><td>Check Execution Container: Zebratester</td><td>zt-7.5a-p0-r-2025.04.02-0-base-1.2.0</td></tr><tr><td>Check Execution Container: Runbin</td><td>runbin-2025.04.17-0-base-2.2.1</td></tr><tr><td>Check Execution Container: Postman</td><td>postman-2025.04.17-0-base-1.4.1</td></tr><tr><td>Bnet (Chrome Version)</td><td>10.2.1 (Chrome 130)</td></tr><tr><td>Zebratester</td><td>7.0B</td></tr><tr><td>ALT</td><td>6.13.3.240</td></tr><tr><td>IronDB</td><td>1.5.0</td></tr></tbody></table>

