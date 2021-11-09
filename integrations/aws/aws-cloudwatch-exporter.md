---
description: This guide explains how to export your AWS CloudWatch logs.
---

# AWS CloudWatch

## LOGIQ CloudWatch exporter Lambda function

You can export AWS CloudWatch logs to LOGIQ using an AWS Lambada function; the process is as below. AWS Lambda function can act as a trigger for a CloudWatch log stream.&#x20;

![](../../.gitbook/assets/flash-high-level-cloudwatch\(1\).png)

### Creating Lambda function

LOGIQ provides a CloudFormation template to create the logiq CloudWatch exporter lambda function.&#x20;

```
https://logiqcf.s3.amazonaws.com/cloudwatch-exporter/cf.yaml
```

{% hint style="info" %}
The same code is available in our [client-integrations](https://bitbucket.org/logiqcloud/client-integrations/src/master/cloudwatch-exporter/) git repository.
{% endhint %}

This CloudFormation stack creates a lambda function and its necessary permissions. The following attributes need to be configured.

| Parameter   | Description                                                    |
| ----------- | -------------------------------------------------------------- |
| APPNAME     | Application name, A readable name for Logiq to partition logs. |
| CLUSTERID   | Cluster ID, A readable name for Logiq to partition logs.       |
| NAMESPACE   | Namespace, A readable name for Logiq to partition logs.        |
| LOGIQHOST   | IP address or hostname of Logiq server.                        |
| INGESTTOKEN | JWT token to securely ingest logs                              |

## Configuring CloudWatch trigger

Once the CloudFormation stack is created, navigate to the AWS Lambda function(logiq-cloudwatch-exporter) and add a trigger.&#x20;

![](<../../.gitbook/assets/image (3).png>)

On the Add trigger page, select CloudWatch and select Log Group.&#x20;

![](<../../.gitbook/assets/image (4).png>)

Once this configuration is complete, any new logs coming to the configured CloudWatch Log group will be streamed to the Logiq cluster.
