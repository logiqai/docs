# How to Handle HTML Windows in ASM Scenarios

## Using selectWindow in ASM <a href="#howtohandlehtmlwindowsinasmscenarios-usingselectwindowinasm" id="howtohandlehtmlwindowsinasmscenarios-usingselectwindowinasm"></a>

Selenium IDE classic (2.9.1) and Selenium IDE TNG (3.0+) handle windows differently. So, if you use the newer Selenium version available for Chrome, you'll need to edit your selectWindow commands manually.

* Selenium IDE v3+ uses handlers to check which tabs it’s on.
* In the classic version of Selenium, you select the windows with the page title or store the URL of the window.
  * Selenium Classic can’t select windows that itself didn’t open. So windows that a script opened itself, for example, can’t be found. While this is rare, that might explain why you can’t select those windows.

### Selecting Windows with Titles <a href="#howtohandlehtmlwindowsinasmscenarios-selectingwindowswithtitles" id="howtohandlehtmlwindowsinasmscenarios-selectingwindowswithtitles"></a>

| **Step**                                                                                                                                                                                                                                                                                                 | **Screenshot**                                                                                                                                                                       |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| <ul><li>Create a script that opens a window.</li><li>Grab the name of the newly opened window by inspecting the page source:</li></ul>                                                                                                                                                                   | ![](../../../.gitbook/assets/1347682330.png)                                                                                                                                         |
| <ul><li>Add a pause before selecting the window to make sure it’s actually loaded in the correct title. There’s currently no way to wait for a window to finish loading before selecting it.</li><li>Add a selectWindow with a target of the title of the page as the following picture shows:</li></ul> | <p><img src="../../../.gitbook/assets/1347059785.png" alt=""></p><ul><li>To deselect the current window, repeat the above steps for the new/old window you want to select.</li></ul> |

### Selecting Windows with href Storing <a href="#howtohandlehtmlwindowsinasmscenarios-selectingwindowswithhrefstoring" id="howtohandlehtmlwindowsinasmscenarios-selectingwindowswithhrefstoring"></a>

| **Step**                                                                                                                                                                                                                                                                                  | **Screenshot**                                                                                                                                                                                                                                                                                                                                                                                                                          |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <ul><li>Go to the page with a window and make sure it also has an href attached to it with a URL.</li><li><p>Write the command “storeAttribute | target@href | test.”</p><ul><li>Where “target” is whatever the target is for the field/button that opens the window.</li></ul></li></ul> | <p><img src="../../../.gitbook/assets/1347682337.png" alt=""></p><p>To use this stored data, all you need to do is write the command <code>open | ${test}</code>. The window will be opened in the current tab you are in, meaning you don’t need to switch between tabs.</p><ul><li>Do keep in mind, though, that you’re unable to go back to the previous site unless you store the previous address to a variable as well.</li></ul> |

### Selecting Windows with the Same Names <a href="#howtohandlehtmlwindowsinasmscenarios-selectingwindowswiththesamenames" id="howtohandlehtmlwindowsinasmscenarios-selectingwindowswiththesamenames"></a>

| **Step**                                                                                                                                                                  | **Screenshot**                                                                                                                                                                               |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <ul><li>Make sure you’re on the window you want to switch from.</li><li>Write the command “runScript | document.title = “Whatever the new title of the page is”</li></ul> | ![](../../../.gitbook/assets/1347387441.png)                                                                                                                                                 |
| In Step 5 in the above example, I’ve also stored the previous name to prove that it changes the title.                                                                    | <p><img src="../../../.gitbook/assets/1347682345.png" alt=""></p><p>As you can see above from the output log, Step 8 echoes the variable “test,” and step 9 echoes the variable “test1”:</p> |
| <ul><li>Do steps 2-4 of the guide “Selecting Windows with Titles” to select the window you want to select.</li></ul>                                                      |                                                                                                                                                                                              |

&#x20;