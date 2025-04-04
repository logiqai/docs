---
description: Instructions for installing fluent-bit agents using Fleet.
---

# Fluent-bit Agent

* Click on the Install Agent Manager Button

<figure><img src="../../.gitbook/assets/image (203).png" alt="" width="375"><figcaption></figcaption></figure>

* Select a Platform
* And, select an Agent Type of Prometheus
* Add any optional Custom Attributes for the new agent
* Add any optional Secrets for the agent

<figure><img src="../../.gitbook/assets/Screenshot 2025-01-15 at 14-52-43 Fleet.png" alt=""><figcaption></figcaption></figure>

* Click on the Proceed button to generate the README instructions and installation script

<figure><img src="../../.gitbook/assets/Screenshot 2025-01-15 at 14-59-25 Fleet.png" alt=""><figcaption></figcaption></figure>

* The Download All button can be used to download these files
* Install the Fleet agent-manager as instructed in the README instructions

#### Check agent-manager status:

To check the status of agent-manager, and the running agents on a Linux host:

```
$ sudo systemctl status agent-manager-fluent-bit
```

To get agent-manager logs on a Linux host:

```
$ sudo journalctl -n 100 -f -u agent-manager-fluent-bit
```

To check the status of agent-manager, and the running agents on a Windows host, use the **Windows Services** app, and locate the service named **agent-manager-fluent-bit**.

To get agent-manager logs on a Windows host, use the **Windows Event Viewer** app. The logs from agent-manager will be located in the **Windows Logs > Application** logs.
