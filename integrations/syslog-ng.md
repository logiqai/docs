---
description: >-
  Syslog-ng is a free and open-source implementation of the Syslog protocol, an
  enhanced log daemon, supporting a wide range of input and output methods:
  Syslog, unstructured text, queueing, SQL & NoSQL
---

# Syslog-ng

### Installation of Syslog-ng

To install Syslog-ng on your system, please refer to the official git repo given below

{% embed url="https://github.com/syslog-ng/syslog-ng" %}

### Configuration of Syslog-ng

LOGIQ supports data ingestion from Syslog-ng. The following instructions describe the steps for configuring log forwarding from Syslog-ng to LOGIQ by modifying the Syslog-ng configuration file.&#x20;

**Syslog-ng** supports both TCP and UDP protocols, LOGIQ only supports ingestion of logs over TCP protocol to ensure packets are not lost or dropped. TCP relies on acknowledgments from the receiver to make sure the packet is delivered.

LOGIQ.AI hosts the syslog protocol at port **514.** The ports are configurable and can be changed if needed. Additonal port for TLS is available at **7514**

### **INPUT**

The below configuration typically sends all system and internal logs, such as sshd, systemd, NetworkManager

```
@version: 3.36
@include "scl.conf"

options {
    time-reap(30);
    mark-freq(10);
    keep-hostname(yes);
    chain-hostnames(no);
};

source s_local {
       system();
       internal();
};
```

The below configuration accepts system logs from /dev/log (from applications or forwarded by systemd) and writes everything to a single file.

```
@version: 3.36
@include "scl.conf"

log {
	source { system(); };
	destination { file("/var/log/syslog"); };
};
```

### OUTPUT

LOGIQ.AI supports multiple way to ingest data via standard interfaces. With syslog-ng you can use the built-in syslog, http output destinations to push data to LOGIQ.AI. We however recommend using LOGIQ.AI's python destination for syslog-ng driver as it provides most capabilities and control over pushing you data at scale.

### Python syslog-ng destination for LOGIQ.AI

The syslog-ng python destination driver for LOGIQ.AI is avalable as a python package and can be installed via pip. To enable the python destination support, first install the python destination support for syslog-ng. Below is an example of how to do this on an ubuntu system.&#x20;

```
apt-get install syslog-ng-mod-python
```

You can refer to the syslog-ng website for other operating systems. You can now proceed to install the LOGIQ.AI driver next. This assumes you have python3 installed. More details on the LOGIQ.AI driver can be found at [https://pypi.org/project/logiqaidstsyslogng/](https://pypi.org/project/logiqaidstsyslogng/)

```
pip install --upgrade logiqaidstsyslogng
```

#### Creating a logiq.conf for the driver

A _logiq.conf_ is required that provides details of the LOGIA.AI instance and how to connect to it. Please note down the path where you save the config as we will need it to configure the destination in syslog-ng.conf. We recommend you store it in _/etc/syslog-ng/logiq.conf_ along with rest of the syslog-ng configruation files.

{% code title="logiq.conf" overflow="wrap" lineNumbers="true" %}
```systemd
[logiq]
# Host or IP for LOGIQ.AI
host = my-logiq-cluster.example.com
# Protocol https
protocol = https
# API Ingest token
key = <JWT Token>
# destination reachability timeout in seconds
timeout = 5
```
{% endcode %}

#### Creating a syslog-ng destination for LOGIQ.AI

You are now ready to update your syslog-ng conf to add a LOGIQ.AI python destination

{% code title="syslog-ng.conf" overflow="wrap" lineNumbers="true" %}
```

destination d_logiq {
    python(
        batch-timeout(500)
        batch-lines(400)
        class("logiqaidstsyslogng.LogDestination")
        value-pairs(
          key(ISODATE)
          scope(rfc5424 nv-pairs)
        )
        options(config "/etc/syslog-ng/logiq.conf")
        options(workers-batch 8)
        options(worker-batch-lines 25)
        options(loglevel WARN)
    );
};

# Connect the source to the logiq destination
log { source(s_local); destination(d_logiq); };
```
{% endcode %}

{% hint style="info" %}
LOGIQ.AI only works with RFC3339/ISO8601 time stamps so the python destination must add the ISODATE key which will be sent as timestamp.

The scope for value-pairs also needs to contain rfc5424 so we can pull out all the standard syslog fields such as host, application, pid, sdata etc.
{% endhint %}

The python destination provides some usefule options as described below

| Name          | Values                                                                         | Default | Notes                                                                                                       |
| ------------- | ------------------------------------------------------------------------------ | ------- | ----------------------------------------------------------------------------------------------------------- |
| batch-timeout | e.g. 500 (milliseconds)                                                        | NA      | Refer to syslog-ng documentation. This allows for batching logs                                             |
| batch-lines   | e.g. 400                                                                       | NA      | Refer to syslog-ng documentation. This limits the max batch size allowed before python plugin calls a flush |
| class         | <pre data-overflow="wrap"><code>logiqaidstsyslogng.LogDestination</code></pre> | NA      | Specifies the LOGIQ.AI python driver class to load                                                          |

The LOGIQ.AI driver provides various options as described below

| Option Name        | Values                         | Default | Notes                                                                                                   |
| ------------------ | ------------------------------ | ------- | ------------------------------------------------------------------------------------------------------- |
| config             | e.g. /etc/syslog-ng/logiq.conf | None    | Location of logiq.conf file                                                                             |
| workers-batch      | e.g. 8/16                      | 1       | Number of workers, more workers allow more parallelism when pushing to a loadbalanced LOGIQ.AI endpoint |
| worker-batch-lines | e.g. 25                        | 25      | How many maximum log events are batched per worker                                                      |
| loglevel           | e.g. INFO/WARN/ERROR/DEBUG     | INFO    | Debug level. Logs are sent to /var/log/logiqaidstsyslogns                                               |
| debug              | true/false                     | false   | Prints additional debug including log event to the log file                                             |
| namespace-key      | e.g. HOST                      | Not set | Which key from log event maps to namespace                                                              |
| application-key    | e.g. PROGRAM                   | Not set | Which key from log event maps to application                                                            |
| cluster-key        | e.g. HOST                      | Not set | Which key from log event maps to cluster/group identifier                                               |

### Organizing data in LOGIQ.AI

Data in the LOGIQ.AI gets organized as flows. A flow consists of a Namespace, an application name and one or more subflows or ProcId's. This allows mapping most legacy and cloud native environments in LOGIQ.AI with minimal configuration

{% hint style="info" %}
Please set namespace, application and cluster\_id mappings in syslogn-ng.conf. If this is not configured, default mappings will be used.
{% endhint %}

### Additional output methods

{% hint style="danger" %}
Additional methods to push data via syslog-ng are documented below but are not recommended for production and scale use.
{% endhint %}

#### OUTPUT (**non-TLS)**

The below configuration describes how logs are sent to LOGIQ over non-TLS protocol using **syslog()** driver

```
destination d_network {
    syslog("<logiq-endpoint>" 
    transport("tcp") 
    port(514));
};


log {
    source(s_local); 
    destination(d_network);
};
```

#### OUTPUT (TLS)

The below configuration forwards logs over TLS to LOGIQ over non-TLS protocol using **syslog()** driver

```
destination d_syslog_tls {
    syslog("<logiq-endpoint>"
        transport("tls")
        port(7514)
        tls(peer-verify(required-trusted)
            ca-dir('/opt/syslog-ng/etc/syslog-ng/keys/ca.d/')
            key-file('/opt/syslog-ng/etc/syslog-ng/keys/client_key.pem')
            cert-file('/opt/syslog-ng/etc/syslog-ng/keys/client_certificate.pem')
        )
    );
};
```



#### Example (non-TLS)

The below configuration shows the full configuration of how Syslog-ng forwards logs over non-TLS protocol using **syslog()** driver

```
@version: 3.36
@include "scl.conf"

options {
    time-reap(30);
    mark-freq(10);
    keep-hostname(yes);
    chain-hostnames(no);
};

source s_local {
       system();
       internal();
};

destination d_network {
    syslog("<logiq-endpoint>" 
    transport("tcp") 
    port(514));
};


log {
    source(s_local); 
    destination(d_network);
};

```

#### OUTPUT http/https

{% hint style="danger" %}
NOTE: The payload in ${MSG} and other fields that come from syslog-ng variable need to be escaped properly, otherwise they will be rejeced with a 400 error.

Below example shows how to construct a body
{% endhint %}

With http/https publish, the following are mandatory

* Ingest token
* namespace
* @timestamp
* application\_name
* cluster\_id
* hostname

In addition to the fields above, arbitrary json attributes can be provided. Nested JSON will automatically get flattened.

Example config below. Please modify relevant fields such as cluster\__id, namespace, application\_name before sending data_

```javascript
destination d_logiq {
    http(url("https://<logiq dns or ip>/v1/json")
        method("POST")
        peer-verify(no)
        headers("Content-Type: application/json")
        headers("Authorization: Bearer <ingest token goes here>")
        body("{ \"@timestamp\": \"${ISODATE}\",
                \"hostname\": \"${HOST}\",
                \"namespace\": \"syslogng-test-logs\",
                \"message\": \"${MSG}\",
                \"application_name\": \"${PROGRAM}\",
                \"proc_id\": \"${PID}\",
                \"cluster_id\": \"logiq-cluster-1\",
                \"severity\": \"${LEVEL}\",
                \"sourcetype\": \"mysourcetype2\"
              }")
    );
};
```

For more information please refer Syslog-ng documentation
