# Deploying LOGIQ EKS on AWS using CloudFormation

This guide will take you through deploying a 2-node EKS cluster on AWS and installing LOGIQ on it using a CloudFormation template. Before you begin, ensure you have the following prerequisites.&#x20;

* Access to an Amazon Web Services account
* Access to create an Elastic Kubernetes Service on AWS
* AWS SDK installed and configured on your machine&#x20;
* Helm3 installed&#x20;

**Step 1**: To begin, navigate to CloudFormation on your AWS Console, and then click **Create stack**.&#x20;

**Step 2**: On the Create stack screen, select the following options as shown in the following screenshot.

* **Template is ready**
* In the **Amazon S3 URL** field, paste the link to the CloudFormation template: [https://logiq-scripts.s3.ap-south-1.amazonaws.com/EKS2.yaml](https://logiq-scripts.s3.ap-south-1.amazonaws.com/EKS2.yaml)

![](<../.gitbook/assets/0 (3)>)

**Step 3**: In order for the EKS cluster to be deployed, we need a VPC and 2 subnets. Select them from the **Network Configuration** and **Subnet Configuration** dropdown lists.

{% hint style="warning" %}
**Important:** Ensure that you choose 2 different subnets from the same VPC.&#x20;
{% endhint %}

![](../.gitbook/assets/1)

**Step 4**: The EKS cluster will need the following node groups. Ensure that you select the node groups as specified in the following table.&#x20;

|           |                               |       |
| --------- | ----------------------------- | ----- |
| Node pool | Instance size                 | Nodes |
| ingest    | c5.xlarge (4 Core 8 GB RAM)   | 1     |
| common    | c5.2xlarge (8 Core 32 GB RAM) | 1     |

**Step 5**: Click **Next**, review and agree to the AWS terms and conditions, and then click **Create stack**.

**Step 6**: To connect to the AWS EKS cluster created above, execute the following command. To do this, you need to install [AWS SDK](https://docs.aws.amazon.com/rekognition/latest/dg/setup-awscli-sdk.html) and configure it using your AWS keys.

```
aws eks --region <AWS REGION> update-kubeconfig --name <EKS-cluster-name>
```

**Step 7**: Once the stack is up and running, we need to create GP3 volumes. To create GP3 volumes, run the following commands.&#x20;

```
kubectl get node

kubectl get ns

NAME STATUS AGE
default Active 4h57m
kube-node-lease Active 4h57m
kube-public Active 4h57m
kube-system Active 4h57m
```

**Step 8**: To enable AWS to create GP3 volumes for our stack, run the following command.&#x20;

```
helm repo add aws-ebs-csi-driver https://kubernetes-sigs.github.io/aws-ebs-csi-driver

helm repo update

helm upgrade --install aws-ebs-csi-driver \
--namespace kube-system \
aws-ebs-csi-driver/aws-ebs-csi-driver
```

**Step 9**: Once the chart is installed, you should see pods similar to those shown below in your `kube-system` namespace.

```
kubectl get pods -n kube-system

ebs-csi-controller-745bf4d44d-9wrps 5/5 Running 0 3h53m
ebs-csi-controller-745bf4d44d-j7xjs 5/5 Running 0 3h53m
ebs-csi-node-fwwn2 3/3 Running 0 3h53m
ebs-csi-node-ksv8z 3/3 Running 0 3h53m
```

**Step 10**: Finally, following the instructions on LOGIQ's [Quickstart guide](https://docs.logiq.ai/deploying-logiq/k8s-quickstart-guide), download the values file from this [location](https://logiq-scripts.s3.ap-south-1.amazonaws.com/values.yaml), and **** replace the following variables in the **values.yaml** file to spin up the LOGIQ stack on the cluster.

* `awsServiceEndpoint`: https://\<aws-region>.amazonaws.com
* `S3_bucket`: S3 bucket name created.
* `AWS_ACCESS_KEY_ID`: AWS access key
* `AWS_SECRET_ACCESS_KEY`: AWS secret key
* `storageClass`: gp3

This completes the deployment of LOGIQ on an EKS cluster on AWS using a CloudFormation template.&#x20;
