# EXTRACT

Apica Ascent provides pre-built rules to parse the fields of ingested log events. However, you can customize these rules to meet your specific needs. Here's how:

1. Select a log line that you want to create an extract rule for.
2. Hover/Click on the ellipsis button that's available on the log line.
3. Click on "Create Rule" to create a new extract rule.

![](<../../.gitbook/assets/search-create-rule-dropdown.png>)

From here, you can define the fields that you want to extract and configure the rule to match your specific use case.

In the modal that opens after clicking "Create Rule," select "Extract" as the type of rule you want to create. Then, enter the details for your extract rule.

![](<../../.gitbook/assets/create-rule-modal-extract.png>)

Like every other rule, when creating an Extract Rule, you will need to enter a name for the rule, specify the group it belongs to. Additionally, you will need to specify a regex pattern of re2 flavour that the rule should match against in order to extract the desired fields from your log data. Once you have provided all the necessary details, save your rule to create the Extract Rule.

![](<../../.gitbook/assets/extract-rule-demo.png>)

Apica Ascent uses [re2 Regular expressions](https://github.com/google/re2/wiki/Syntax) for creating pattern expression, A sample expression for extracting ingress logs are mentioned below.

```
(?P<server_ip>\S+) (?P<method>\S+) (?P<uri>\S+) (?P<uri_query>\S+) (?P<server_port>\d+) (?P<username>\S+) (?P<client_ip>\S+) (?P<user_agent>\S+) (?P<referer>\S+) (?P<status>\S+) (?P<substatus>\S+) (?P<win32_status>\S+) (?P<time_taken>\S+)
```

Extract Rule also allows you to give a piece of JavaScript code that can access the Log with the 'Event' object in its scope. Read Code Rule for more details.

Once you have created an Extract Rule, all incoming log lines that match the specified criteria will be evaluated, and the fields will be extracted if available.

In addition to the ability to create custom Extract Rules, Apica Ascent also offers a variety of pre-built rules for popular applications such as IIS, ingress, AWS VPC Flow logs, etc. These pre-built rules can help you get started quickly and streamline the process of configuring your data management rules.
