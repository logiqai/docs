# Fluent Bit

## Fluent Bit configuration

_HTTP_ output plugin allows to flush your records into a HTTP endpoint. The **HTTP** output plugin allows to provide interoperability between compatible systems, Logiq being one.

The below code block defines the minimal changes to be added to the fluent-bit configuration using the http plugin to start sending log events to flash.

```
[INPUT]
    Name              tail
    Path              /var/log/*
    Path_Key          On
    Tag               logiq
    Buffer_Max_Size   1024k
    Read_from_Head    On

[FILTER]
    Name          record_modifier
    Match         logiq
    Record cluster_id flash

[FILTER]
    Name          record_modifier
    Match         logiq
    Record namespace mesos

[FILTER]
    Name          record_modifier
    Match         logiq
    Record app_name fluentbit


[OUTPUT]
    Name          http
    Match         *
    Host          localhost
    Port          80
    URI           /v1/json_batch
    Format        json
    tls           off
    tls.verify    off
    net.keepalive off
    compress      gzip
    Header Authorization Bearer ${LOGIQ_TOKEN}
```

## Fluent Bit for Windows

You can use Fluent Bit to ship Windows logs to LOGIQ by leveraging the following Fluent Bit configuration.

```
[SERVICE]
    Flush           5
    Daemon          yes
    Log_Level       info


[FILTER]
    Name          record_modifier
    Match         *
    Record namespace Windows 

[FILTER]
    Name modify
    Match *
    Rename SourceName AppName
    Rename ComputerName Hostname


[INPUT]
    Name                   winlog
    Channels               Setup,Windows PowerShell,Security
    Tag                    Windows-events
    Interval_Sec           5



[OUTPUT]
    name                   http
    match                  *
    host                   Logiq-Hostname
    port                   443
    URI                    /v1/json_batch
    Format                 json
    tls                    on
    tls.verify             off
    net.keepalive          off
    compress               gzip
    Header Authorization Bearer <token>
```

To forward Windows logs to LOGIQ using Fluent Bit, do the following.&#x20;

1. Copy the configuration provided above and save it locally in a temporary folder.&#x20;
2. Edit the fields in the `[OUTPUT]` section of the configuration file to match your LOGIQ instance.&#x20;
3. Clone the LOGIQ installation GitHub repository locally and navigate to the `windows` folder.
4. Copy and paste the `fluent-install.ps1` script into the folder where you saved the Fluent Bit configuration file.&#x20;
5.  Since Windows does not allow you to execute scripts due to default PowerShell script execution policies, you should update the set execution policy by running:&#x20;

    ```
    Set-ExecutionPolicy unrestricted
    ```
6. Navigate to **Windows** > **PowerShell** and run it in Administrator mode.&#x20;
7.  Execute the `fluent-install.ps1` script, as shown in the following example:

    ```
    PS D:\test> .\fluentbit-install.ps1
    [SC] CreateService SUCCESS
    The fluent-bit service is starting.
    The fluent-bit service was started successfully.
    ```
8. Navigate to **Windows** > **Run**. &#x20;
9. Type `services.msc` and hit Enter.&#x20;

You'll now see a Fluent Bit service running on your Windows machine.&#x20;

## Fluent Bit K8S

If you are running a K8S cluster, you can use fluent-bit to send data to the LOGIQ server. Please see below for instructions

### Managing multiple K8S clusters in a single LOGIQ instance

LOGIQ has provided its own fluent-bit daemon for deploying on K8S clusters. It is available at [https://bitbucket.org/logiqcloud/client-integrations/src/master/fluent-bit/](https://bitbucket.org/logiqcloud/client-integrations/src/master/fluent-bit/). It allows the administrator to pass a human readable `CLUSTER_ID` or cluster identifier with all the log data.

{% hint style="success" %}
Providing a CLUSTER\_ID allows LOGIQ to separate namespaces that may be conflicting in two separate K8S clusters.

It is also easier for the administrator to use human readable names vs LOGIQ using uuid's etc that it detects from the incoming stream.
{% endhint %}

### Running the fluent-bit daemonset

* Clone the repository to get the **`kubectl`** YAML files to start your daemonset

```
git clone https://bitbucket.org/logiqcloud/client-integrations.git
```

* The files needed are under folder **`fluent-bit`**

```
$ cd client-integrations/
$ cd fluentd-bit/
$ ls -la
total 64
drwxr-xr-x  8 user  staff   256 Aug  9 05:47 .
drwxr-xr-x  9 user  staff   288 Aug  9 05:20 ..
-rw-r--r--  1 user  staff  2446 Aug  9 05:47 README.md
-rw-r--r--  1 user  staff  8688 Aug  9 05:32 fluent-bit-config-logiq-forward.yml
-rw-r--r--  1 user  staff  1670 Aug  9 05:29 fluent-bit-daemonset-logiq-output.yml
-rw-r--r--  1 user  staff   269 Aug  9 05:26 fluent-bit-role-binding.yaml
-rw-r--r--  1 user  staff   194 Aug  9 04:49 fluent-bit-role.yaml
-rw-r--r--  1 user  staff    86 Aug  9 05:25 fluent-bit-service-account.yaml
```

To get started run the following commands to create the namespace, service account and role setup:

```bash
$ kubectl create namespace logiq-logging
$ kubectl create -f fluent-bit-service-account.yaml
$ kubectl create -f fluent-bit-role-binding.yaml
$ kubectl create -f fluent-bit-role.yaml
```

#### Fluent Bit to LOGIQ

The next step is to create a ConfigMap that will be used by the Fluent Bit DaemonSet:

```
$ kubectl create -f fluent-bit-config-logiq-forward.yml
```

Fluent Bit DaemonSet is ready to be used with LOGIQ on a regular Kubernetes Cluster, configure the following in deamonset `fluent-bit-daemonset-logiq-output.yml`. If you do not have your ingest token, You can generate them using [`logiqctl`](https://docs.logiq.ai/logiq-server/agentless/generating-secure-ingest-token)

*   name: LOGIQ\_HOST

    value: "YOUR\_LOGIQ\_SERVER\_IP"
*   name: CLUSTER\_ID

    value: "YOUR\_CLUSTER\_ID"
*   name: LOGIQ\_TOKEN

    value: "YOUR\_INGEST\_TOKEN"

For Kubernetes version < 1.17, please change the apiVersion: "extensions/v1beta1" from "apps/v1" and remove selector attached to DaemonSet spec selector: matchLabels: k8s-app: fluent-bit-logging

```
kubectl create -f fluent-bit-daemonset-logiq-output.yml
```

#### Enabling TLS

You can enable TLS for Fluent Bit if you'd like to secure the data transferred through Fluent Bit to LOGIQ. To do so, edit the \`fluent-bit-config-logiq-forward.yaml\` file as shown below.

```
output-logiq.conf: |
    [OUTPUT]
        Name          http
        Match         *
        Host          ${LOGIQ_HOST}
        Port          ${LOGIQ_PORT}
        URI           /v1/json_batch
        Format        json
        tls           on
        tls.verify    off
        net.keepalive off
        compress      gzip
        Header Authorization Bearer ${LOGIQ_TOKEN}
```

Be sure to also configure the following:

* name: LOGIQ\_HOST value: "YOUR\_LOGIQ\_SERVER\_IP"
* name: LOGIQ\_PORT value: "443"
* name: CLUSTER\_ID value: "YOUR\_CLUSTER\_ID"
* name: LOGIQ\_TOKEN value: "YOUR\_INGEST\_TOKEN"



