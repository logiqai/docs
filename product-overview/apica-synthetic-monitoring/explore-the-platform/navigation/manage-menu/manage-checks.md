# Manage Checks

It is possible to work with multiple checks at once from the Manage Checks page.

![](../../../../.gitbook/assets/2159116380.png)

When you click on the “Manage > Checks” button from the top-level ASM menu, you will be brought to the Manage Checks page:



From here, you will be able to perform helpful tasks such as enabling/disabling, editing, or deleting checks with the click of a button; editing multiple checks at once via the Bulk Edit function; adding/removing users to check groups; and changing group assignment of multiple checks at once.

The following diagram and table provide an overview of the available functions within the Manage Checks page:



| **Icon** | **Name**      | **Description**                                                                                       |
| -------- | ------------- | ----------------------------------------------------------------------------------------------------- |
|          | Edit          | [Edit the check](https://apica-kb.atlassian.net/wiki/spaces/ASMDOCS/pages/2148991311/Editing+Checks). |
|          | Run           | Run the check.                                                                                        |
|          | Delete        | Completely remove the check from ASM.                                                                 |
|          | Toggle select | Select/deselect checks/groups/subgroups.                                                              |

## Assign Checks <a href="#managechecks-assignchecks" id="managechecks-assignchecks"></a>

Selected checks can be associated with a group or subgroup from the **Assign** dialog.



Checks associated with the group are shown on the left. On the right, checks not associated with the group are displayed. The list can be filtered using free text searches and the **Filter** button. You can move checks between the lists with the **Add** and **Remove** transfer buttons. You can rearrange the order of checks in the group with the **Up** and **Down** buttons.

### Assign Check To Group <a href="#managechecks-assignchecktogroup" id="managechecks-assignchecktogroup"></a>

To associate a check with a group, start in the **Manage check** view:



* Use the Checks Filter to find the group
* Click the **Assign Checks** button

The dialog opens:



* Enter a search text in the filter box
* Click the **Filter** button

Checks matching the search texts are displayed:



* Mark the Checks to associate



* Click **Add** to move the check



* Click **Save**

The Check will be included in the group.



## Bulk Edit <a href="#managechecks-bulkedit" id="managechecks-bulkedit"></a>

If you want to edit the common aspects of multiple checks at the same time, you can use the **Bulk Edit** feature.



Whenever you select more than one check in the Manage Checks view, a bulk action toolbar becomes available at the top of the window:

![](../../../../.gitbook/assets/2168160267.png)

| **Action**              | **Description**                          |
| ----------------------- | ---------------------------------------- |
| **Checks View**         | Switch to the normal Manage Checks view. |
| **Bulk Edit**           | Switch to bulk edit mode.                |
| **Disable**             |  Disable the selected checks.            |
| **Enable**              | Enable the selected checks.              |
| **Run**                 | Run the selected checks.                 |
| **Delete**              | Remove all the selected checks.          |
| **Deselect All Checks** | Deselect all selected checks.            |

You can perform Bulk Edit on up to 100 checks at a time. You can't Bulk Edit Integration Checks and other Check Types at the same time.

To edit parameters for the selected checks:

* Mark the parameter by checking the checkbox on the left

The row is indicated in green and the fields become editable.



A running tally of the marked parameters is shown at the top of the window:

![](../../../../.gitbook/assets/2169372673.png)

#### Merge Or Replace <a href="#managechecks-mergeorreplace" id="managechecks-mergeorreplace"></a>

For appropriate fields, you can choose to **merge** the data in the fields or **replace** the date with new values.

![](../../../../.gitbook/assets/2169405441.png)

| **Option** | **Effect**                                                                                                           |
| ---------- | -------------------------------------------------------------------------------------------------------------------- |
| Merge      | All values from all checks will be applied to the selected checks in the bulk action.                                |
| Replace    | Remove the current value for the field and replace it with the new value for the selected checks in the bulk action. |

If the selected checks are of different check types, only those parameters that are in common for all the checks will be editable.

## Filter Checks <a href="#managechecks-filterchecks" id="managechecks-filterchecks"></a>

At the top of the view, filters are available to filter out checks by **Name**, **Check type**, **Location**, **Group**, **Tag** and **State**.



| Item              | Description                                  |
| ----------------- | -------------------------------------------- |
| Search            |  Name of check to search for (free text).    |
| Check Type        |  Type of check.                              |
| Location          |  Location used by the check.                 |
| Group             |  Associated group (hierachical quicksearch). |
| Tag               | Tags used by the check.                      |
| Hide Empty Groups | Hide groups containing no checks.            |

## Managing Monitor Groups <a href="#managechecks-managingmonitorgroups" id="managechecks-managingmonitorgroups"></a>

The **Manage Checks** view contains actions to manage **Monitor Groups** for your account.



Buttons to perform group actions are available both at the top left and top right:



| Icon                                            | Button                  | Description                               |
| ----------------------------------------------- | ----------------------- | ----------------------------------------- |
|                                                 | **Add Top Level Group** | Create a Top Level group.                 |
|                                                 | **Add Subgroup**        | Add Subgroup to the Top Level group.      |
|                                                 | **Rename**              | Change name of group.                     |
|                                                 | **Assign Users**        | Add/remove users from the group.          |
| ![](../../../../.gitbook/assets/2168127515.png) | **Delete Group**        | Remove the group.                         |
|                                                 | **Toggle select**       | Select/deselect all checks and subgroups. |

Checks that are not explicitly assigned to any other group are collected in the **Ungrouped Checks** group.



The **ungrouped checks** group can be expanded to show its contents with the **Expand** button. To collapse the group again, use the **Collapse** button.

## Check Information <a href="#managechecks-checkinformation" id="managechecks-checkinformation"></a>

For each check in the list, information about the check is displayed, with action buttons at the end.



#### Legend <a href="#managechecks-legend" id="managechecks-legend"></a>

| **Column**              | **Description**                                                                                                                                                                 |
| ----------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Select                  | Toggle to Select/deselect check.                                                                                                                                                |
| Run                     | Run the selected check(s).                                                                                                                                                      |
| Check Type & Version    | Check type icon (and the version where applicable).                                                                                                                             |
| Check Name, Link & Tags | Name of the check (the link opens the [Edit Checks](https://apica-kb.atlassian.net/wiki/spaces/ASMDOCS/pages/2148991311/Editing+Checks) view), hover over to see assigned tags. |
| Check Location          | Country flag of the Agent Location with country and city.                                                                                                                       |
| Interval                | Frequency of check runs.                                                                                                                                                        |
| Severity Thresholds     | Settings for the severity.                                                                                                                                                      |
| Status                  | Indicates if the check is `Enabled` or `Disabled`.                                                                                                                              |
| Edit                    | Opens the [Edit Checks](https://apica-kb.atlassian.net/wiki/spaces/ASMDOCS/pages/2148991311/Editing+Checks) view.                                                               |
| Delete                  | Remove the check.                                                                                                                                                               |

## Assign Users <a href="#managechecks-assignusers" id="managechecks-assignusers"></a>

A group can have users associated with it to provide explicit access through the **Assign Users** dialog.



Marked users are SSO users assigned through your SSO settings. Read more about assigning monitor groups through SSO [here](https://apica-kb.atlassian.net/wiki/spaces/ASMDOCS/pages/2150498502/Configuring+SSO+Within+ASM#Step-2%3A-Configure-ASM-to-Utilize-SSO).

Users associated with the group are shown on the left.

On the right, users not associated with the group are displayed.

You can move users between the lists with the **Add** and **Remove** transfer buttons.

**Assign a User To a Group**

To associate a user with a group, start in the **Manage Checks** view:



* Find the desired group
* Click the **Assign Users** button

The dialog opens:



* Mark the users to associate by checking the boxes



* Click **Add** to move the user to the group



* Click **Save**

The users are associated with the group.
