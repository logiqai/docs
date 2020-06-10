---
description: >-
  This page describes the AWS CloudFormation based deployment for the LOGIQ
  stack
---

# AWS Quickstart guide

## Overview

LOGIQ can be deployed on AWS in a single AMI instance in a 1-Click fashion using our CloudFormation template and the LOGIQ AMI from the Amazon Marketplace. Please read and agree [EULA](https://docs.logiq.ai/eula/eula) before proceeding.

All the resources required to create and configure LOGIQ on AWS are taken care by the template. All you need to do is provide a few simple input parameters.

The CloudFormation template can be found in the software subscription at the AWS marketplace

```
https://aws.amazon.com/marketplace/pp/B083ZMYQNV
```

{% hint style="info" %}
Please note that using the Marketplace AMI is not free and you will be charged per the marketplace published rates for LOGIQ
{% endhint %}

## LOGIQ UI credentials <a id="default-user-and-password"></a>

Once the LOGIQ instance is created, you can login to the instance using the below credentials

**user**: _logiq@foo.com_

**password**: _&lt;name of your CloudFormation stack&gt;-&lt;name of your S3 bucket&gt;_

e.g. if CloudFormation stack is called Foo and bucket is called Bar the password is Foo-Bar

## AWS Quickstart video

{% embed url="https://www.youtube.com/watch?v=IDmJOF9y5Ac" %}

Also see section on [AMI using CloudFormation](../running-on-aws/ami-using-cloudformation.md) for more details.

## Ingesting data

Please refer to section on [data ingestion](agentless.md) for more details.

