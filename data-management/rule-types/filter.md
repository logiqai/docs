# Filter

The Filter rule filters events that meet its Filter criteria. This is useful when you want to control the data volumes. Assume that you do not want to store and debug/info logs, you can create a Filter rule that would drop all the log lines that are either info or debug. Filter rule can also drop the fields available in the log line without dropping the entire line.

Select a log line to create an extract rule, click on the ellipsis available on the logline and click on the "create rule".

![](<../../.gitbook/assets/image (25).png>)

In the modal that opens, select FILTER and enter the details.&#x20;

![](<../../.gitbook/assets/image (19).png>)

Like every other rule, Enter Name, Group, and Parameters to filter.

![](<../../.gitbook/assets/image (27) (1) (1).png>)

## Filter Fields

Users can optionally choose to filter selected fields instead of the entire logs line. This is useful in cases when logs contain metadata like the Kubernetes labels that may not be needed to store long term. To enable Field filtering toggle "Labels to Drop" and select or enter fields in the dropdown.

![](<../../.gitbook/assets/image (17) (1).png>)

Once the rule is created all the incoming log lines that match the criteria are dropped before sending storage or downstream systems.

LOGIQ offers many inbuilt Filter rules for various applications like Java, ingress, auditd, Kubernetes etc...
