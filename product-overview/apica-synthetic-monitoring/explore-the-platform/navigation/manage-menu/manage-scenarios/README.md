# Manage Scenarios

In the **Manage Scenarios** view, You can edit your Selenium IDE scripts directly from the browser and test them to make sure the script is working properly using different locations and browser versions.



The “Download Script Extension” functionality is deprecated and the feature is not maintained.

There are a number of buttons located at the top right of the “Customer’s Scenarios” section:

| Button                                                             | Name       | Description                                                                                         |
| ------------------------------------------------------------------ | ---------- | --------------------------------------------------------------------------------------------------- |
|  **Add Scenario**                                                  | Add        | Add or create a [new scenario](http://academy.apicasystems.com/asmdocs/manage/scenarios/add/start). |
| **Delete Scenarios**                                               | Delete     | Remove all selected scenarios.                                                                      |
| **Checkbox to the right of “Add Scenario” and “Delete Scenarios”** | Toggle all | Select/deselect all scenarios in the list.                                                          |

There are a number of icons located at the top right of an individual scenario:

| Icon | Name          | Description                                                                                                                                   |
| ---- | ------------- | --------------------------------------------------------------------------------------------------------------------------------------------- |
|      | Download      | Save the scenario to local computer.                                                                                                          |
|      | Edit          | Change [settings](https://apica-kb.atlassian.net/wiki/spaces/ASMDOCS/pages/2149023977/Understanding+the+Edit+Scenario+Page) for the scenario. |
|      | Assign        | Create [associations](http://academy.apicasystems.com/asmdocs/manage/scenarios/associate/start) with one or several checks.                   |
|      | Delete        | Remove the scenario.                                                                                                                          |
|      | Toggle select | Select/deselect scenario.                                                                                                                     |

## Add Scenario Dialog <a href="#managescenarios-addscenariodialog" id="managescenarios-addscenariodialog"></a>



| Option      | Description                    |
| ----------- | ------------------------------ |
| Name        | Identifier for the scenario.   |
| Choose File | Remove all selected scenarios. |
| Save        | Save the scenario.             |
| Cancel      | Cancel scenario creation.      |

## Upload To Scenario Manager <a href="#managescenarios-uploadtoscenariomanager" id="managescenarios-uploadtoscenariomanager"></a>

When you have a finished script file on your local computer, you can upload it to the Scenario Manager.

## Upload Script File <a href="#managescenarios-uploadscriptfile" id="managescenarios-uploadscriptfile"></a>

The upload button is on the right hand side of the table.



* Click **Add Scenario**

The **Add Scenario** dialog opens:



* Click **Choose File**



* Browse to the script file you want to use
* Click **Open**

The file is added to the dialog:



The name for the scenario does not have to be the same as the file name.

* Enter a descriptive **Name** for the scenario

**Note:** You will end up having a great number of scenarios, so make sure you have a reasonable naming scheme for your scenarios that suits your organization.



* Click **Save**

A notification is shown:



The scenario is added to the table:



## Associate <a href="#managescenarios-associate" id="managescenarios-associate"></a>

A single scenario can be associated with and used in multiple checks. You can access that list from the **Associated With Checks** link.

### Dialog <a href="#managescenarios-dialog" id="managescenarios-dialog"></a>



Checks using the scenario are shown on the left.

On the right, checks not associated with the scenario are displayed. The list can be filtered using free text searches and the **Filter** button.

You can move checks between the lists with the **Add** and **Remove** transfer buttons.

#### Associate Scenario With Check <a href="#managescenarios-associatescenariowithcheck" id="managescenarios-associatescenariowithcheck"></a>

To associate a check with a scenario, start in the **Manage Scenario** view:



* Click link in the **Associated With Checks**

The dialog opens:



* Enter a search text in the filter box
* Click the **Filter** button

Checks matching the search texts are displayed:



* Mark the Checks to associate



* Click **Add** to move the check



* Click **Save**

The **Associated with Checks** link is updated with the new count.



## Scenarios Filter <a href="#managescenarios-scenariosfilter" id="managescenarios-scenariosfilter"></a>

At the top of the view, a filters are available to filter out scenarios by **Name**, or **Date Created** (or a range of dates).

**View**



| Item         | Description                                  |
| ------------ | -------------------------------------------- |
| Name         |  Name of scenario to search for (free text). |
| Date Created |  Start date for filtering.                   |
| To           |  End date for filtering.                     |
| Rows         |  Number of rows to display.                  |
