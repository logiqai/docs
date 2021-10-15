---
description: This document lists out the AWS resources needed to get started with LOGIQ
---

# Getting started

## Create an S3 bucket

LOGIQ stores all your ingested logs in an S3 bucket. You will need to create a bucket in a region which has Athena access. Please refer to the [AWS documentation](https://docs.aws.amazon.com/general/latest/gr/rande.html#athena) for Athena regions.

## Generate Programmatic access keys for LOGIQ 

* Go to your AWS IAM console and add a user for programmatic access. 
* Download and save the Secret and Access key for the user. This will be later used to access your S3 bucket where log data will be ingested.

Proceed to [AWS IAM Resources](aws-iam-resources.md) to configure permissions for the user.

## Running the LOGIQ cluster

You should now have the following information created and ready for using and running a LOGIQ cluster.

1. AWS S3 bucket name and ARN
2. Access/Secret key for S3 and Athena access
3. Glue service role and ARN

### Self hosted

If you are hosting LOGIQ instances in your AWS account, you can setup using [Cloud formation](../deploying-logiq/aws-cloudformation.md) instructions in the AWS Quickstart guide.

### Managed service

If LOGIQ is running as a managed cluster for you, please provide us with the above information to get up and running.



