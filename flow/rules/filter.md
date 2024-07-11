# FILTER

The Filter rule allows you to filter events that meet specific criteria. This is particularly useful when you want to control the volume of data being stored or processed. For example, if you do not want to store debug or info logs, you can create a Filter rule that drops all log lines that contain these levels.

In addition to dropping entire log lines, Filter rules can also be configured to drop specific fields within a log line. This can be useful when you only want to retain certain fields of interest.

To create a Filter Rule, select a log line, click on the ellipsis button available on the log line, and select "Create Rule."

![](<../../.gitbook/assets/search-create-rule-dropdown.png>)

In the modal that opens after clicking "Create Rule," select "Filter" as the type of rule you want to create. Then, enter the necessary details for your Filter Rule, including a name for the rule, the group it belongs to, and any parameters needed to filter your log data.

Like every other rule, the Filter Rule also allows you to specify additional parameters to filter your log data. These may include fields like log severity level or timestamp, which can be used to control the data volumes.

Once you have provided all the necessary details, save your rule to create the Filter Rule.

![](<../../.gitbook/assets/Filter-create-rule.png>)

## Filter Fields

When creating a Filter Rule, users can choose to filter selected fields instead of dropping the entire log line. This can be particularly useful when logs contain metadata like Kubernetes labels that may not be needed for long-term storage or analysis.

To enable field filtering, toggle on the "Labels to Drop" option and select or enter the fields you wish to filter in the dropdown. This will ensure that only the selected fields are dropped from the log line, while other fields will still be retained.

By using field filtering in combination with the Filter Rule, you can ensure that your log data is efficiently managed and stored, with only the necessary fields retained for further analysis.

![](<../../.gitbook/assets/Filter-rule-drop-labels.png>)

Once you have created a Filter Rule and specified your filter criteria, all incoming log lines that match the criteria will be dropped before they are sent to storage or downstream systems. This can help to control the volume of data being stored and ensure that only relevant data is retained for further analysis.

In addition to creating custom Filter Rules, Apica Ascent also offers many inbuilt Filter Rules for various applications like Java, ingress, auditd, Kubernetes, and more. These pre-built rules can be easily accessed and configured to suit your specific needs, making it easy to filter out unnecessary data from your log streams.
