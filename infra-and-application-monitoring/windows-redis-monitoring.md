# Windows Redis Monitoring

To monitor a Redis server running on a Windows machine, you can use a combination of Windows Exporter and Prometheus to send metrics to LOGIQ.AI.

Before running the PowerShell script, make sure you have NSSM and Prometheus installed. The script is used to start the Redis Exporter as a service and requires two arguments:

* NSSM\_PATH: the path of nssm.exe
* PROMETHEUS\_CONFIG\_PATH: the path to the Prometheus configuration file.

To run the PowerShell script, open an administrator PowerShell and run the following command:

{% file src="../.gitbook/assets/redis-exporter-installer.ps1" %}

This script has 2 requirements:

* Path of `nssm.exe`
* Path to `prometheus.conf` file.

```
.\redis-exporter-installer.ps1 -NSSM_PATH "<NSSM-path>" -PROMETHEUS_CONFIG_PATH "<Prometheus-configuration-path>"
```
