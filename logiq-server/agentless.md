---
description: >-
  LOGIQ server can connect to the popular agents such as logstash, rsyslog,
  fluentd. You can also use the docker syslog driver to connect directly to
  LOGIQ for your container applications
---

# Ingesting data

## Logstash

### Configuring Logstash

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
* rsyslog-gnutls, enables rsyslog to communicate over secure socket

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

## Fluentd K8S

If you are running a K8S cluster, you can use fluentd to send data to the LOGIQ server. Please see below for instructions

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

Edit the **`fluentd/fluentd-logiq.yaml`** and add your LOGIQ cluster IP/DNS. Also configure your Cluster Id \(e.g. RC, Prod, Dev-Test, QA\)

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

Edit the**`fluentd/fluentd-logiq_non_tls.yaml`**and add your LOGIQ cluster IP/DNS. Also configure your Cluster Id \(e.g. RC, Prod, Dev-Test, QA\)

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

## Docker Syslog log driver 

Using the docker syslog driver to send logs to LOGIQ is quite simple. Details about the docker syslog driver can be found here [https://docs.docker.com/config/containers/logging/syslog/](https://docs.docker.com/config/containers/logging/syslog/)

LOGIQ supports both TLS and non TLS syslog ports using TCP.

### Required values

Following fields are required options to be passed to the logdriver

* `tag` - User a human readable string for better readability otherwise the first 12 chars of the container id will be used
* `syslog-format=rfc5424`
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
--log-opt syslog-format=rfc5424 --log-opt tag=mysql --name mysql3 -d mysql
```

### Using TCP and TLS port

When using to connect to LOGIQ TLS port in a secured setup, pass the client certificates to connect to the server

```text
docker run --log-driver syslog \
--log-opt syslog-address=tcp://logiqserver-devtest.example.com:514 \
--log-opt syslog-tls-cert=client.pem --log-opt syslog-tls-key=key.pem \
--log-opt syslog-tls-ca-cert=ca.pem --log-opt syslog-format=rfc5424 \
--log-opt tag=mysql --name mysql3 -d mysql
```



