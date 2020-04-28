---
description: This page describes the IAM Resources required for LOGIQ platform to run
---

# AWS IAM Resources

{% hint style="info" %}
NOTE: LOGIQ can use Athena and Glue on AWS optionally to power the SQL queries. Instructions below for Athena/Glue are only needed if you choose to use those services.
{% endhint %}

## LOGIQ User Role

You need to provide AWS access key and secret in LOGIQ server configuration with the following permissions. 

```javascript
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "VisualEditor0",
            "Effect": "Allow",
            "Action": [
                "s3:PutObject",
                "s3:GetObject",
                "s3:ListBucket"
            ],
            "Resource": [
                "arn:aws:s3:::<YOUR_BUCKET_NAME>",
                "arn:aws:s3:::<YOUR_BUCKET_NAME>/*"
            ]
        },
        {
            "Sid": "VisualEditor1",
            "Effect": "Allow",
            "Action": [
                "iam:PassRole",
                "s3:ListAllMyBuckets",
                "glue:CreateCrawler"
            ],
            "Resource": "*"
        }
    ]
}
```



You also need to provide AWS access key and secret in LOGIQ server configuration with **AmazonAthenaFullAccess** \(arn:aws:iam::aws:policy/AmazonAthenaFullAccess\) policy.

## IAM Service Role For Glue

You need to grant your IAM role permissions that AWS Glue can assume when calling other services on your behalf. This includes access to Amazon S3 for any sources, targets, scripts, and temporary directories that you use with AWS Glue. Permission is needed by crawlers, jobs, and development endpoints.

Please refer to the following guide for creating a service role for glue

### Create an IAM Role for AWS Glue

Please refer to the following guide for creating a service role for glue

{% embed url="https://docs.aws.amazon.com/en\_pv/glue/latest/dg/create-an-iam-role" %}

Use the below Inline policy for Glue Service Role. You need to update the policy with your actual S3 Bucket name. Alternately you can use the [Cloud formation template below](aws-iam-resources.md#aws-cloud-formation-template-for-glue-service-role) to create the Glue Service Role

```javascript
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "glue:*",
                "s3:GetBucketLocation",
                "s3:ListBucket",
                "s3:ListAllMyBuckets",
                "s3:GetBucketAcl",
                "iam:ListRolePolicies",
                "iam:GetRole",
                "iam:GetRolePolicy",
                "cloudwatch:PutMetricData"
            ],
            "Resource": [
                "*"
            ]
        },
        {
            "Effect": "Allow",
            "Action": [
                "s3:GetObject",
                "s3:PutObject",
                "s3:DeleteObject"
            ],
            "Resource": [
                "arn:aws:s3:::<YOUR_BUCKET_NAME>/*"
            ]
        },
        {
            "Effect": "Allow",
            "Action": [
                "logs:CreateLogGroup",
                "logs:CreateLogStream",
                "logs:PutLogEvents"
            ],
            "Resource": [
                "arn:aws:logs:*:*:/aws-glue/*"
            ]
        }
    ]
}
```

### AWS Cloud formation template for Glue Service Role

{% tabs %}
{% tab title="Glue-Service-Role-Cloudformation.yml" %}
```yaml
AWSTemplateFormatVersion: '2010-09-09'
Description: >-
  This template will build out the IAM Roles for Logiq Glue Crawler

Parameters:
  S3BucketName:
    Description: Name of the Logiq S3 bucket 
    Type: String

Resources:
  LogiqGlueCrawlerPolicy:
    Type: 'AWS::IAM::ManagedPolicy'
    Properties:
      ManagedPolicyName: Logiq-Glue-Crawler-Policy
      Description: Policy for Logiq Glue Crawler
      Roles: 
        - !Ref LogiqGlueCrawlerRole
      PolicyDocument:
        Version: 2012-10-17
        Statement:
          - Effect: Allow
            Action:
              - 'glue:*'
              - 's3:GetBucketLocation'
              - 's3:ListBucket'
              - 's3:ListAllMyBuckets'
              - 's3:GetBucketAcl'
              - 'iam:ListRolePolicies'
              - 'iam:GetRole'
              - 'iam:GetRolePolicy'
              - 'cloudwatch:PutMetricData'
            Resource:
              - '*'   
          - Effect: Allow
            Action:
              - 's3:DeleteObject'
              - 's3:PutObject'
              - 's3:GetObject'
            Resource:
              - !Sub 'arn:aws:s3:::${S3BucketName}/*'   
          - Effect: Allow
            Action:
              - 'logs:PutLogEvents'
              - 'logs:CreateLogStream'
              - 'logs:CreateLogGroup'
            Resource:
              - 'arn:aws:logs:*:*:/aws-glue/*'  

  LogiqGlueCrawlerRole:
    Type: 'AWS::IAM::Role'
    Properties: 
      AssumeRolePolicyDocument: 
        Version: '2012-10-17'
        Statement: 
          - 
            Effect: 'Allow'
            Principal: 
              Service: 
                - 'glue.amazonaws.com'
            Action: 
              - 'sts:AssumeRole'
      RoleName: Logiq-Glue-Service-Role
```
{% endtab %}
{% endtabs %}

