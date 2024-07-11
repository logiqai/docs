# Slack (Webhook Integration)

#### Slack Channel Alerts <a href="#slack-webhookintegration-slackchannelalerts" id="slack-webhookintegration-slackchannelalerts"></a>

The Slack integration allows Alerts to be delivered to Slack channels.

**Note:** For Slack delivery to work, you need to configure a [Slack Integration](https://apica-kb.atlassian.net/wiki/spaces/ASMDOCS/pages/4632856/Slack+Integration) custom integration in Slack.

With Slack, you can

* Communicate incident alerts to Slack channels
* Share alert information with single users or other team channels

#### Slack Integration Overview <a href="#slack-webhookintegration-slackintegrationoverview" id="slack-webhookintegration-slackintegrationoverview"></a>

1. [Integrate with Slack](https://apica-kb.atlassian.net/wiki/spaces/ASMDOCS/pages/4632856/Slack+Integration)
2.  [Add Slack Target](https://apica-kb.atlassian.net/wiki/spaces/ASMDOCS/pages/4632848/Add+Slack+Target)



## Part 1: Slack Integration <a href="#slack-webhookintegration-part1-slackintegration" id="slack-webhookintegration-part1-slackintegration"></a>

## Slack Integration <a href="#slack-webhookintegration-slackintegration" id="slack-webhookintegration-slackintegration"></a>

Before you can use Slack as a target for delivery, you need to configure an **incoming WebHook** custom integration in Slack. Please see the Slack Documentation for current Webhook process details:

* [Sending messages using Incoming Webhooks](https://api.slack.com/messaging/webhooks)

## Webhook Settings <a href="#slack-webhookintegration-webhooksettings" id="slack-webhookintegration-webhooksettings"></a>

When you have created the basic WebHook integration, you can further customize the parameters and behavior.



* Change settings as desired

When you are satisfied with the settings:

* Click **Save Settings**

## Setting up Slack from the Slack Platform <a href="#slack-webhookintegration-settingupslackfromtheslackplatform" id="slack-webhookintegration-settingupslackfromtheslackplatform"></a>

This page is a simple copy from the Slack page. For the complete page, please follow the link to the official Slack documentation.

### [Getting started with Incoming Webhooks](https://api.slack.com/messaging/webhooks#getting\_started) <a href="#slack-webhookintegration-gettingstartedwithincomingwebhooks" id="slack-webhookintegration-gettingstartedwithincomingwebhooks"></a>

A quick review of the 4-step process (if you've already done some of these things it'll be even easier) that will have you posting messages using Incoming Webhooks in a few minutes:

#### 1. Create a Slack app (if you don't have one already) <a href="#slack-webhookintegration-1.createaslackapp-ifyoudonthaveonealready" id="slack-webhookintegration-1.createaslackapp-ifyoudonthaveonealready"></a>

#### 2. Enable Incoming Webhooks <a href="#slack-webhookintegration-2.enableincomingwebhooks" id="slack-webhookintegration-2.enableincomingwebhooks"></a>

#### 3. Create an Incoming Webhook <a href="#slack-webhookintegration-3.createanincomingwebhook" id="slack-webhookintegration-3.createanincomingwebhook"></a>

#### 4. Use your Incoming Webhook URL to post a message <a href="#slack-webhookintegration-4.useyourincomingwebhookurltopostamessage" id="slack-webhookintegration-4.useyourincomingwebhookurltopostamessage"></a>

## Part 2: Adding a Slack Target <a href="#slack-webhookintegration-part2-addingaslacktarget" id="slack-webhookintegration-part2-addingaslacktarget"></a>

**Note:** For this **deprecated** method of Slack delivery to work, you must first configure a [Slack Integration](https://apica-kb.atlassian.net/wiki/pages/createpage.action?spaceKey=AM\&title=Part%201%3A%20Slack%20Integration%20%28Webhooks%20Deprecated%29) custom integration in Slack.

## Alerting to a Slack Target <a href="#slack-webhookintegration-alertingtoaslacktarget" id="slack-webhookintegration-alertingtoaslacktarget"></a>

This deprecated Webhook method delivers alerts to a defined Slack integration destination (a Slack Target).



### Creating a Slack Target <a href="#slack-webhookintegration-creatingaslacktarget" id="slack-webhookintegration-creatingaslacktarget"></a>

This is a complete Step-by-Step Guide to Add a Slack Target via Webhooks, which is **deprecated**, per Slack.

| **Step**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        | **Screenshot** |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------- |
| <h3 id="slack-webhookintegration-toaddaslacktarget">To add a Slack target</h3><ul><li>Click the <strong>WebHook</strong> button</li><li>A blank target is created</li><li>Select Slack</li></ul>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |                |
| <h3 id="slack-webhookintegration-targetname">Target Name</h3><ul><li>Enter the target name for identifying the Slack target in ASM.</li></ul><h4 id="slack-webhookintegration-url">URL</h4><ul><li>The integration URL is the access point in Slack for alert delivery. Copy the ID's from the Slack <a href="https://apica-kb.atlassian.net/wiki/spaces/ASMDOCS/pages/4632837/Slack++Settings">Slack Settings</a> and paste them into the textbox.<code>https://hooks.slack.com/services/</code><strong>T00000000/B00000000/XXXXXXXXXXXXXXXXXXXXXXXX</strong></li></ul><h4 id="slack-webhookintegration-channel">Channel</h4><ul><li>The channel setting defines the channel (or user) in Slack where the alerts are delivered.</li><li>Enter the <strong>Channel</strong> (or user) name</li></ul><p><strong>Note:</strong> The <strong>channel name</strong> must be preceded by the # character.</p><p><strong>Note:</strong> The <strong>user name</strong> must be preceded by the @ character.</p><h4 id="slack-webhookintegration-messagetitleandmessage">Message Title and Message</h4><ul><li>Enter the Title of the Message and the Message itself. You can use <a href="https://apica-kb.atlassian.net/wiki/pages/createpage.action?spaceKey=AM&#x26;title=New%3A%20Message%20Placeholders">Alerts Message Placeholders</a> in the title to add dynamic information. The delivered alert message can use all formatting provided by Slack, <em>and</em> placeholders for ASM information. For more details about Slack formatting, see the Slack documentation: <a href="https://api.slack.com/docs/message-formatting">https://api.slack.com/docs/message-formatting</a></li></ul> |                |
| <h4 id="slack-webhookintegration-done-addwebhookslacktarget">Done (Add WebHook Slack Target)</h4><ul><li>Click the <strong>Add WebHook Slack Target</strong> button</li><li>Target is created, containing the selected destination.</li></ul>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |                |

## Example Slack Webhook <a href="#slack-webhookintegration-exampleslackwebhook" id="slack-webhookintegration-exampleslackwebhook"></a>



**URL**: generated on the Slack side
