---
description: >-
  This page describes the LOGIQ deployment on Kubernetes cluster using HELM 3
  charts.
---

# K8S Quickstart guide

## 1 - Prerequisites

Apica Ascent K8S components are made available as helm charts. The instructions below assume you are using HELM 3. 

### 1.1 Add Apica Ascent helm repository

#### 1.1.0 Adding Apica Ascent helm repository to your HELM repositories

```bash
helm repo add apica-repo https://logiqai.github.io/helm-charts
```

{% hint style="info" %}
The HELM repository will be named `apica-repo`. For installing charts from this repository please make sure to use the repository name as the prefix e.g.

`helm install <deployment_name> apica-repo/<chart_name>`
{% endhint %}

You can now run `helm search repo apica-repo` to see the available helm charts

```bash
$ helm search repo apica-repo
NAME                CHART VERSION    APP VERSION    DESCRIPTION
apica-repo/apica-ascent    2.2.11           2.1.11         Apica Ascent Observability HELM chart for Kubernetes
```

#### 1.1.1 Update your HELM chart

If you already added Apica Ascent HELM repository in the past, you can get updated software releases using `helm repo update`

```bash
$ helm repo update
$ helm search repo apica-repo
NAME                CHART VERSION    APP VERSION    DESCRIPTION
apica-repo/apica-ascent    2.2.11           2.1.11         Apica Ascent Observability HELM chart for Kubernetes
```

### 1.2 Create namespace where Apica Ascent will be deployed

{% hint style="danger" %}
NOTE: Namespace name cannot be more than 15 characters in length
{% endhint %}

```bash
kubectl create namespace apica-ascent
```

This will create a namespace **`apica-ascent`** where we will deploy the Apica Ascent Log Insights stack.

{% hint style="info" %}
If you choose a different name for the namespace, please remember to use the same namespace for the remainder of the steps
{% endhint %}

### 1.3 Prepare your Values YAML file

Sample YAML files for small, medium, large cluster configurations can be downloaded at the following links. 

{% tabs %}
{% tab title="values.small.yaml" %}
{% file src="../.gitbook/assets/values \(2\).yaml" caption="values.small.yaml" %}
{% endtab %}

{% tab title="values.medium.yaml" %}
{% file src="../.gitbook/assets/values.medium \(17\).yaml" caption="values.medium.yaml" %}
{% endtab %}

{% tab title="values.large.yaml" %}
{% file src="../.gitbook/assets/values.large \(18\).yaml" caption="values.large.yaml" %}
{% endtab %}
{% endtabs %}

These YAML files can be used for deployment with -f parameter as shown below in the description.

```bash
helm install apica-ascent --namespace apica-ascent \
--set global.persistence.storageClass=<storage class name> apica-repo/apica-ascent -f values.small.yaml
```

Please refer to [Section 3.10 ](k8s-quickstart-guide.md#3-10-sizing-your-LOGIQ-cluster) for sizing your Apica Ascent cluster as specified in these YAML files.

## 2. Install LOGIQ

```bash
helm install apica-ascent --namespace apica-ascent \
--set global.persistence.storageClass=<storage class name> apica-repo/apica-ascent
```

This will install Apica Ascent and expose the Apica Ascent services and UI on the ingress IP. If you plan to use an AWS S3 bucket, please refer to section [3.2](k8s-quickstart-guide.md#3-2-using-an-aws-s3-bucket) before running this step. Please refer to [Section 3.4 ](k8s-quickstart-guide.md#3-4-changing-the-storage-class)for details about storage class. Service ports are described in the [Port details section](https://docs.logiq.ai/logiq-server/quickstart-guide#ports). You should now be able to go to `http://ingress-ip/`

{% hint style="info" %}
The default login and password to use is `flash-admin@foo.com` and `flash-password`. You can change these in the UI once logged in. HELM chart can override the default admin settings as well. See section[ 3.7](k8s-quickstart-guide.md#3-7-customize-admin-account) on customizing the admin settings
{% endhint %}

![Apica Ascent Insights Login UI ](../.gitbook/assets/screen-shot-2020-03-24-at-3.42.55-pm.png)

Apica Ascent server provides Ingest, log tailing, data indexing, query, and search capabilities.  
Besides the web-based UI, Apica Ascent also offers [apicactl, Apica CLI](https://github.com/ApicaSystem/apicactl) for accessing the above features.

## 3 Customizing the deployment

### 3.1 Enabling https for the UI

```bash
helm install apica-ascent --namespace apica-ascent \
--set global.domain=ascent.my-domain.com \
--set ingress.tlsEnabled=true \
--set kubernetes-ingress.controller.defaultTLSSecret.enabled=true \
--set global.persistence.storageClass=<storage class name> apica-repo/apica-ascent
```

{% hint style="success" %}
You should now be able to login to Apica Ascent UI at your domain using `https://ascent.my-domain.com` that you set in the ingress after you have updated your DNS server to point to the Ingress controller service IP

The default login and password to use is `flash-admin@foo.com` and `flash-password`. You can change these in the UI once logged in.
{% endhint %}

{% hint style="info" %}
The `ascent.my-domain.com` also fronts all the Apica Ascent service ports as described in the [port details section](quickstart-guide.md#ports).
{% endhint %}

| HELM Option | Description | Defaults |
| :--- | :--- | :--- |
| `global.domain` | DNS domain where the Apica Ascent service will be running. This is required for HTTPS | No default |
| `ingress.tlsEnabled` | Enable the ingress controller to front HTTPS for services | false |
| `kubernetes-ingress.controller.defaultTLSSecret.enabled` | Specify if a default certificate is enabled for the ingress gateway | false |
| `kubernetes-ingress.controller.defaultTLSSecret.secret` | Specify the name of a TLS Secret for the ingress gateway. If this is not specified, a secret is automatically generated of option `kubernetes-ingress.controller.defaultTLSSecret.enabled` above is enabled. |  |

#### 3.1.1 Passing an ingress secret

If you want to pass your own ingress secret, you can do so when installing the HELM chart

```bash
helm install apica-ascent --namespace apica-ascent \
--set global.domain=ascent.my-domain.com \
--set ingress.tlsEnabled=true \
--set kubernetes-ingress.controller.defaultTLSSecret.enabled=true \
--set kubernetes-ingress.controller.defaultTLSSecret.secret=<secret_name> \
--set global.persistence.storageClass=<storage class name> apica-repo/apica-ascent
```

### 3.2 Using an AWS S3 bucket

Depending on your requirements, you may want to host your storage in your own K8S cluster or create a bucket in a cloud provider like AWS.

{% hint style="danger" %}
Please note that cloud providers may charge data transfer costs between regions. It is important that the Apica Ascent cluster be deployed in the same region where the S3 bucket is hosted
{% endhint %}

#### 3.2.1 Create an access/secret key pair for creating and managing your bucket <a id="3-1-1"></a>

Go to AWS IAM console and create an access key and secret key that can be used to create your bucket and manage access to the bucket for writing and reading your log files

#### 3.2.2 Deploy the Apica Ascent helm in gateway mode

Make sure to pass your `AWS_ACCESS_KEY_ID` and `AWS_SECRET_ACCESS_KEY` and give a bucket name. The S3 gateway acts as a caching gateway and helps reduce API costs.  
Create a bucket in AWS s3 with a unique bucket name in the region where you plan to host the deployment.

{% hint style="info" %}
You do not need to create the bucket, we will automatically provision it for you. Just provide the bucket name and access credentials in the step below.

If the bucket already exists, Apica Ascent will use it. Check to make sure the access and secret key work with it. Additionally, provide a valid amazon service endpoint for s3 else the config defaults to [https://s3.us-east-1.amazonaws.com](https://s3.us-east-1.amazonaws.com)
{% endhint %}

```bash
helm install apica-ascent --namespace apica-ascent --set global.domain=ascent.my-domain.com \
--set global.environment.s3_bucket=<bucket_name> \
--set global.environment.awsServiceEndpoint=https://s3.<region>.amazonaws.com \
--set global.environment.s3_region=<region> \
--set global.environment.AWS_ACCESS_KEY_ID=<access_key> \
--set global.environment.AWS_SECRET_ACCESS_KEY=<secret_key> \
--set global.persistence.storageClass=<storage class name> apica-repo/apica-ascent
```

| HELM Option | Description | Defaults |
| :--- | :--- | :--- |
| `global.cloudProvider` | This helm option specifies the supported cloudProvider that is hosting the S3 compatible bucket. Right now only `aws` is supported. | aws |
| `global.environment.s3_bucket` | Name of the S3 bucket in AWS | logiq |
| `global.environment.awsServiceEndpoint` | S3 Service endpoint : [https://s3.\*\*&lt;region&gt;\*\*.amazonaws.com](https://s3.**<region>**.amazonaws.com) | [https://s3.us-east-1.amazonaws.com](https://s3.us-east-1.amazonaws.com) |
| `global.environment.AWS_ACCESS_KEY_ID` | AWS Access key for accessing the bucket | No default |
| `global.environment.AWS_SECRET_ACCESS_KEY` | AWS Secret key for accessing the bucket | No default |
| `global.environment.s3_region` | AWS Region where the bucket is hosted | us-east-1 |

{% hint style="info" %}
S3 providers may have restrictions on bucket names for e.g. AWS S3 bucket names are globally unique.
{% endhint %}

### 3.3 Install Apica Ascent server certificates and Client CA `[OPTIONAL]`

Apica Ascent supports TLS for all ingest. We also enable non-TLS ports by default. It is however recommended that non-TLS ports not be used unless running in a secure VPC or cluster. The certificates can be provided to the cluster using K8S secrets. Replace the template sections below with your Base64 encoded secret files.

{% hint style="info" %}
If you skip this step, the Apica Ascent server automatically generates a ca and a pair of client and server certificates for you to use. you can get them from the ingest server pods under the folder `/flash/certs`
{% endhint %}

```yaml
apiVersion: v1
kind: Secret
metadata:
  name: logiq-certs
type: Opaque
data:
  ca.crt: {{ .Files.Get "certs/ca.crt.b64" }}
  syslog.crt: {{ .Files.Get "certs/syslog.crt.b64" }}
  syslog.key: {{ .Files.Get "certs/syslog.key.b64" }}
```

Save the secret file e.g. `logiq-certs.yaml`. Proceed to install the secret in the same namespace where you want to deploy Apica Ascent

The secret can now be passed into the Apica Ascent deployment

```bash
helm install apica-ascent --namespace apica-ascent --set global.domain=ascent.my-domain.com \
--set logiq-flash.secrets_name=logiq-certs \
--set global.persistence.storageClass=<storage class name> apica-repo/apica-ascent
```

| HELM Option | Description | Defaults |
| :--- | :--- | :--- |
| `logiq-flash.secrets_name` | TLS certificate key pair and CA cert for TLS transport | No default |

### 3.4 Changing the storage class

If you are planning on using a specific storage class for your volumes, you can customize it for the Apica Ascent deployment. By default, Apica Ascent uses the `standard` storage class

{% hint style="info" %}
It is quite possible that your environment may use a different storage class name for the provisioner. In that case please use the appropriate storage class name. E.g. if a user creates a storage class `ebs-volume` for the EBS provisioner for their cluster, you can use `ebs-volume` instead of `gp2` as suggested below
{% endhint %}

| Cloud Provider | K8S StorageClassName | Default Provisioner |
| :--- | :--- | :--- |
| AWS | gp2 | EBS |
| Azure | standard | azure-disc |
| GCP | standard | pd-standard |
| Digital Ocean | do-block-storage | Block Storage Volume |
| Oracle | oci | Block Volume |
| Microk8s | microk8s-hostpath |  |

```bash
helm upgrade --namespace apica-ascent \
--set global.persistence.storageClass=<storage class name> \
apica-ascent apica-repo/apica-ascent
```

### 3.5 Using external AWS RDS Postgres database instance

To use external AWS RDS Postgres database for your Apica Ascent deployment, execute the following command.

```bash
helm install apica-ascent --namespace apica-ascent \
--set global.chart.postgres=false \
--set global.environment.postgres_host=<postgres-host-ip/dns> \
--set global.environment.postgres_user=<username> \
--set global.environment.postgres_password=<password> \
--set global.persistence.storageClass=<storage class name> apica-repo/apica-ascent
```

| HELM Option | Description | Default |
| :--- | :--- | :--- |
| `global.chart.postgres` | Deploy Postgres which is needed for Apica Ascent metadata. Set this to false if an external Postgres cluster is being used | true |
| `global.environment.postgres_host` | Host IP/DNS for external Postgres | postgres |
| `global.environment.postgres_user` | Postgres admin user | postgres |
| `global.environment.postgres_password` | Postgres admin user password | postgres |
| `global.environment.postgres_port` | Host Port for external Postgres | 5432 |

{% hint style="warning" %}
While configuring RDS, create a new parameter group that sets autoVaccum to true or the value "1", associate this parameter group to your RDS instance.

Auto vacuum automates the execution of `VACUUM` and `ANALYZE` \(to gather statistics\) commands. Auto vacuum checks for bloated tables in the database and reclaims the space for reuse.
{% endhint %}

### 3.6 Upload Apica Ascent professional license

The deployment described above offers 30 days trial license. Send an e-mail to `support@apica.io` to obtain a professional license. After obtaining the license, use the apicactl tool to apply the license to the deployment. Please refer to `apicactl` details at [https://github.com/ApicaSystem/apicactl](https://github.com/ApicaSystem/apicactl). You will need API-token from Apica Ascent UI as shown below

![Apica Ascent Insights Login Api-token ](../.gitbook/assets/Screen-Shot-2020-08-09-ALERT.png)

```bash
Setup your Apica Ascent Cluster endpoint
- apicactl config set-cluster ascent.my-domain.com

Sets a Apica Ascent ui api token
- apicactl config set-token api_token

Upload your Apica Ascent deployment license
- apicactl license set -f=license.jws

View License information
 - apicactl license get
```

### 3.7 Customize Admin account

```bash
helm install apica-ascent --namespace apica-ascent \
--set global.environment.admin_name="LOGIQ Administrator" \
--set global.environment.admin_password="admin_password" \
--set global.environment.admin_email="admin@example.com" \
--set global.persistence.storageClass=<storage class name> apica-repo/apica-ascent
```

| HELM Option | Description | Default |
| :--- | :--- | :--- |
| `global.environment.admin_name` | Apica Ascent Administrator name | flash-admin@foo.com |
| `global.environment.admin_password` | Apica Ascent Administrator password | flash-password |
| `global.environment.admin_email` | Apica Ascent Administrator e-mail | flash-admin@foo.com |

### 3.8 Using external Redis instance

To use external Redis for your Apica Ascent deployment, execute the following command.

{% hint style="danger" %}
NOTE: At this time Apica Ascent only supports connecting to a Redis cluster in a local VPC without authentication. If you are using an AWS Elasticache instance, do not turn on encryption-in-transit or cluster mode.
{% endhint %}

```bash
helm install apica-ascent --namespace apica-ascent \
--set global.chart.redis=false \
--set global.environment.redis_host=<redis-host-ip/dns> \
--set global.persistence.storageClass=<storage class name> apica-repo/apica-ascent
```

| HELM Option | Description | Default |
| :--- | :--- | :--- |
| `global.chart.redis` | Deploy Redis which is needed for log tailing. Set this to false if an external Redis cluster is being used | true |
| `global.environment.redis_host` | Host IP/DNS of the external Redis cluster | redis-master |
| `global.environment.redis_port` | Host Port where external Redis service is exposed | 6379 |

### 3.9 Configuring cluster id

When deploying Apica Ascent, configure the cluster id to monitor your own Apica Ascent deployment. For details about the `cluster_id` refer to section [Managing multiple K8S clusters](agentless/#managing-multiple-k-8-s-clusters-in-a-single-logiq-instance)

```bash
helm install apica-ascent --namespace apica-ascent \
--set global.environment.cluster_id=<cluster id> \
--set global.persistence.storageClass=<storage class name> apica-repo/apica-ascent
```

| HELM Option | Description | Default |
| :--- | :--- | :--- |
| global.environment.cluster\_id | Cluster Id being used for the K8S cluster running Apica Ascent. See Section on [Managing multiple K8S](agentless/#managing-multiple-k-8-s-clusters-in-a-single-logiq-instance) clusters for more details. | Apica Ascent |

### 3.10 Sizing your Apica Ascent cluster

When deploying Apica Ascent, size your infrastructure to provide appropriate vcpu and memory requirements. We recommend the following minimum size for small. medium and large cluster specification from [Section 1.3 ](k8s-quickstart-guide.md#1-3-prepare-your-values-YAML-file) values yaml files.

| Apica Ascent Cluster | vCPU | Memory | NodeCount |
| :--- | :--- | :--- | :--- |
| small | 12 | 32 gb | 3 |
| medium | 20 | 56 gb | 5 |
| large | 32 | 88 gb | 8 |

### 3.11 NodePort/ClusterIP/LoadBalancer

The service type configurations are exposed in values.yaml as below

```bash
flash-coffee:
  service:
    type: ClusterIP
logiq-flash:
  service:
    type: NodePort
kubernetes-ingress:
  controller:
    service:
      type: LoadBalancer
```

For e.g. if you are running on bare-metal and want an external LB to front Apica Ascent, configure all services as `NodePort`

```bash
helm install apica-ascent -n apica-ascent -f values.yaml \
--set flash-coffee.service.type=NodePort \
--set logiq-flash.service.type=NodePort \
--set kubernetes-ingress.controller.service.type=NodePort \
apica-repo/apica-ascent
```

### 3.12 Using Node Selectors

The Apica Ascent stack deployment can be optimized using node labels and node selectors to place various components of the stack optimally

```bash
logiq.ai/node=ingest
```

The node label `logiq.ai/node` above can be used to control the placement of ingest pods for log data into ingest optimized nodes. This allows for managing cost and instance sizing effectively.

The various nodeSelectors are defined in the globals section of the values.yaml file

```bash
globals:
  nodeSelectors:
    enabled: true
    ingest: ingest
    infra: common
    other: common
    db: db
    cache: cache
    ingest_sync: sync
```

In the example above, there are different node pools being used - `ingest` , `common` , `db`, `cache` and `sync`

{% hint style="info" %}
Node selectors are enabled by setting `enabled` to `true` for `globals.nodeSelectors`
{% endhint %}

### 3.13 Installing Grafana

The Apica Ascent stack includes Grafana as part of the deployment as an optional component. To enable Grafana in your cluster, follow the steps below

```bash
helm upgrade --install apica-ascent --namespace apica-ascent \
--set global.chart.grafana=true \ 
--set global.persistence.storageClass=<storage class name> apica-repo/apica-ascent
```

The Grafana instance is exposed at port 3000 on the ingress controller. The deployed Grafana instance uses the same credentials as the Apica Ascent UI

## 4 Teardown

If and when you want to decommission the installation using the following commands

```bash
helm delete apica-ascent --namespace apica-ascent
helm repo remove apica-repo
kubectl delete namespace apica-ascent
```

If you followed the installation steps in section 3.1 - Using an AWS S3 bucket, you may want to delete the s3 bucket that was specified at deployment time.

