# ASM Platform Overview

## ASM Portal <a href="#asmplatformoverview-asmportal" id="asmplatformoverview-asmportal"></a>

The following video serves as an excellent reference for users who are new to the ASM portal.

Intro to ASM.webm

## ASM Portal Navigation <a href="#asmplatformoverview-asmportalnavigation" id="asmplatformoverview-asmportalnavigation"></a>

Below is an overview of the ASM platform navigation. It allows users to easily find all of the features offered within ASM. This article provides an overview of the different pages which can be accessed from the top navigation bar.



Clicking on the ASM image to the left of the Overview menu item will always bring you back to the main Dashboard.

## Overview <a href="#asmplatformoverview-overview" id="asmplatformoverview-overview"></a>



### Dashboard <a href="#asmplatformoverview-dashboard" id="asmplatformoverview-dashboard"></a>

See [Dashboards](https://apica-kb.atlassian.net/wiki/spaces/ASMDOCS/pages/2132246613/Dashboards) for more information.

### Apica Panels <a href="#asmplatformoverview-apicapanels" id="asmplatformoverview-apicapanels"></a>

The “Apica Panels” menu item allows users to view their configured Apica Panels instances. Apica Panels is a feature which allows users to integrate Apica data into Grafana dashboards for easier viewing; see [Using the Apica Panels Dashboards](https://apica-kb.atlassian.net/wiki/spaces/ASMDOCS/pages/2133754653/Using+the+Apica+Panels+Dashboards) for a complete overview of the feature. The “Apica Panels” menu item contains two sub-items: “Panels” and “About”.



#### Panels <a href="#asmplatformoverview-panels" id="asmplatformoverview-panels"></a>

Clicking the “Panels” link will bring you to the Panels page, on which you can see a high level overview of your Panels dashboards and open or delete an individual Panels dashboard.



The default Panels version available in the ASM SaaS portal is called “Apica Panels (v2)”. There are two major versions of Apica Panels; one version is based on Grafana version 4, and the other (Panels v2) is based on Grafana version 8. Apica Panels (v1) is only available to customers who had ASM Panels enabled before the major version change and have a need to maintain their older dashboards.



If you do not see “Apica Panels (v1)” on your dashboard, it means you do not have legacy Apica Panels configured on your account. Proceed with using only Panels v2 panels.

#### About (Apica Panels) <a href="#asmplatformoverview-about-apicapanels" id="asmplatformoverview-about-apicapanels"></a>

Clicking on the “About” sub-menu item will bring you to the “About” page, which provides a high-level overview of the Apica Panels feature.



## Tools <a href="#asmplatformoverview-tools" id="asmplatformoverview-tools"></a>

The **Tools** section provides access to a number of different system features, such as Impersonate, API settings, Maintenance, Journal, Trace Route, and Messages.

**Menu**



## Impersonate <a href="#asmplatformoverview-impersonate" id="asmplatformoverview-impersonate"></a>

With the **Impersonate** tool you can view Synthetic Monitoring from a different user's perspective. This feature can be very useful for troubleshooting or assisting your users with any problem they may encounter.



| Item          | Description                                |
| ------------- | ------------------------------------------ |
| Filter        | Search for user accounts by name.          |
| Customer      | Customer the user account belongs to.      |
| User Name     | Account user name.                         |
| Roles         | List of roles associated with the account. |
| Last Activity | Clear the settings.                        |
|               | Switch from current user and impersonate.  |

### Start Impersonation <a href="#asmplatformoverview-startimpersonation" id="asmplatformoverview-startimpersonation"></a>

The **Impersonate** tool allows Admin users to use Synthetic Monitoring with the permissions and settings of another user.

**Impersonate User**

To impersonate a user:

* Open the **Tools** menu



* Click **Impersonate**



* Use the **Filter** to search for users
* Find the user in the table
* Click **Impersonate**

### Drop Impersonation <a href="#asmplatformoverview-dropimpersonation" id="asmplatformoverview-dropimpersonation"></a>

When you want to stop impersonating, you can drop the impersonation without logging out and in again.



**Drop Impersonation**

To stop impersonating a user:

* Open the **User** menu
* Click **Drop Impersonation**

The user context is switched back to the original one.



## Maintenance <a href="#asmplatformoverview-maintenance" id="asmplatformoverview-maintenance"></a>

The **Maintenance** view lets you modify or delete result records for individual checks and recalculate any associated consolidation records. The table shows a list of previous maintenance tasks and information about them:



| Button          | Description                          |
| --------------- | ------------------------------------ |
| Show entries    | Number of rows to display per page.  |
| Refresh History | Reload and update the table display. |

| Column  | Description                                        |
| ------- | -------------------------------------------------- |
| Created | Timestamp for when the task was created.           |
| Action  | Action(s) performed by the task.                   |
| Status  | The task status (`running`/`success`/`cancelled`). |
| Records | Number of items affected by the task.              |

### Maintenance Tasks <a href="#asmplatformoverview-maintenancetasks" id="asmplatformoverview-maintenancetasks"></a>

Maintenance tasks can be created by selecting relevant checks and applying the appropriate action.



### Apply Action <a href="#asmplatformoverview-applyaction" id="asmplatformoverview-applyaction"></a>



The **apply action** section lets you select what action to apply to the selected checks and queue the task for processing.

| Option            | Description                                      |
| ----------------- | ------------------------------------------------ |
| Update            | Change the Check Result Status to this severity. |
| Set Value to NULL | Exclude the check from all calculations.         |
| Delete            | Remove the results.                              |

Press **Process Selected Records** to remove the results.

### Selector View <a href="#asmplatformoverview-selectorview" id="asmplatformoverview-selectorview"></a>



The **selectors** allow you to pick which checks to include in the task.

| Item            | Description                                                |
| --------------- | ---------------------------------------------------------- |
| Type            | List of check types.                                       |
| Checks          | List of checks of the selected type.                       |
|                 | Check result Colors to include.                            |
| From            | Start date and time for the period.                        |
| To              | End date and time for the period.                          |
| Refresh         | Reload and update the table display according to settings. |
| Display records | The number of rows to display per page.                    |
| Search          | Search for checks by message text.                         |

### Create A Maintenance Task <a href="#asmplatformoverview-createamaintenancetask" id="asmplatformoverview-createamaintenancetask"></a>

Maintenance tasks can be created by selecting relevant checks and applying the appropriate action.



To create a maintenance task:

1. Select the check results you want to modify:
2. Type from the list
3. Check from the list
4. Pick a period:
5. Enter a **From** date and time
6. Enter a **To** date and time
7. Search for strings in message texts, if needed
8. Click **Refresh**
9. Click **Process Selected Records**

A database task is placed in a queue for execution. It will run as soon as possible.

When queued, the maintenance task is visible in the Task table.

### Table <a href="#asmplatformoverview-table" id="asmplatformoverview-table"></a>



The **table** shows the result of applying the selectors.

**NOTE:** The action in the task will apply to all selected checks. Make sure you have selected the correct checks before clicking the button.

| Column   | Description                                                        |
| -------- | ------------------------------------------------------------------ |
| Severity | Check result status severity.                                      |
| Time     | Timestamp for the check run.                                       |
| Value    | Duration                                                           |
| Message  | The result message. (Clicking this will show the browser results). |
| Attempts | Number of attempts for the check run.                              |

## Journal <a href="#asmplatformoverview-journal" id="asmplatformoverview-journal"></a>

The **Journal** keeps a record of all user actions taken in the system.



### Selectors <a href="#asmplatformoverview-selectors" id="asmplatformoverview-selectors"></a>

The journal can be filtered by a number of parameters.



| **Item**     | **Description**                                            |
| ------------ | ---------------------------------------------------------- |
| Severity     | Event Severity to include.                                 |
| From         | Start date and time for the period.                        |
| To           | End date and time for the period.                          |
|  Message     | Event description.                                         |
|  Customer    | Customer account.                                          |
|  User        | Involved user, if any.                                     |
|  IP-Address  | The associated IP address for the event, if any.           |
|  Source      | Originating location.                                      |
|  Category    | Event Categories.                                          |
|  Check       | Involved check, if any.                                    |
| Apply Filter | Reload and update the table display according to settings. |

### Entries <a href="#asmplatformoverview-entries" id="asmplatformoverview-entries"></a>

The **Entries** table shows the result of applying the selectors.



| **Column**  | **Description**                                  |
| ----------- | ------------------------------------------------ |
| Severity    | Event Severity.                                  |
|  Timestamp  | Date and time when the event occurred.           |
|  Message    | Event description.                               |
|  Customer   | Customer account.                                |
|  User       | Involved user, if any.                           |
|  IP-Address | The associated IP address for the event, if any. |
|  Source     | Originating location.                            |
|  Category   | Event Categories.                                |
|  Check      | Involved check, if any.                          |

## Traceroute <a href="#asmplatformoverview-traceroute" id="asmplatformoverview-traceroute"></a>

The Traceroute tool allows you to easily run a Traceroute from any of our Apica [Locations](https://apica-kb.atlassian.net/wiki/pages/createpage.action?spaceKey=ASMDOCS\&title=Locations%20Locations\&linkCreation=true\&fromPageId=2134049566) to any URL or IP address you choose.



### Introduction <a href="#asmplatformoverview-introduction" id="asmplatformoverview-introduction"></a>

The purpose of running a traceroute is to get an indication of which way traffic takes between a source and a destination. Traceroute sends test Packet with TTL values starting at 1. The resulting [ICMP](https://apica-kb.atlassian.net/wiki/spaces/GLOS/pages/4632057/Icmp) `Time Exceeded` messages are used to discover any devices (called "hops") forwarding the packets to the destination. For each hop, the response time is recorded to indicate transmission speed. Any detected failures or packet losses on the way are also the recorder and displayed to give an idea of the transmission quality.

### Configuration <a href="#asmplatformoverview-configuration" id="asmplatformoverview-configuration"></a>

The Traceroute tool configuration is fairly simple.



| Item        | Description                                                                                                                                                                                                |
| ----------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Host        | Target destination.                                                                                                                                                                                        |
| Location    | Apica [Locations Locations](https://apica-kb.atlassian.net/wiki/pages/createpage.action?spaceKey=ASMDOCS\&title=Locations%20Locations\&linkCreation=true\&fromPageId=2134049608) to use as starting point. |
| **Execute** | Perform traceroute.                                                                                                                                                                                        |

These Tracroute settings are used by default and are not configurable:

| Option                  | Value      |   |
| ----------------------- | ---------- | - |
|  Maximum number of hops |  30        |   |
| Wait timeout per hop    | 5 seconds  |   |
| Job execution timeout   | 60 seconds |   |

### Traceroute Results <a href="#asmplatformoverview-tracerouteresults" id="asmplatformoverview-tracerouteresults"></a>

The results of the traceroute run is shown in the results frame.



The first line shows information about the traceroute configuration:

Hostname and IP address, the upper limit on hops to try, and size of the test packets.

On each subsequent row, information about each hop is shown:

Hop Number, hostname and/or IP address for the hop, and ther response times for each of the three test packets.

## Messages <a href="#asmplatformoverview-messages" id="asmplatformoverview-messages"></a>

The **Messages** view lets you configure system messages to display to Synthetic Monitoring users.

**View**



| Item                  | Description                                 |
| --------------------- | ------------------------------------------- |
| Importance            | Message importance (and display color).     |
| Message               | Message to display                          |
| Customer              | Customer to display the message to.         |
| Include Sub-customers | Also display message to sub-customers.      |
| Active Time Period    | Period during which to display the message. |
| Activity              | Turn message on or off.                     |

**Configuration**



| Item                  | Description                                 |
| --------------------- | ------------------------------------------- |
| Message               | Message to display                          |
| Message is From       | Sender to display                           |
| Active Time Period    | Period during which to display the message. |
| Importance            | Message importance (and display color).     |
| Enabled               | Turn message on or off.                     |
| Customer              | Customer to display the message to.         |
| Include Sub-customers | Also display message to sub-customers.      |
| **Test**              | Preview the message.                        |
| **Cancel**            | Close dialog.                               |
| **Save**              | Save the message.                           |

**Formatting**

The message can contain some formatting. You format the text by putting the text within .

| Formatting       | Tag                                | Preview                      |
| ---------------- | ---------------------------------- | ---------------------------- |
| Link:            | `[link="linkurl"]Link Text[/link]` | Link Text                    |
| Bold:            | \[`b]Bold Text[/b]`                | **Bold Text**                |
| Italic:          | `[i]Italic Text[/i]`               | **Italic Text**              |
| Bold and Italic: | `[ib]Italic and Bold Text[/ib]`    | \***Italic and Bold Text**\* |

### Create Message <a href="#asmplatformoverview-createmessage" id="asmplatformoverview-createmessage"></a>

Messages can be added from the **Messages** view.

**Add New Message**

* Click the **Add New Message** button

The **Add New Messages** dialog is shown

**Configuration**



| Item                  | Description                                 |
| --------------------- | ------------------------------------------- |
| Message               | Message to display                          |
| Message is From       | Sender to display                           |
| Active Time Period    | Period during which to display the message. |
| Importance            | Message importance (and display color).     |
| Enabled               | Turn message on or off.                     |
| Customer              | Customer to display the message to.         |
| Include Sub-customers | Also display message to sub-customers.      |
| **Test**              | Preview the message.                        |
| **Cancel**            | Close dialog.                               |
| **Save**              | Save the message.                           |

**Formatting**

The message can contain some formatting. You format the text by putting the text within .

| Formatting       | Tag                                                                                                                                                                  | Preview                                                                              |
| ---------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------ |
| Link:            | `link="linkurl"Link Text[/link]`                                                                                                                                     | [Link Text](https://apica-kb.atlassian.net/wiki/spaces/AM/pages/2134049652/Messages) |
| Bold:            | `[b]Bold Text[/b]`                                                                                                                                                   | **Bold Text**                                                                        |
| Italic:          | `[i]Italic Text[/i]`                                                                                                                                                 | _Italic Text_                                                                        |
| Bold and Italic: | `[ib]Italic and Bold Text`[/ib](https://apica-kb.atlassian.net/wiki/pages/createpage.action?spaceKey=ASMDOCS\&title=%2Fib\&linkCreation=true\&fromPageId=2134049680) | \***Italic and Bold Text**\*                                                         |

## Filter Checks <a href="#asmplatformoverview-filterchecks" id="asmplatformoverview-filterchecks"></a>

All checks in all monitor groups can be filtered by using the filter buttons.

### Filter Checks By Status <a href="#asmplatformoverview-filterchecksbystatus" id="asmplatformoverview-filterchecksbystatus"></a>

To filter out all checks with a particular status:



* Click the color button in the menu bar for each status type you want to view

The button is highlighted, and only checks matching the status are shown in the dashboard.



* Click the same color(s) again to disable the filter



## Log In <a href="#asmplatformoverview-login" id="asmplatformoverview-login"></a>

Synthetic Monitoring is accessed through a web-based control panel, using basic authentication.

**How to log in**

To log in to Synthetic Monitoring:

* Obtain your user and password from your system administrator
* Open the [Apica Synthetic Portal](http://wpm.apicasystem.com/) in your browser:

The login dialog is displayed:



* Enter your **username** and **password**
* Click **Log In**

When you have been logged in, the Overview Dashboard will be displayed.

The first time you log in (before creating checks), this view may be mostly empty.

## Remember Me <a href="#asmplatformoverview-rememberme" id="asmplatformoverview-rememberme"></a>

You can have the browser remember your credentials, so you won't have to type them each time you log in.&#x20;

\##

To cache your username and password in the browser:



* Click the **Remember Me** checkbox

## Reset Password <a href="#asmplatformoverview-resetpassword" id="asmplatformoverview-resetpassword"></a>

In case you forget your password, you can reset it from the login dialog.

\##



To reset the password:

* Click the **Forgot Your Password** link

A dialog opens:



* Enter your **User Name**
* Click **Continue**

An email is sent to the address registered for your account.



## Apica Password and Login Policy <a href="#asmplatformoverview-apicapasswordandloginpolicy" id="asmplatformoverview-apicapasswordandloginpolicy"></a>

Apica Synthetic Monitoring Portal logins will enforce the following minimum password requirements, in line with Apica security policy password and account security.

### Password Requirements <a href="#asmplatformoverview-passwordrequirements" id="asmplatformoverview-passwordrequirements"></a>

* Passwords will have a minimum length of 12 alphanumeric characters and must contain a mix of lower, upper, number, and special characters.
* A User will be Locked out after 5 failed login attempts and will need to be unlocked by a user with a user or customer administrator role.
* Users may reset their passwords as needed. Apica will provide a reset link via email. That emailed link will be valid for 1-hour.

***

The features below are Opt-In and need to be activated in coordination with Apica Support.

### Password Expiration <a href="#asmplatformoverview-passwordexpiration" id="asmplatformoverview-passwordexpiration"></a>

* After 90 days, a password will expire and need to be changed.
  * &#x20;Warnings will be sent to the user email 7 days before and on the day of password expiration to allow the password to be reset before it expires.
* Reset an expired password via the login page or contacting a User or Customer-level administrator.

### Inactive Logins <a href="#asmplatformoverview-inactivelogins" id="asmplatformoverview-inactivelogins"></a>

* After 90 days of user inactivity, Apica will consider the user account inactive and will deactivate that account.
  * &#x20;Warnings will be sent to the user email 7 days before expiration and on the expiration day.
* User or Customer level Administrators can activate a deactivated account to allow the user to log in again.

For more information, contact [support@apica.io](mailto:support@apica.io).

## New Integration + <a href="#asmplatformoverview-newintegration" id="asmplatformoverview-newintegration"></a>

New integration checks are created from the **New Integration +** menu.

**Menu**



* Click **New Integration +**



* Select a Check type to create by clicking on the icon.

The **New Integration** wizard is shown.

## New Integration Configuration <a href="#asmplatformoverview-newintegrationconfiguration" id="asmplatformoverview-newintegrationconfiguration"></a>

#### Configuration <a href="#asmplatformoverview-configuration.3" id="asmplatformoverview-configuration.3"></a>

After the **New Integration** wizard has been completed, the finished check is opened in edit mode.

\##

In the edit view, you can set further configuration options for the check.

The exact options available vary with integration type.



## New Integration Creation Wizard <a href="#asmplatformoverview-newintegrationcreationwizard" id="asmplatformoverview-newintegrationcreationwizard"></a>

All integration check types can be created through the **New Integration** wizard. The details vary with integration type, but the general principles are the same for all of them.

## Create Wizard: Step 1 Information <a href="#asmplatformoverview-createwizard-step1information" id="asmplatformoverview-createwizard-step1information"></a>

In the first step, you can name the check and add a description.

\##



## Create Wizard: Step 2 Specifics <a href="#asmplatformoverview-createwizard-step2specifics" id="asmplatformoverview-createwizard-step2specifics"></a>

In the second step, you provide

* integration information,
* metric settings,
* Locations - Introduction, and
* other integration-specific settings.

\##



## Create Wizard: Step 3 Options <a href="#asmplatformoverview-createwizard-step3options" id="asmplatformoverview-createwizard-step3options"></a>

#### Step 3: Options <a href="#asmplatformoverview-step3-options" id="asmplatformoverview-step3-options"></a>

In the third step you can configure

* how often the check is to run,
* set threshold values for check notifications, and
* add it to one or more [Monitor Groups](https://apica-kb.atlassian.net/wiki/pages/createpage.action?spaceKey=ASMDOCS\&title=Monitor%20Groups\&linkCreation=true\&fromPageId=2134868148).

\##



## Step 4: Confirmation <a href="#asmplatformoverview-step4-confirmation" id="asmplatformoverview-step4-confirmation"></a>

The final step shows all configurations made, and allows you to go back to revise the check or move forward and create it.

\##



## Status Filter <a href="#asmplatformoverview-statusfilter" id="asmplatformoverview-statusfilter"></a>

To the right of the navigation bar, there is a color coded status summary of all the checks associated with your user account.

**Menu**



The numbers in the colored boxes indicate the number of checks with that status.

#### [Colors](http://confluence.teamsinspace.com:8090/display/ASMDOCS/Colors) <a href="#asmplatformoverview-colors" id="asmplatformoverview-colors"></a>

Check Status is represented by four colors:

| Color                                    | Description |
| ---------------------------------------- | ----------- |
|  Green                                   | Information |
| Yellow                                   | Warning     |
| Orange                                   | Error       |
| Red                                      | Fatal       |

The colors are used in any context where the check status is displayed.

## Filter Checks <a href="#asmplatformoverview-filterchecks.1" id="asmplatformoverview-filterchecks.1"></a>

All checks in all monitor groups can be filtered by using the filter buttons.

**Filter Checks By Status**

To filter out all checks with a particular status:



* Click the color button in the menu bar for each status type you want to view

The button is highlighted, and only checks matching the status are shown in the dashboard.



* Click the same color(s) again to disable the filter

