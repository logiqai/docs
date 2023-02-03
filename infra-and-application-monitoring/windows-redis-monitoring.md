# Windows Redis Monitoring

To monitor a Redis server running on a Windows machine, you can use a combination of Windows Exporter and Prometheus to send metrics to LOGIQ.AI.

This script will help you setup Redis Exporter as a service on a 64-bit Windows Machine and it requires two arguments:

* **PROMETHEUS\_CONFIG\_PATH**: the path to the Prometheus configuration file.
* **NSSM\_PATH**: the path of nssm.exe

Before running the PowerShell script, make sure you have `NSSM` and `Prometheus` installed.&#x20;

To run the PowerShell script, open an administrator PowerShell and run the following command:

{% file src="../.gitbook/assets/redis-exporter-installer.ps1" %}
Powershell script to setup Redis Exporter
{% endfile %}

```
.\redis-exporter-installer.ps1 -NSSM_PATH "<NSSM-path>" -PROMETHEUS_CONFIG_PATH "<Prometheus-configuration-path>"
```
