# Extract

Ingested Log events fields can be fully parsed using the pre-built LOGIQ.ai pack rules. The section illustrates how one customizes it for its need. &#x20;

Select a log line user want to create an extract rule, click on the ellipsis available on the logline  and click on the "create rule"

![](<../../.gitbook/assets/image (25).png>)

In the modal that opens, select EXTRACT and enter the details.&#x20;

![](<../../.gitbook/assets/image (29).png>)

Like every other rule, Enter Name, Group, Parameters to filter (optional), and Pattern.

![](<../../.gitbook/assets/image (27) (1).png>)

LOGIQ uses [re2 Regular expressions](https://github.com/google/re2/wiki/Syntax) for creating pattern expression, A sample expression for extracting ingress logs are mentioned below.&#x20;

```
(?P<server_ip>\S+) (?P<method>\S+) (?P<uri>\S+) (?P<uri_query>\S+) (?P<server_port>\d+) (?P<username>\S+) (?P<client_ip>\S+) (?P<user_agent>\S+) (?P<referer>\S+) (?P<status>\S+) (?P<substatus>\S+) (?P<win32_status>\S+) (?P<time_taken>\S+)
```

Once the rule is created all the incoming log lines that match the criteria are evaluated and the fields are extracted if available.

LOGIQ offers many inbuilt rules for various applications like IIS, ingress, AWS VPC Flow logs etc...
