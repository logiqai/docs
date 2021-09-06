# Log Data Rewrite

Your incoming log data might include Personally Identifiable Information \(PII\) that can identify an individual, either on its own or in combination with other relevant data. You may need to redact or replace PII or other sensitive data to stay compliant with data security regulations or support your business use case. LOGIQ supports the creation and use of custom regular expressions that match patterns in your incoming data stream and mask or replace these matched patterns.

### Example: Removing names and phone numbers from log data

In this example, assume that the following lines of data are from an incoming log data stream.

```text
2021-08-28 01:34:55.001Z Jane Smith phone number : (408) 555-1212
2021-08-29 01:34:55.002Z Raj Sigh local phone number => 206-555-1212
2021-08-30 01:34:55.003Z Tim White office phone number is 408121324
```

You notice that the data you are ingesting includes names and respective US phone numbers that fall under PII. To mask these names and US phone numbers from incoming data, you can use LOGIQ to create the following regular expression to sample and match incoming data.

```text
^(?P<name>\w+\s+\w+)\s+(?P<p1>.*)phone number(?P<p2>.*)\s(?P<phone>\D*\d{3}\D*\d{3}\D*\d{4})\s*$  
```

The regular expression above produces the following capture groups.

* \`$name\`
* \`$p1\`
* \`$p2\`
* \`$phone\`

The rewrite rule for replacing names and phone numbers in the above sample log data is as shown below.

```text
XXX-Name ${p1}phone number${p2} XXX-XXX-XXXX
```

The rewrite rule replaces `$name` and `$phone` among these groups while retaining `$p1` and `$p2`, providing the log data with redacted PII as the output, as shown below. 

```text
2021-08-28 01:34:55.001Z XXX-Name phone number : xxx-xxx-xxxx
2021-08-29 01:34:55.002Z XXX-Name local phone number is xxx-xxx-xxxx
2021-08-30 01:34:55.003Z XXX-Name office phone => xxx-xxx-xxxx
```

It is crucial to be mindful of the context of the regular expression you create for your incoming log data. In the example above, the incoming log data and the created regular expression contain the string "phone number". If you used a non-contextual regex that only matches and replaces numerical patterns, like the following example, you might end up substituting numbers in your log data that are not necessarily phone numbers.

```text
(?p<phone>\D*\d{3}\D*\d{3}\D*d{4})
```

{% hint style="info" %}
**Note**: For more information on RE2 search and replace syntax and best practices, do read the [RE2 documentation](https://qinwenfeng.com/re2r_doc/#2_replace_a_substring). 
{% endhint %}

### Creating a PII masking rule via the UI

You can create a custom rewrite rule to match and mask PII in your log data from the Rules section on your LOGIQ UI. To access create a new rule, click **Events** &gt; **Rules** &gt; **+ New Rule**.

![](../.gitbook/assets/rw1_2021-08-25_20-44-05.jpg)

To configure your rewrite rule, do the following. 

1. Select **Re-Write** from the **Rule Type** dropdown menu.
2. Provide a **Name** for your rule. 
3. Select a **Level** and **Group**. 
4. Provide a **Description** of the rule. 
5. Specify the **Namespace** to apply the rule. 
6. Optionally, provide an **ApplicationMatch** to match the application where you'd like to use the rule. 
7. Provide your **Match** and **Rewrite** expressions.  
8. Optionally, add match parameters. 
9. Click **Create Rule**. 

Your new rewrite rule is now created. You new rule will apply to all incoming log data for the specified namespace, look for patterns within the log data that match the match expression, and rewrite log data as per the rewrite expression. 










