# Deploying LOGIQ EKS on AWS using CloudFormation

## 1. Overview

This guide will take you through deploying LOGIQ.AI on an EKS cluster on AWS using CloudFormation and HELM. The installation will create user roles and policies that are necessary to create a GP3 storage class and a private S3 bucket with default encryption and bucket policies.&#x20;

## 2. EKS K8S compatibility

{% hint style="info" %}
**Note:** This deployment method using Helm is only supported on Kubernetes versions **1.18**, **1.19**, and **1.20**. Steps described in the document only work if the cluster is created using the given cloud formation template
{% endhint %}

## 3. AWS Resources

The cloud formation template provision the following resources

1. S3 Bucket
2. EKS Cluster
3. EKS Node Pools&#x20;
4. IAM Role - This role will have permissions to access the S3 bucket and managing Container Storage Interface for gp3 volumes.

## 4. Pre-requisites

Before you begin, ensure you have the following prerequisites.&#x20;

* You have permissions on your AWS account to create an Elastic Kubernetes Service, S3 Bucket, and IAM Roles.
* The AWS SDK is installed and configured on your machine&#x20;
* [Helm 3 ](https://helm.sh/docs/intro/install/)is installed on your machine.

## 5. Deployment steps

### 5.1 Create EKS Cluster

**Step 1:** To prepare for the deployment, first obtain the Cloudformation template that will be used.&#x20;

1. If you choose to host the Postgres database in RDS copy the following template URL to be used in step 3: **https://logiq-scripts.s3.ap-south-1.amazonaws.com/EKS1.yml**
2. For hosting the Postgres database within the EKS cluster, copy the following template URL to be used in step 3: **https://logiq-scripts.s3.ap-south-1.amazonaws.com/EKS2.yaml**

{% hint style="info" %}
**NOTE:** Using option 2 in Step 1 will create an additional node pool.
{% endhint %}

**Step 2**: On your AWS Console, navigate to CloudFormation and select **Create stack**.&#x20;

**Step 3**: Provide the options as shown in the screen capture below

* Under **Prerequisite - Prepare template**, select **Template is ready**.
* Under **Specify template** > **Template source**, select **Amazon S3 URL -** Here you will specify the template URL from Step 1 above.

![](<../.gitbook/assets/0 (3) (1)>)

**Step 4**: To deploy the EKS cluster, we need a VPC and 2 subnets. Select them from the **Network Configuration** and **Subnet Configuration** dropdown lists.

{% hint style="info" %}
**Important:** You **MUST** choose 2 different subnets from the same VPC.&#x20;
{% endhint %}

![](<../.gitbook/assets/image (14).png>)

**Step 5:** Provide an **S3 bucket name**. A private bucket with bucket policies will be created.

![](<../.gitbook/assets/image (15).png>)

**Step 6**: The EKS cluster will need the following node groups. Ensure that you select the node groups as specified in the following table.&#x20;

| Node group | Instance size (min recommended) | Nodes      |
| ---------- | ------------------------------- | ---------- |
| ingest     | c5.xlarge (4 Core 8 GB RAM)     | 2          |
| common     | c5.2xlarge (8 Core 32 GB RAM)   | 2          |
| db         | c5.xlarge (4 Core 8 GB RAM)     | 2 (For HA) |

**Step 7**: Click **Next**, and follow the instructions on the screen to create the stack.

### 5.2 Verify EKS setup

**Step 1**: Once the stack is fully provisioned, connect to the AWS EKS cluster using AWS CLI as mentioned below. To do this, you need to install and configure [AWS CLI](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html).

```
aws eks --region <AWS REGION> update-kubeconfig --name <EKS-cluster-name>
```

**Step 2**: Once the EKS cluster is up and running, execute the following commands to check the health of the cluster.

```
kubectl get namespace
NAME STATUS AGE
default Active 4h57m
kube-node-lease Active 4h57m
kube-public Active 4h57m
kube-system Active 4h57m
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

**Step 1**: Follow the instructions on LOGIQ's [Quickstart guide](https://docs.logiq.ai/deploying-logiq/k8s-quickstart-guide), and download the values file below as per the configuration picked in [Secton 5.1, Step 1](deploying-logiq-eks-on-aws-using-cloudformation.md#create-the-eks-cluster) above.,&#x20;

{% tabs %}
{% tab title="Using AWS RDS" %}
{% hint style="info" %}
Use the values file below if you picked RDS in section 5.1 step 1
{% endhint %}

{% file src="../.gitbook/assets/values (5).yaml" %}
{% endtab %}

{% tab title="Not using AWS RDS" %}
{% hint style="info" %}
Use the values file below if you picked local Postgres in section 5.1 step 1
{% endhint %}

{% file src="../.gitbook/assets/values (6).yaml" %}
{% endtab %}
{% endtabs %}

**Step 2**: Replace the following variables in the **values.yaml** from step 1 above to install the LOGIQ stack on your EKS cluster.

* `awsServiceEndpoint`: https://\<aws-region>.amazonaws.com
* `s3_bucket`: S3 bucket name
* `storageClass`: gp3
* `createStorageClass`: true

This completes the deployment of LOGIQ on an EKS cluster on AWS using a CloudFormation template.&#x20;
