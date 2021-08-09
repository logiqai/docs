---
description: >-
  LOGIQ server can connect to the popular agents such as logstash, rsyslog,
  fluentd. You can also use the docker syslog driver to connect directly to
  LOGIQ for your container applications
---

# Ingesting data

## Logstash

### Syslog output plugin

```text
input {

file {
    path => "/var/log/syslog"
    type => "syslog"
    start_position => "beginning"
  }

filter {
  uuid {
    target => "uuid"
  }
}

output {
  syslog { appname => "my-awesome-app"
           host => "logiq-server-dns.my-domain.com"
           protocol => "ssl-tcp"
           msgid => "%{uuid}"
           ssl_cert => "client.crt"
           ssl_key => "client.key"
           ssl_cacert => "logiq.crt"
           ssl_verify => true
           port => "7514"
           rfc => "rfc5424"
           id => "%{uuid}"
         }
  stdout { codec => rubydebug }
}
```

**NOTE**: Change _"host" , "appname", "ssl\_cert", "ssl\_key", "ssl\_cacert"_ above to suit your configuration

### HTTP output plugin

```text
output {
   http {
        url => "https://logiq-dns-or-ip/v1/json_batch"
        headers => { "Authorization" => "Bearer <Auth token>" }
        http_method => "post"
        format => "json_batch"
        content_type => "json_batch"
        pool_max => 300
        pool_max_per_route => 100
        socket_timeout => 60
       }
}
```

You can additionally control the data organization by specifying additional fields

```text
filter {
  mutate {
    add_field => { "cluster_id" => "demo-http-test" }
    add_field => { "namespace" => "namespace_name" }
    add_field => { "app_name" => "application_name" }
    add_field => { "proc_id" => "process_or_pod_identifier" }
  }
}
```

You can generate the Bearer token using [`logiqctl`](https://logiqctl.logiq.ai/get/logiqctl_get_httpingestkey/)

```text
$logiqctl get httpingestkey
```

## Rsyslogd

Please see below on how to configure Rsyslog to send to LOGIQ server. Rsyslog can send data to LOGIQ using either TCP transport or RELP transport. The RELP module for Rsyslog is called `omrelp` and for the TCP forward is called `omfwd`

{% hint style="warning" %}
LOGIQ strongly recommends sending data using the RELP transport to ensure packets are not lost or dropped. RELP relies on acknowledgements from the receiver to make sure packet is delivered. LOGIQ, for its part only sends the acknowledgements back once the data is written to persistent store.
{% endhint %}

### Using omfwd

Update the syslog config in `/etc/rsyslog.conf` or `/etc/rsyslog.d/50-default.conf`

```text
*.* action(type="omfwd"
           queue.type="LinkedList"
           action.resumeRetryCount="-1"
           queue.size="10000"
           queue.saveonshutdown="on"
           target="logiq-server-syslog-host" Port="514" Protocol="tcp"
           )
```

### Using omrelp

#### Installation rsyslog RELP modules

rsyslog is installed by default in most modern OS's, rsyslog needs the omrelp module to send data to a RELP aware endpoint such as LOGIQ. To enable RELP install packages listed below

* rsyslog-relp, enables RELP protocol for rsyslog
* rsyslog-gnutls, enables rsyslog to communicate over a secure socket

```text
sudo apt update
sudo apt install rsyslog-gnutls rsyslog-relp
```

* For Redhat/CentOS/Fedora, use yum to install

```text
yum install rsyslog-gnutls rsyslog-relp
```

#### **Configuring rsyslog \(TLS\)**

Update the syslog config in `/etc/rsyslog.conf` or `/etc/rsyslog.d/50-default.conf`

```text
module(load="omrelp")
action(type="omrelp" 
        target="logiq-server-relp-host" 
        port="2514" 
        tls="on" 
        tls.caCert="/etc/ssl/LOGIQ/certs/LOGIQ.crt" 
        tls.myCert="/etc/ssl/LOGIQ/certs/client.crt" 
        tls.myPrivKey="/etc/ssl/LOGIQ/certs/client.key" 
        tls.authMode="fingerprint"
        tls.PermittedPeer=["SHA1:BF:46:AB:9F:A3:77:46:AF:6B:D2:EC:A4:30:72:F1:CC:0E:17:C9:42"]
        action.reportSuspensionContinuation="on"
        action.resumeRetryCount="-1"
        action.resumeInterval="10"
        queue.type="fixedArray"
        queue.size="250000"
        queue.dequeueBatchSize="1024"
        queue.workerThreads="4"
        queue.workerThreadMinimumMessages="50000"
        queue.spoolDirectory="/var/log/rsyslog"
        queue.fileName="XXX_sock"
        queue.maxFileSize="16m"
        queue.maxDiskSpace="2G"
        queue.highWaterMark="200000"
        queue.lowWaterMark="100000"
        queue.checkpointInterval="30000"
        queue.saveOnShutdown="on"
        queue.timeoutEnqueue="1"
)
```

**NOTE**: Change _"target", "port", tls.caCert" , "tls.myCert", "tls.myPrivKey", "tls.PermitterPeer"_ above to suit your configuration. For non TLS config, set _"tls"_ parameter as _"off"_ and remove all tls.\* parameters from above config file. E.g. of target=ec2-34-213-110-235.us-west-2.compute.amazonaws.com

#### **Configuring rsyslog \(non-TLS\)**

Update the syslog config in `/etc/rsyslog.conf` or `/etc/rsyslog.d/50-default.conf`

{% hint style="info" %}
Rsyslog non-TLS uses port 20514 vs TLS which uses port 2514
{% endhint %}

```text
module(load="omrelp")
action(type="omrelp" 
        target="logiq-server-relp-host" 
        port="20514" 
        tls="off" 
        action.reportSuspensionContinuation="on"
        action.resumeRetryCount="-1"
        action.resumeInterval="1"
        action.resumeIntervalMax="1"
        queue.type="LinkedList"
        queue.size="25000"
        queue.dequeueBatchSize="1024"
        queue.workerThreads="4"
        queue.workerThreadMinimumMessages="60000"
        queue.saveOnShutdown="on"
        queue.timeoutEnqueue="10"
        
)
```

## Fluentd K8S

If you are running a K8S cluster, you can use fluentd to send data to the LOGIQ server. Please see below for instructions

### Managing multiple K8S clusters in a single LOGIQ instance

When deploying fluentd daemonset on K8S clusters, we recommend you use the fluentd daemon set container provided by LOGIQ. It is available at [https://hub.docker.com/repository/docker/logiqai/fluentd-remote-syslog](https://hub.docker.com/repository/docker/logiqai/fluentd-remote-syslog). It allows the administrator to pass a human readable `CLUSTER_ID` or cluster identifier with all the log data.

{% hint style="success" %}
Providing a CLUSTER\_ID allows LOGIQ to separate namespaces that may be conflicting in two separate K8S clusters.

It is also easier for the administrator to use human readable names vs LOGIQ using uuid's etc that it detects from the incoming stream.
{% endhint %}

### Running the fluentd daemonset

* Clone the repository to get the **`kubectl`** YAML files to start your daemonset

```text
git clone https://bitbucket.org/logiqcloud/client-integrations.git
```

* The files needed are under folder **`fluentd`**

```text
$ cd client-integrations/
$ cd fluentd/
$ ls -la
total 32
drwxr-xr-x  6 user  staff   192 Oct 30 14:47 .
drwxr-xr-x  7 user  staff   224 Oct 30 14:47 ..
-rw-r--r--  1 user  staff   645 Oct 30 14:47 README.md
-rw-r--r--  1 user  staff  1373 Oct 30 14:47 fluentd-logiq.yaml
-rw-r--r--  1 user  staff  1373 Oct 30 14:47 fluentd-logiq_non_tls.yaml
-rw-r--r--  1 user  staff   590 Oct 30 14:47 fluentd_rbac.yaml
-rw-r--r--  1 user  staff   210 Oct 30 14:47 secret.yaml
```

### **TLS Mode**

Edit the **`fluentd/secret.yaml`** to include your CA and Client pub/private keys in base64 encoded format

Edit the **`fluentd/fluentd-logiq.yaml`** and add your LOGIQ cluster IP/DNS. Also configure your `CLUSTER_ID` \(e.g. RC, Prod, Dev-Test, QA\).

```text
....
  - env:
        - name: SYSLOG_HOST
          value: "YOUR_LOGIQ_SERVER_IP"
        - name: CLUSTER_ID
          value: "YOUR_CLUSTER_ID"          
....
```

Run the **`kubectl`** commands to create the **`kube-logging`** namespace. You can choose a different namespace as well. In case a different namespace is used please edit the YAML files to set the correct namespace before applying them

```text
kubectl create namespace kube-logging
kubectl apply -f fluentd_rbac.yaml
kubectl apply -f secret.yaml
kubectl apply -f fluentd-logiq.yaml
```

### Non-TLS Mode

Edit the**`fluentd/fluentd-logiq_non_tls.yaml`**and add your LOGIQ cluster IP/DNS. Also configure your `CLUSTER_ID` \(e.g. RC, Prod, Dev-Test, QA\)

```text
....
  - env:
        - name: SYSLOG_HOST
          value: "YOUR_LOGIQ_SERVER_IP"
        - name: CLUSTER_ID
          value: "YOUR_CLUSTER_ID"          
....
```

Run the **`kubectl`** commands to create the **`kube-logging`** namespace. You can choose a different namespace as well. In case a different namespace is used please edit the YAML files to set the correct namespace before applying them

```text
kubectl create namespace kube-logging
kubectl apply -f fluentd_rbac.yaml
kubectl apply -f fluentd-logiq_non_tls.yaml
```

## Fluent-bit K8S

If you are running a K8S cluster, you can use fluent-bit to send data to the LOGIQ server. Please see below for instructions

### Managing multiple K8S clusters in a single LOGIQ instance

LOGIQ has provided its own fluent-bit daemon for deploying on K8S clusters. It is available at [https://bitbucket.org/logiqcloud/client-integrations/src/master/fluent-bit/](https://bitbucket.org/logiqcloud/client-integrations/src/master/fluent-bit/). It allows the administrator to pass a human readable `CLUSTER_ID` or cluster identifier with all the log data.

{% hint style="success" %}
Providing a CLUSTER\_ID allows LOGIQ to separate namespaces that may be conflicting in two separate K8S clusters.

It is also easier for the administrator to use human readable names vs LOGIQ using uuid's etc that it detects from the incoming stream.
{% endhint %}

### Running the fluent-bit daemonset

* Clone the repository to get the **`kubectl`** YAML files to start your daemonset

```text
git clone https://bitbucket.org/logiqcloud/client-integrations.git
```

* The files needed are under folder **`fluent-bit`**

```text
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

```text
$ kubectl create -f fluent-bit-config-logiq-forward.yml
```

Fluent Bit DaemonSet is ready to be used with LOGIQ on a regular Kubernetes Cluster, configure the following in deamonset fluent-bit-daemonset-logiq-output.yml.
If you do not have your ingest token, You can generate them using [`logiqctl`](https://docs.logiq.ai/logiq-server/agentless/generating-secure-ingest-token)


* name: LOGIQ\_HOST

  value: "YOUR\_LOGIQ\_SERVER\_IP"

* name: LOGIQ\_PORT

  value: "80"

* name: CLUSTER\_ID

  value: "YOUR\_CLUSTER\_ID"
  
* name: LOGIQ\_TOKEN

  value: "YOUR\_INGEST\_TOKEN"


For Kubernetes version &lt; 1.17, please change the apiVersion: "extensions/v1beta1" from "apps/v1" and remove selector attached to DaemonSet spec selector: matchLabels: k8s-app: fluent-bit-logging

```text
$ kubectl create -f fluent-bit-daemonset-logiq-output.yml
```

## Docker Syslog log driver

Using the docker syslog driver to send logs to LOGIQ is quite simple. Details about the docker syslog driver can be found here [https://docs.docker.com/config/containers/logging/syslog/](https://docs.docker.com/config/containers/logging/syslog/)

LOGIQ supports both TLS and non TLS syslog ports using TCP.

### Required values

Following fields are required options to be passed to the logdriver

* `tag` - User a human readable string for better readability otherwise the first 12 chars of the container id will be used
* `syslog-format=rfc3164`
* `syslog-address`

### Optional values

* syslog-tls-cert
* syslog-tls-key
* syslog-tls-ca-cert
* syslog-tls-skip-verify

### Using TCP and non TLS port

Sending data from docker to LOGIQ using TCP and non TLS port can be done as below. In the example below, we are going to run a mysql container and have all logs go to LOGIQ server hosted at _logiqserver-devtest.example.com_

```text
docker run --log-driver syslog \
--log-opt syslog-address=tcp://logiqserver-devtest.example.com:514 \
--log-opt syslog-format=rfc3164 --log-opt tag=mysql --name mysql3 -d mysql
```

### Using TCP and TLS port

When using to connect to LOGIQ TLS port in a secured setup, pass the client certificates to connect to the server

```text
docker run --log-driver syslog \
--log-opt syslog-address=tcp://logiqserver-devtest.example.com:514 \
--log-opt syslog-tls-cert=client.pem --log-opt syslog-tls-key=key.pem \
--log-opt syslog-tls-ca-cert=ca.pem --log-opt syslog-format=rfc3164 \
--log-opt tag=mysql --name mysql3 -d mysql
```

## Fluentd configuration

Fluentd `out-forward` Buffered Output plugin forwards events to other fluentd nodes. Logiq has the capability to act as one of the fluentd nodes.

The below code block defines the minimal changes to be added to fluentd configuration to start sending log events to flash. It is important to have the transformations while sending the data to Logiq.

```text
<source>
  @type tail
  path /var/log/*.log
  pos_file /var/log/tty.txt.pos
  <parse>
    @type none
  </parse>
</source>


<filter>
  @type record_transformer
  enable_ruby
  <record>
    hostname "#{Socket.gethostname}"
    namespace "#{Socket.gethostname}"
    cluster_id "hadoop-master"
    log ${record["message"]}
  </record>
</filter>



<match>
  @type forward
  send_timeout 10s
  recover_wait 10s
  hard_timeout 20s


<format>
  @type msgpack
  time_type unixtime
  utc
 </format>
  <buffer time,tag,message>
    @type memory
    timekey 2s
    timekey_wait 1s
    flush_mode interval
    flush_interval 1s
    retry_max_interval 2s
    retry_timeout 10s
  </buffer>


  <server>
    name logiq
    host development.logiq.ai
    port 24224
    weight 100
  </server>

   <secondary>
    @type secondary_file
    directory /var/log/forward-failed
  </secondary>
</match>
```

## Fluent-bit configuration

_Forward_ is the protocol used by [Fluentd](http://www.fluentd.org) to route messages between peers. The **forward** output plugin allows to provide interoperability between compatible systems, Logiq being one.

The below code block defines the minimal changes to be added to the fluent-bit configuration using the http plugin to start sending log events to flash.

```text
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

