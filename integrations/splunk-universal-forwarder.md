---
description: Configuring Splunk Universal Forwarder to send data to LOGIQ
---

# Splunk Universal Forwarder

Splunk Universal Forwarder can be configured to send raw TCP data to LOGIQ. To enable forwarding to LOGIQ edit `$SPLUNK_HOME/etc/system/local/outputs.conf` file and enable TCP forwarding.

```
[tcpout]
disabled = false 
defaultGroup = logiq

[tcpout:logiq]
server = <logiq_instance>:<port>
sendCookedData=false
negotiateProtocolLevel = 0

```
