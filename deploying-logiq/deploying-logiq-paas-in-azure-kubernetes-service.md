# Deploying LOGIQ PaaS in Azure Kubernetes Service

## Creating an Azure Kubernetes Cluster

From the Azure portal **Home** page, search for Kubernetes, and then click **Kubernetes services** from the search results.

![](../.gitbook/assets/1)

Click on **Create** > **Create Kubernetes cluster**

Under **Project details**, select:

* An Azure **Subscription**
* Select or create an Azure **Resource group**
* Select 2 availability zones

Under **Cluster details**, configure the following:

* **Kubernetes cluster name**
* Select a **Region** for the deployment
* Select two **Availability zones**
* Kubernetes version -1.19.11

Create three node pools as described in the following table. The below configuration is for ingesting 24 GB/day. Ensure that the node pools are all only **one availability zone**

| **Size**                   | **Node pool**             | **Node labels**      | **Node count** |
| -------------------------- | ------------------------- | -------------------- | -------------- |
| 4 Core 8 GB RAM (D4s\_v3)  | Ingest (CPU intensive)    | logiq.ai/node=ingest | 1              |
| 8 Core 16 GB RAM (F8s\_v2) | Common (Memory intensive) | logiq.ai/node=common | 1              |
| 4 Core 8 GB RAM (F4s\_v2)  | Hauler                    | logiq.ai/node=hauler | 1              |

The following screenshots depict the labeling of the node pools.

![](../.gitbook/assets/3) ![](../.gitbook/assets/4)

Review your configuration and click **Create**.

To connect with the Kubernetes cluster you just created, ensure you have [Azure CLI ](https://docs.microsoft.com/en-us/cli/azure/)installed, on your terminal, execute the below command.

```
az login --tenant “tenant-id”
```

Go to the Kubernetes service screen, select your cluster and click on the **Connect** icon and follow the instructions which display on the right panel.

### Create MinIO Blob Storage Gateway for S3 Compatibility&#x20;

Please follow the instructions on [MinIO’s site](https://az.minio.io/index.html#deploy-minio-6) to create a MinIO Blob Storage Gateway. Once you login, create a bucket inside MinIO, and copy the access keys. Next, install LOGIQ by following the instructions provided in the LOGIQ [Kubernetes quick start guide](k8s-quickstart-guide.md).&#x20;

You'll need to configure the following parameters in the values.yaml file to use MinIO Blob Storage Gateway.

```
awsServiceEndpoint: https://<your-blobstorage-accountname>.az.minio.io
s3_bucket: <S3 bucket created above>
AWS_ACCESS_KEY_ID: <Storage account name>
AWS_SECRET_ACCESS_KEY: <Access key from the Minio>
```

