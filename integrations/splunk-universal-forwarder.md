---
description: Configuring Splunk Universal Forwarder to send data to LOGIQ
---

# Splunk Universal Forwarder

### Raw mode ( not cooked )

{% hint style="info" %}
Splunk universal forwarders support forwarding raw data as it is collected as well in Splunk's proprietary protocol S2S. LOGIQ.AI can directly ingest from Splunk UF in raw mode that does not use proprietary S2S protocol.
{% endhint %}

Splunk Universal Forwarder can be configured to send raw TCP data to LOGIQ. To enable forwarding to LOGIQ edit `$SPLUNK_HOME/etc/system/local/outputs.conf` file and enable TCP forwarding.

```
[tcpout]
disabled = false 
defaultGroup = logiq

[tcpout:logiq]
server = <logiq_instance>:<raw port>
sendCookedData=false
negotiateProtocolLevel = 0

```

### Splunk Cooked mode

LOGIQ.AI can ingest data from splunk forwarders in Cooked mode as well.  You can create a S2S Ingest app extension to directly ingest data from Splunk universal forwarder and Heavy forwarder in cooked mode.

Go to "Explore" -> "App Extensions" and create your S2S Ingest app extension

<figure><img src="../.gitbook/assets/Screen Shot 2023-01-02 at 1.20.49 PM.png" alt=""><figcaption><p>S2S Cooked mode plugin</p></figcaption></figure>

{% hint style="success" %}
Multiple S2s Ingest extensions can be running simultaneously
{% endhint %}
