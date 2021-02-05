# 1-Click deployment using CloudFormation

## Overview <a id="overview"></a>

LOGIQ can be deployed on AWS in a single AMI instance in a 1-Click fashion using our CloudFormation template and the LOGIQ AMI from the Amazon Marketplace.

All the resources required to create and configure LOGIQ on AWS are taken care by the template. All you need to do is provide a few simple input parameters.

The CloudFormation template can be found below

```text
https://logiqcf.s3.amazonaws.com/releases/logiq-stack.json
```

{% hint style="info" %}
Please note that using the Marketplace AMI is not free and you will be charged per the marketplace published rates for LOGIQ
{% endhint %}

## Template parameters <a id="template-parameters"></a>

The following parameters need to be provided for a successful deployment via the CloudFormation template

### Stack name <a id="stack-name"></a>

![](https://blobscdn.gitbook.com/v0/b/gitbook-28427.appspot.com/o/assets%2F-LmzGprckLqwd5v6bs6m%2F-Ly4bERo8hA6sD8wcsA0%2F-Ly4dGdKGVgj3czze5PD%2FScreen%20Shot%202020-01-08%20at%206.50.43%20AM.png?alt=media&token=d3f5b8f2-6415-48ba-91de-9a3ae383084e)

### AWS Resource configuration <a id="aws-resource-configuration"></a>

The LOGIQ AMI is instantiated with an SSH key pair installed so a user can later connect to the AMI when required. In addition an S3 Bucket where the user data will be stored is required.

Optionally, the prefix for creating access control resources like a LOGIQ User and Role can be provided. For optional resources, we use defaults if none is provided. _It is strongly advised that a unique prefix string be used if you plan on running multiple instances so as to keep the users and roles separate._

![](https://blobscdn.gitbook.com/v0/b/gitbook-28427.appspot.com/o/assets%2F-LmzGprckLqwd5v6bs6m%2F-Ly4bERo8hA6sD8wcsA0%2F-Ly4dSsi70LCGJEeB_wG%2FScreen%20Shot%202020-01-08%20at%206.51.13%20AM.png?alt=media&token=14dfeb26-7038-459e-9215-3fa60f1152da)

### EC2 Instance configuration <a id="ec2-instance-configuration"></a>

The LOGIQ services are deployed in an EC2 instance in a specific region. The template asks you to select a region for deployment. You also need to select an appropriate instance size. By default an m5.xlarge instance is created if user does not change it.

A larger instance results in better performance. In addition, to secure your environment, it is strongly recommended that you provide a CIDR range for the clients that can connect to the LOGIQ server. This will be programmed in the security group created during the deployment.

![](https://blobscdn.gitbook.com/v0/b/gitbook-28427.appspot.com/o/assets%2F-LmzGprckLqwd5v6bs6m%2F-Ly4bERo8hA6sD8wcsA0%2F-Ly4eLENrOpRiD7BiWxg%2FScreen%20Shot%202020-01-08%20at%206.51.23%20AM.png?alt=media&token=ea257f62-f625-48a9-83c1-84315b9808e5)

## Supported Regions <a id="supported-regions"></a>

The CloudFormation template supports all AWS regions including Amazon GovCloud regions.

## Default user and password <a id="default-user-and-password"></a>

Once the LOGIQ instance is created, you can login to the instance using the below credentials

**user**: _logiq@foo.com_

**password**: _&lt;name of your CloudFormation stack&gt;-&lt;name of your S3 bucket&gt;_

e.g. if CloudFormation stack is called Foo and bucket is called Bar the password is Foo-Bar

## TLS Client certificates <a id="tls-client-certificates"></a>

LOGIQ server exposes several protocols via secure ports. The client public/private certificate to connect to the server is available via SSH into the AMI. The below command illustrates ssh into LOGIQ server instance and print the certificate details

```bash
$ ssh -i ~/Downloads/logiqai.pem ubuntu@3.82.5.14
$ sudo docker logs -f `sudo docker ps | grep quay.io/logiq/flash:rc.singlecontainer | awk '{ printf $1 }'
```

![](https://blobscdn.gitbook.com/v0/b/gitbook-28427.appspot.com/o/assets%2F-LmzGprckLqwd5v6bs6m%2F-Ly5NJ5w66w11HLmRxV8%2F-Ly5RZRmsx1pUhW089ZS%2FScreen%20Shot%202020-01-08%20at%2010.36.41%20AM.png?alt=media&token=76ed9f91-3a66-4d87-8702-843f1905faff)

