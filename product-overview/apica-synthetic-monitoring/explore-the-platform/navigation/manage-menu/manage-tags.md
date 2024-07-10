# Manage Tags

Categorization and identification of checks can be done by adding tags.



By default, there are a number of tags already defined for use. They represent some suggestions for common ways to use the tags. All predefined tags are fully editable.

## Tags Introduction <a href="#managetags-tagsintroduction" id="managetags-tagsintroduction"></a>

Adding tags in the Manage Tags view will make them available for use in all checks.



In Synthetic Monitoring tags are keys that can have multiple values, allowing for better context in results and management. For example, the key “Environment” could have values such as “Prod”, “Dev”, “Alpha”, “Beta”, letting you quickly identify checks running on different environments.

Tags can also be accessed through the ASM API, which lets you perform more intelligent categorization in automated tasks and integrations.

### Display <a href="#managetags-display" id="managetags-display"></a>

Tags are shown in various places in Synthetic Monitoring.

#### Dashboard <a href="#managetags-dashboard" id="managetags-dashboard"></a>

In the [Dashboard](https://apica-kb.atlassian.net/wiki/spaces/ASMDOCS/pages/2132246613/Dashboards), tags are indicated by the **Tag** icon next to the check name:



Hovering over the check name or tag icon will show the tags configured for the check:



#### Details <a href="#managetags-details" id="managetags-details"></a>

In the Check Details toolbar, tags are shown below the check name:



#### Results <a href="#managetags-results" id="managetags-results"></a>

In the [Result Details toolbar](https://apica-kb.atlassian.net/wiki/spaces/ASMDOCS/pages/2165735469/Understanding+Check+Results#Title-Section), tags are shown below the check name:



## Add Tags <a href="#managetags-addtags" id="managetags-addtags"></a>

#### Add Tags <a href="#managetags-addtags.1" id="managetags-addtags.1"></a>

You can add new tags and edit existing ones from the Manage Tags view.

**View**



**Add Tag**

To add a new tag:



* Click **Add Tag**



A new blank tag row is added to the table.



* Select a color for the tag



* Enter a tag name (key)



* Enter as many values as needed:
* Type a value text
* Press `Enter`
* Repeat for each value



* Click **Save**

The tag is now available for use in checks:

