# Deploying LOGIQ EKS on AWS using CloudFormation

## 1. Overview

This guide will take you through deploying LOGIQ.AI on an EKS cluster on AWS using CloudFormation and HELM. The installation will create user roles and policies that are necessary to create a GP3 storage class and a private S3 bucket with default encryption and bucket policies.&#x20;

## 2. EKS K8S compatibility

{% hint style="info" %}
**Note:** This deployment method using Helm is only supported on Kubernetes versions **1.18**, **1.19**, and **1.20**. Steps described in the document only work if the cluster is created using the given cloud formation template
{% endhint %}

## 3. AWS Resources

The Cloud formation template provisions the following resources

1. S3 Bucket
2. EKS Cluster
3. EKS Node Pools&#x20;

### 3.1 IAM Role

Create a role for EKS and EKS Node Pools with the below policies. Alternatively, this can be created using Cloud formation template **** [**https://logiq-scripts.s3.ap-south-1.amazonaws.com/logiqiamrole.yaml**](https://logiq-scripts.s3.ap-south-1.amazonaws.com/logiqiamrole.yaml)**,** details of created resources will be in the output section of Cloud formation, these details are used in section 5(step 4 and 5).

* AmazonEKSWorkerNodePolicy&#x20;
* AmazonEC2ContainerRegistryReadOnly&#x20;
* AmazonEKS\_CNI\_Policy&#x20;
* AmazonEKSClusterPolicy&#x20;
* AmazonEKSServicePolicy

Create the managed policies below and attach them to the above role, this will enable one to create **GP3** volumes in the cluster.

```
{
 "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "ec2:CreateSnapshot",
                "ec2:AttachVolume",
                "ec2:DetachVolume",
                "ec2:ModifyVolume",
                "ec2:DescribeAvailabilityZones",
                "ec2:DescribeInstances",
                "ec2:DescribeSnapshots",
                "ec2:DescribeTags",
                "ec2:DescribeVolumes",
                "ec2:DescribeVolumesModifications"
            ],
            "Resource": "*"
        },
        {
            "Effect": "Allow",
            "Action": [
                "ec2:CreateTags"
            ],
            "Resource": [
                "arn:aws:ec2:*:*:volume/*",
                "arn:aws:ec2:*:*:snapshot/*"
            ],
            "Condition": {
                "StringEquals": {
                    "ec2:CreateAction": [
                        "CreateVolume",
                        "CreateSnapshot"
                    ]
                }
            }
        },
        {
            "Effect": "Allow",
            "Action": [
                "ec2:DeleteTags"
            ],
            "Resource": [
                "arn:aws:ec2:*:*:volume/*",
                "arn:aws:ec2:*:*:snapshot/*"
            ]
        },
        {
            "Effect": "Allow",
            "Action": [
                "ec2:CreateVolume"
            ],
            "Resource": "*",
            "Condition": {
                "StringLike": {
                    "aws:RequestTag/ebs.csi.aws.com/cluster": "true"
                }
            }
        },
        {
            "Effect": "Allow",
            "Action": [
                "ec2:CreateVolume"
            ],
            "Resource": "*",
            "Condition": {
                "StringLike": {
                    "aws:RequestTag/CSIVolumeName": "*"
                }
            }
        },
        {
            "Effect": "Allow",
            "Action": [
                "ec2:CreateVolume"
            ],
            "Resource": "*",
            "Condition": {
                "StringLike": {
                    "aws:RequestTag/kubernetes.io/cluster/*": "owned"
                }
            }
        },
        {
            "Effect": "Allow",
            "Action": [
                "ec2:DeleteVolume"
            ],
            "Resource": "*",
            "Condition": {
                "StringLike": {
                    "ec2:ResourceTag/ebs.csi.aws.com/cluster": "true"
                }
            }
        },
        {
            "Effect": "Allow",
            "Action": [
                "ec2:DeleteVolume"
            ],
            "Resource": "*",
            "Condition": {
                "StringLike": {
                    "ec2:ResourceTag/CSIVolumeName": "*"
                }
            }
        },
        {
            "Effect": "Allow",
            "Action": [
                "ec2:DeleteVolume"
            ],
            "Resource": "*",
            "Condition": {
                "StringLike": {
                    "ec2:ResourceTag/kubernetes.io/cluster/*": "owned"
                }
            }
        },
        {
            "Effect": "Allow",
            "Action": [
                "ec2:DeleteSnapshot"
            ],
            "Resource": "*",
            "Condition": {
                "StringLike": {
                    "ec2:ResourceTag/CSIVolumeSnapshotName": "*"
                }
            }
        },
        {
            "Effect": "Allow",
            "Action": [
                "ec2:DeleteSnapshot"
            ],
            "Resource": "*",
            "Condition": {
                "StringLike": {
                    "ec2:ResourceTag/ebs.csi.aws.com/cluster": "true"
                }
            }
        }
    ]
}
```

In order for the IAM role to access the S3 bucket, create the policy below and attach it to the above IAM role&#x20;

{% hint style="info" %}
**Note:** Replace \<Your-bucket-name> with the name of the unique bucket name.
{% endhint %}

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "ConsoleAccess",
            "Effect": "Allow",
            "Action": [
                "s3:GetAccountPublicAccessBlock",
                "s3:GetBucketAcl",
                "s3:GetBucketLocation",
                "s3:GetBucketPolicyStatus",
                "s3:GetBucketPublicAccessBlock"
            ],
            "Resource": "*"
        },
        {
            "Sid": "ListObjectsInBucket",
            "Effect": "Allow",
            "Action": "s3:ListBucket",
            "Resource": [
                "arn:aws:s3:::<Your-bucket-name>"
            ]
        },
        {
            "Sid": "AllObjectActions",
            "Effect": "Allow",
            "Action": "s3:*Object",
            "Resource": [
                "arn:aws:s3:::<Your-bucket-name>/*"
            ]
        }
    ]
}
```

Edit the Trust Relationship in the IAM role and add the following entities

{% hint style="info" %}
Without adding the trust relationship, roles cannot be attached to the EKS cluster and node-groups
{% endhint %}

* ec2.amazonaws.com
* eks.amazonaws.com

## 4. Pre-requisites

Before you begin, ensure you have the following prerequisites.&#x20;

1. You have permission on your AWS account to create an Elastic Kubernetes Service, S3 Bucket.
2. Above mentioned roles are created
3. The AWS CLI is installed and configured on your machine&#x20;
4. [Helm 3 ](https://helm.sh/docs/intro/install/)is installed on your machine.
5. If you choose to use AWS RDS, then follow the guidelines below for your RDS
   * Note down your RDS instance DNS, username, and password handy.
   * Use Postgres V13 RDS type with 100GB storage, io1 with 3000 IOPS.
   * We recommend creating a _db.m5.xlarge_ for deployments ingesting < 500GB/day and _db.m5.2xlarge_ for deployments ingesting > 500GB/day
   * Ensure EKS cluster can connect to AWS RDS Instance. Once the EKS cluster is created, add the security group of EKS cluster in the Postgres security group inbound rules for port 5432

## 5. Deployment steps

### 5.1 Create EKS Cluster

**Step 1:** To prepare for the deployment, first obtain the Cloudformation template that will be used at the URL: **** [ **** ](https://logiq-scripts.s3.ap-south-1.amazonaws.com/logiq-eks.yaml)****[**https://logiq-scripts.s3.ap-south-1.amazonaws.com/EKSCluster.yaml**](https://logiq-scripts.s3.ap-south-1.amazonaws.com/EKSCluster.yaml) ****&#x20;

**Step 2**: On your AWS Console, navigate to CloudFormation and select **Create stack**.&#x20;

**Step 3**: Provide the options as shown below

* Under **Prerequisite - Prepare template**, select **Template is ready**.
* Under **Specify template** > **Template source**, select **Amazon S3 URL -** Here you will specify the template URL from Step 1 above.

![](../.gitbook/assets/0)

**Step 4**: To deploy the EKS cluster, we need to enter the **ARN** of the **IAM Role for EKS** that was created in **section 3.1.** We need a VPC with 2 subnets. Select them from the Network Configuration and Subnet configuration dropdown lists.

{% hint style="info" %}
**Important:** You **MUST** choose 2 different subnets from the same VPC.&#x20;
{% endhint %}

<figure><img src="../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>

The EKS cluster will need the following node groups. Ensure that you select the node groups as specified in the following table.&#x20;

| Node group | Instance size (min recommended) | Nodes (HA) |
| ---------- | ------------------------------- | ---------- |
| **ingest** | c5.xlarge (4 Core 8 GB RAM)     | 2          |
| **common** | c5.2xlarge (8 Core 32 GB RAM)   | 2          |
| **db**     | c5.xlarge (4 Core 8 GB RAM)     | 2          |

<figure><img src="../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

**Step 5:** Provide the **S3 bucket name** from **section 3,** the Cloudformation will create the S3 bucket, S3 bucket name needs to be globally unique.

![](<../.gitbook/assets/image (73).png>)

**Step 6**: Click **Next**, and follow the instructions on the screen to create the stack.



### 5.2 Verify EKS setup and tag subnets

**Step 1**: Once the stack is fully provisioned, connect to the AWS EKS cluster using AWS CLI as mentioned below. To do this, you need to install and configure [AWS CLI](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html).

```
aws eks --region <AWS REGION> update-kubeconfig --name <EKS-cluster-name>
```

**Step 2**: Once the EKS cluster is up and running, execute the following commands to check the health of the cluster.

```bash
kubectl get namespace
NAME STATUS AGE
default Active 4h57m
kube-node-lease Active 4h57m
kube-public Active 4h57m
kube-system Active 4h57m
```

**Step 3:** [**Tag both subnets**](https://docs.aws.amazon.com/eks/latest/userguide/network\_reqs.html#vpc-subnet-tagging) used in EKS cloud formation as mentioned below. Replace the cluster name, region, and subnet-id.

```
aws ec2 create-tags --region <region> --resources <subnet-id> --tags Key="kubernetes.io/cluster/<cluster_name>",Value="shared"
```

### 5.3 Enable GP3 storage class for EKS

**Step 1**: The Amazon Elastic Block Store Container Storage Interface (CSI) Driver provides a [CSI](https://github.com/container-storage-interface/spec/blob/master/spec.md) interface used by Container Orchestrator to manage the lifecycle of Amazon EBS volumes. To enable GP3 volumes for this stack, run the following commands.

```
helm repo add aws-ebs-csi-driver https://kubernetes-sigs.github.io/aws-ebs-csi-driver

helm repo update

helm upgrade --install aws-ebs-csi-driver \
--namespace kube-system \
aws-ebs-csi-driver/aws-ebs-csi-driver
```

**Step 2**: Once the chart is installed, you should see pods similar to those shown below in your `kube-system` namespace.

```
kubectl get pods -n kube-system

ebs-csi-controller-745bf4d44d-9wrps 5/5 Running 0 3h53m
ebs-csi-controller-745bf4d44d-j7xjs 5/5 Running 0 3h53m
ebs-csi-node-fwwn2 3/3 Running 0 3h53m
ebs-csi-node-ksv8z 3/3 Running 0 3h53m
```

### 5.4 Deploy LOGIQ.AI using HELM

**Step 1**: Download the values file below and customize it per the instructions below.&#x20;

{% tabs %}
{% tab title="Values File For Helm" %}
{% file src="../.gitbook/assets/values (1).yaml" %}
{% endtab %}
{% endtabs %}

**Step 2**: Replace the following variables in the **values.yaml** from step 1 above and proceed to install the LOGIQ stack on your EKS cluster.

1. `awsServiceEndpoint`: https://s3.\<aws-region>.amazonaws.com
2. `s3_bucket`: S3 bucket name
3. `s3_region`: \<s3 region>

**Step 3:** Create the logiq namespace in your EKS cluster

```bash
kubectl create namespace logiq
```

**Step 4:** Deploy LOGIQ.AI stack using helm and updated values file, see below for additional options to customize the deployment for enabling https and to use external Postgres database

```bash
helm upgrade --install logiq -n logiq -f values.yaml logiq-repo/logiq
```

**Step 5 (Optional):** To enable https using self-signed certificates, please add additional options to helm and provide the domain name for the ingress controller. In the example below, replace **"logiq.my-domain.com"** with the https domain where this cluster will be available.

{% hint style="info" %}
NOTE: Your DNS will need to be programmed separately to map the domain to the service endpoint for logiq. Please see Step 7 below on how to obtain the service endpoint.
{% endhint %}

```bash
helm upgrade --install logiq -n logiq \
--set global.domain=logiq.my-domain.com \
--set ingress.tlsEnabled=true \
--set kubernetes-ingress.controller.defaultTLSSecret.enabled=true \
-f values.yaml logiq-repo/logiq
```

**Step 6 (Optional):** If you choose to deploy using AWS RDS, provide the following options below to customize

```bash
helm upgrade --install logiq -n logiq \
--set global.environment.postgres_host=<AWS RDS-host-ip/dns> \
--set global.environment.postgres_user=<AWS RDS-username> \
--set global.environment.postgres_password=<AWS RDS-password> \
--set global.chart.postgres=false \
-f values.yaml logiq-repo/logiq
```

&#x20;**Step 7:** After the installation is complete execute the below command to get the service endpoint

```bash
kubectl -n logiq get svc | grep LoadBalancer
NAME                        TYPE           CLUSTER-IP       EXTERNAL-IP
logiq-kubernetes-ingress     LoadBalancer <cluster_ip>    <Service end-point>
```

&#x20;
