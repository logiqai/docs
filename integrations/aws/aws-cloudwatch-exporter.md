---
description: This guide explains how to export your AWS CloudWatch logs to LOGIQ.
---

# AWS CloudWatch

## LOGIQ CloudWatch exporter Lambda function

You can export AWS CloudWatch logs to LOGIQ using an AWS Lambada function. The AWS Lambda function acts as a trigger for a CloudWatch log stream.&#x20;

This guide explains the process for setting up an AWS Lambda function and configuring an AWS CloudWatch trigger to forward CloudWatch logs to LOGIQ.

![](../../.gitbook/assets/flash-high-level-cloudwatch\(1\).png)

### Creating a Lambda function

LOGIQ provides CloudFormation templates to create the LOGIQ CloudWatch exporter Lambda function.&#x20;

Depending on the type of logs you'd like to export, use the appropriate CloudFormation template from the following list.&#x20;

#### Exporting Lambda Function logs

Use the following CloudFormation template to export AWS Lambda function logs to LOGIQ.

```
https://logiqcf.s3.amazonaws.com/cloudwatch-exporter/logiq-cloudwatch-lambda-logs-exporter.yaml
```

#### Exporting CloudTrail Logs

Use the following CloudFormation template to export CloudTrail logs to LOGIQ.

```
https://logiqcf.s3.amazonaws.com/cloudwatch-exporter/logiq-cloudwatch-cloudtrail-exporter.yaml
```

#### Exporting AWS VPC Flowlogs

Use the following CloudFormation template to export Flowlogs logs to LOGIQ.

```
https://logiqcf.s3.amazonaws.com/cloudwatch-exporter/logiq-cloudwatch-flowlogs-exporter.yaml
```

#### Exporting Cloudwatch logs from other services

Use the following CloudFormation template to export cloudwatch logs.&#x20;

```
https://logiqcf.s3.amazonaws.com/cloudwatch-exporter/logiq-cloudwatch-exporter.yaml
```

This CloudFormation stack creates a Lambda function and its necessary permissions. You must configure the following attributes.

| Parameter     | Description                                                         |
| ------------- | ------------------------------------------------------------------- |
| `APPNAME`     | Application name - a readable name for LOGIQ to partition logs.     |
| `CLUSTERID`   | Cluster ID - a readable name for LOGIQ to partition logs.           |
| `NAMESPACE`   | Namespace - a readable name for LOGIQ to partition logs.            |
| `LOGIQHOST`   | IP address or hostname of the LOGIQ server. (Without http or https) |
| `INGESTTOKEN` | JWT token to securely ingest logs                                   |

## Configuring the CloudWatch trigger

Once the CloudFormation stack is created, navigate to the AWS Lambda function (`logiq-cloudwatch-exporter`) and add a trigger.&#x20;

![](<../../.gitbook/assets/image (3).png>)

On the **Add trigger** page, select **CloudWatch**, and then select a CloudWatch Logs **Log Group**.&#x20;

![](<../../.gitbook/assets/image (4).png>)

Once this configuration is complete, any new logs coming to the configured CloudWatch Log group will be streamed to the LOGIQ cluster.
