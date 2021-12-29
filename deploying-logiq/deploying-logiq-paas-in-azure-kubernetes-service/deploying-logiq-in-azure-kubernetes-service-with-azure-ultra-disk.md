# Deploying LOGIQ in Azure Kubernetes Service with Azure Ultra Disk

In this guide, we'll look at how you can deploy LOGIQ in AKS with storage backed by Azure ultra disks. This type of deployment involves the following steps.

* Creating an AKS cluster and associated node pools
* Creating an Azure blob storage account on MinIO
* Creating an Azure ultra disk storage class
* Deploying LOGIQ on the cluster

**Step1:** Install [Azure CLI](https://docs.microsoft.com/en-us/cli/azure/).

**Step2:** Connect to your Azure account using Azure CLI by running the following command.

```
az login --tenant “tenant-id”
```

**Step3:** Create a resource group by running the following command.

```
az group create --name <Resource group name> --location <location>
```

**Step4:** Create four node pools as described and labelled in the following table. The table describes the node pool configuration for ingesting 100 GB of data per day.

{% hint style="warning" %}
**Important:** Ensure that the node pools are all created in the **same availability zone**.
{% endhint %}

| **Size**                   | **Node pool**          | **Node labels**      | **Node count** |
| -------------------------- | ---------------------- | -------------------- | -------------- |
| 8 Core 16 GB RAM (F8s\_v2) | ingest (CPU intensive) | logiq.ai/node=ingest | 1              |
| 8 Core 16 GB RAM (F8s\_v2) | common                 | logiq.ai/node=common | 1              |
| 4 Core 8 GB RAM (F4s\_v2)  | db                     | logiq.ai/node=db     | 1              |
| 4 Core 8 GB RAM (F4s\_v2)  | hauler                 | logiq.ai/node=hauler | 1              |

Execute the following commands to create the AKS cluster along with the node pools described above.

```
az aks create -g <your resource group> --name <cluster name> -l <location> --node-vm-size Standard_f8s_v2 --zones 1 --nodepool-name ingest --nodepool-labels logiq.ai/node=ingest --node-count 1 --enable-ultra-ssd

az aks nodepool add --cluster-name <cluster name> --name common --resource-group <You resource group> --zones 1 --labels logiq.ai/node=common --node-vm-size standard_f8s_v2 --node-count 1 --enable-ultra-ssd

az aks nodepool add --cluster-name <cluster name> --name db --resource-group <You resource group> --zones 1 --labels logiq.ai/node=db --node-vm-size standard_f4s_v2 --node-count 1 --enable-ultra-ssd

az aks nodepool add --cluster-name <cluster name> --name hauler --resource-group <You resource group> --zones 1 --labels logiq.ai/node=hauler --node-vm-size standard_f4s_v2 --node-count 1 --enable-ultra-ssd
```

The following code block depicts example commands for creating the AKS cluster with the node pool specification provided in the table above.

```
az aks create -g azure-test --name logiqai -l eastus --node-vm-size Standard_f8s_v2 --zones 1 --nodepool-name ingest --node-count 1 --nodepool-labels logiq.ai/node=ingest --enable-ultra-ssd

az aks nodepool add --cluster-name logiqai --name common --resource-group azure-test --zones 1 --labels logiq.ai/node=common --node-vm-size standard_f8s_v2 --node-count 1 --enable-ultra-ssd

az aks nodepool add --cluster-name logiqai --name hauler --resource-group azure-test --zones 1 --labels logiq.ai/node=hauler --node-vm-size standard_f4s_v2 --node-count 1 --enable-ultra-ssd

az aks nodepool add --cluster-name logiqai --name db --resource-group azure-test --zones 1 --labels logiq.ai/node=db --node-vm-size standard_f4s_v2 --node-count 1 --enable-ultra-ssd
```

Your AKS cluster and associated node pools should now be provisioned. You can verify this by visiting the Azure portal and viewing the AKS service and node pools, as depicted below.&#x20;

![](https://lh4.googleusercontent.com/son2vtRRR2B9h3yfEtftxq94fcik3Hvf-GSvt\_LPr9AAvqYlVCes57TNxD15Z2zwHxItR5vh\_mpmMYJ\_OWGXrfO2lJx664mYTks20FHN9FS0avQkLmRMVcUeDAuzOdgDxJbNDwpJ)

Connect to the AKS cluster by first visiting the Azure portal, navigating to the AKS cluster you created, and selecting it. Next, click on the **Connect** icon and follow the instructions displayed on the right panel. Execute the following command and you should see the nodes in your cluster.

```
kubectl get node
```

**Step 5:** Follow the instructions on [MinIO’s site](https://az.minio.io/index.html#deploy-minio-6) to create an Azure blog storage account. Once you login, click the “+” button on the right hand corner of the screen to create a bucket named `logiq`. Note down this bucket name since we'd be using it in later steps.&#x20;

![](https://lh5.googleusercontent.com/TOZYU86wNeRjxOZ9QmDu9jZHSleUQoZTqtRYFgQldthGDhmdNTOzMwyRlj6OUXB9KYPDeNNNe-007GbbedzFrc7-FlZK5X5zfGYQXhOdVAB5lDaMiMPo9VMt7XpeUzt16UXWrNrM)

**Step 6:** Create an [Azure ultra disk](https://azure.microsoft.com/en-us/services/storage/blobs/) storage class using the YAML configuration provided below.&#x20;

```
kind: StorageClass
apiVersion: storage.k8s.io/v1
metadata:
name: ultra-disk-sc
provisioner: kubernetes.io/azure-disk
volumeBindingMode: WaitForFirstConsumer # optional, but recommended if you want to wait until the pod that will use this disk is created
parameters:
skuname: UltraSSD_LRS
cachingMode: None
kind: managed
diskIopsReadWrite: "3000" # minimum value: 2 IOPS/GiB
diskMbpsReadWrite: "125" # minimum value: 0.032/GiB
```

**Step 7:** Verify that the storage class has been created by running the following command.&#x20;

```
kubectl get sc ultra-disk-sc
```

**Step 8:** Download the `values.yaml` file from [this location](https://logiq-scripts.s3.ap-south-1.amazonaws.com/values.yaml) and replace the following variables in the file.&#x20;

```
awsServiceEndpoint: https://<your-blobstorage-accountname>.az.minio.io
s3_bucket with the minio bucketname created at step 5.
AWS_ACCESS_KEY_ID: minio service name
AWS_SECRET_ACCESS_KEY: access key from the mino.
storageClass: ultra-disk-sc
```

**Step 9:** Finally, follow the instructions on LOGIQ’s [Quickstart guide](https://docs.logiq.ai/deploying-logiq/k8s-quickstart-guide) to spin up the LOGIQ stack on this AKS cluster.&#x20;

This completes the deployment of LOGIQ on an AKS cluster with Azure blog storage.&#x20;

**Step 10 **_**(optional)**_**:** Execute the following command to disable monitoring AKS with container insights on your cluster.&#x20;

```
az aks disable-addons -a monitoring -n <aks cluster name> -g <resource group>
```
