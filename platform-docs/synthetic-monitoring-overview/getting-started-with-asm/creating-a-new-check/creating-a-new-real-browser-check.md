# Creating a New Real Browser Check

To begin, click on any of the icons within the “Real Browser Checks” section of the “Create New Check” wizard.

## Step 1: Name, Description, and Tags <a href="#creatinganewrealbrowsercheck-step1-name-description-andtags" id="creatinganewrealbrowsercheck-step1-name-description-andtags"></a>



Fill in the name of the check and a brief description if desired. Then add any Tags you wish to associate with the checks.

## Step 2: URL, Scenario, and Location <a href="#creatinganewrealbrowsercheck-step2-url-scenario-andlocation" id="creatinganewrealbrowsercheck-step2-url-scenario-andlocation"></a>



| **Item**        | **Description**                       | **Comment**                                                                                     |
| --------------- | ------------------------------------- | ----------------------------------------------------------------------------------------------- |
| URL             | URL to access.                        |                                                                                                 |
| Browser Version | Browser version to use for the check. | Depending on the version, additional options may be available.                                  |
| Scenario        | Scenario file.                        |                                                                                                 |
| Location        | Locations for the check.              | **Note:** If you select multiple locations, a separate check will be created for each location. |

**Buttons**

| **Item**    | **Description**       |
| ----------- | --------------------- |
| Add         | Add.                  |
| Debug       | Debug .               |
| Edit Script | Edit the script file. |

## Step 3: Interval, Thresholds & Monitor Groups <a href="#creatinganewrealbrowsercheck-step3-interval-thresholds-and-monitorgroups" id="creatinganewrealbrowsercheck-step3-interval-thresholds-and-monitorgroups"></a>

In the third step, you can define how often the check is to run, basic reporting settings and add administrative settings.



**Frequency**

| **Item**  | **Description**              | **Comment**                                           |
| --------- | ---------------------------- | ----------------------------------------------------- |
| Frequency | Time between data retrieval. |  If set to `manual`, the check is only run on demand. |

**Thresholds**

| **Item**                       | **Description**                                                            | **Comment**                                  |
| ------------------------------ | -------------------------------------------------------------------------- | -------------------------------------------- |
| High Warning Threshold         | Severity level Threshold calculation method and settings.                  | A warning is triggered **above** this value. |
| High Error Threshold           | Severity level Threshold calculation method and settings.                  | Error is triggered **above** this value.     |
| Low Warning Threshold          | Severity level Threshold calculation method and settings.                  | A warning is triggered **below** this value. |
| Low Error Threshold            | Severity level Threshold calculation method and settings.                  | Error is triggered **below** this value.     |
| Treat 3rd party URL as Warning | Errors generated by third party URLs are handled as Severity level events. |                                              |

**Groups**

| **Item**       | **Description**               | **Comment** |
| -------------- | ----------------------------- | ----------- |
| Monitor Groups | Monitor Groups for the check. |             |

## Step 4: Confirm & Create <a href="#creatinganewrealbrowsercheck-step4-confirm-and-create" id="creatinganewrealbrowsercheck-step4-confirm-and-create"></a>

The final step provides an overview of the check configuration and allows you to create it.



* Click **Create** to add the check and open the Configuration view.
