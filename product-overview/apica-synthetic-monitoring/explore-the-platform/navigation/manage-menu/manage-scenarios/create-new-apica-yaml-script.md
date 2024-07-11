# Create New Apica YAML Script

It is possible to create ZebraTester scripts directly from the ASM UI by utilizing a tool known as “ApicaYAML”. ApicaYAML is a tool which works on the Apica backend to convert a user-created YAML script into a ZebraTester script without the need for a GUI-based scripting tool. This article will focus on how to use the ASM-based editor to quickly create and deploy ZebraTester scripts; refer to [Apica YAML](https://apica-kb.atlassian.net/wiki/spaces/DAZT/pages/2151055361) for core documentation on the tool itself.

Wondering whether to use the traditional ZebraTester GUI or Apica YAML to create your script? Compare the two tools[ here](https://apica-kb.atlassian.net/wiki/spaces/DAZT/pages/2151055361/Apica+YAML#Comparing-ZebraTester-to-ApicaYAML).

To access the ApicaYAML editor, navigate to the [Manage Scenarios page](https://wpm.apicasystem.com/ManageScenarios) and click the “Create New YAML Script” button:

<figure><img src="../../../../../.gitbook/assets/image (20).png" alt=""><figcaption></figcaption></figure>

In the “Create New Scenario” box which pops up, enter the desired name of the script and click “Save”:

![](<../../../../../.gitbook/assets/image (21).png>)

When the scenario has been named and saved, you will see another dialog box, which will ask whether you would like to edit the Scenario:

![](<../../../../../.gitbook/assets/image (22).png>)

If you click “Cancel”, the scenario will be saved and will be able to be edited later from the Manage Scenarios page. If you click “OK”, you will be taken to the “Edit Yaml Script” screen:

<figure><img src="../../../../../.gitbook/assets/image (23).png" alt=""><figcaption></figcaption></figure>

Within this page, you will be presented with a code editor which you can use to create your script. When you are finished with your script, press the “Save” button to save the script. You can also compile the script directly into a ZebraTester script by pressing the “Compile” button:

<figure><img src="../../../../../.gitbook/assets/image (24).png" alt=""><figcaption></figcaption></figure>

When you press the “Compile Yaml” button, the YAML you have written using the [ApicaYAML syntax](https://apica-kb.atlassian.net/wiki/spaces/DAZT/pages/2123300865/Scripting+with+Apica+YAML+-+Syntax+Usage) will be compiled into a ZebraTester script. You can then create a ZebraTester check with this script.
