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

**Syslog-ng** supports both TCP and UDP protocols, LOGIQ recommends ingestion of logs over TCP protocol to ensure packets are not lost or dropped. TCP relies on acknowledgments from the receiver to make sure the packet is delivered.

LOGIQ.AI hosts the lumberjack protocol at port **514.** The ports are configurable and can be changed if needed.

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

### OUTPUT (**non-TLS)**

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

### OUTPUT (TLS)

The below configuration forwards logs over TLS to LOGIQ over non-TLS protocol using **syslog()** driver

```
destination d_syslog_tls {
    syslog("<logiq-endpoint>"
        transport("tls")
        port(2514)
        tls(peer-verify(required-trusted)
            ca-dir('/opt/syslog-ng/etc/syslog-ng/keys/ca.d/')
            key-file('/opt/syslog-ng/etc/syslog-ng/keys/client_key.pem')
            cert-file('/opt/syslog-ng/etc/syslog-ng/keys/client_certificate.pem')
        )
    );
};
```



### Example (non-TLS)

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
    port(26514));
};


log {
    source(s_local); 
    destination(d_network);
};

```

For more information please refer Syslog-ng documentation
