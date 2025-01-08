---
description: >-
  This document helps to configure the vault service in development mode and
  ingest audit logs into Ascent using fluentBit.
---

# Vault

## Configuring Vault in dev mode and ingest the audit logs into Apica Ascent - OCI.

{% embed url="https://github.com/ApicaSystem/ApicaHub/tree/b263b6febab876f358aa05b7ec47b23dca0cac3f/integrations/vault/logs" %}
Download and place the configuration files in the working directory where you plan to set up and deploy Vault. Ensure the files are accessible and correctly formatted to avoid errors during deployment.
{% endembed %}

### Step 1: Create a Namespace for Vault

Create a namespace to isolate Vault resources.

```bash
kubectl create namespace vault
kubectl get namespace
```

### Step 2: Create a persistent volume vlaim (PVC) with access mode `ReadWriteOnce`

The persistent volume claim (PVC) is required to stores logs data, and fluentBit reads the logs data from this pvc and ingest it to Ascent.

Create the new PVC under vault namespace.

```bash
kubectl apply -f vault-pvc.yaml -n vault
kubectl get pvc -n vault
```

### Step 3: Install Vault in Dev Mode and Verify the Installation

The following commands installs the hashicorp vault in development mode.

```bash
helm repo add hashicorp https://helm.releases.hashicorp.com
helm repo update

helm upgrade --install vault hashicorp/vault \
       --set='server.dev.enabled=true' \
       --set='ui.enabled=true' \
       --set='ui.serviceType=LoadBalancer' \
       --namespace vault -f server.yaml --debug

kubectl get all -n vault
```

Verify the pods are in the running state, update the PVC access mode.

### Step 4: Update the PVC access mode to ReadWriteMany

Updating a PersistentVolumeClaim (PVC) to use the ReadWriteMany (RWX) access mode is necessary when multiple pods need simultaneous access to the same data. In this case, Vault pods write logs to the shared volume, while Fluent Bit reads these logs and ingests them into Apica Ascent

```bash
kubectl get pvc -n vault
kubectl edit pvc/<replace PV name> -n vault
```

Change the access mode from `ReadWriteOnce` to `ReadWriteMany` and save the updated configuration.

```yaml
spec:
  accessModes:
  - ReadWriteMany
```

### Step 4: Enable Audit Logs from the CLI



```bash
kubectl exec -it pod/vault-0 -n vault -- sh
vault login root
vault audit list
vault audit enable file file_path=/vault/logs/vault-audit.log log_format=json
vault audit list
```

### Step 5: Install Fluent Bit and Add Helm Repository

Add the Fluent Bit Helm repository and update it:

```bash
helm repo add fluent https://fluent.github.io/helm-charts
helm repo update
```

### Step 6: Create a ConfigMap for Fluent Bit

Apply the ConfigMap for Fluent Bit configuration.

#### Note: Before creating the ConfigMap, update the following TODOs in `fb-configmap.yaml`:

1. Replace the file path (`#TODO: REPLACE PATH`).
2. Replace the host (`#TODO: REPLACE HOST`).
3. Replace the URI if needed (`#TODO: REPLACE URI IF NEEDED`).
4. Replace the Bearer token (`#TODO: REPLACE Bearer token`).

```bash
kubectl apply -f fb-configmap.yaml -n vault
kubectl get configmap -n vault
kubectl apply -f fb-deployment.yaml -n vault
```

### Step 7: Generate Logs and Verify Fluent Bit Output

Generate some logs by logging into the Vault UI and creating secrets.

Verify the Fluent Bit pod logs:

```bash
kubectl logs pod/<pod name> -n vault
```

You should see the recent audit log content.

### Step 8: Verify Logs in Apica Ascent

1. Log in to Apica Ascent.
2. Navigate to **Logs & Insights**.
3. Look for the `vault-logs` namespace.
4. Click on the Vault app to view the logs.
