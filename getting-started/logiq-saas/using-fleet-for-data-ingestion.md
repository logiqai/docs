# Using Fleet for Data Ingestion

## Quick Start Guide for Using Ascent's Fleet Management to Get Up and Running with Ingesting Metrics and Logs into Ascent.

Step 1: Install Agent Manager

Step 2: Update Configuration File

Step 3: Apply Configuration File

Step 4: Verify Metrics/Logs are being Ingested



## Step 1: From Fleet, Install Agent Manager:

Go to -> Explore -> Fleet

Click -> Install Manager

<figure><img src="../../.gitbook/assets/image (499).png" alt=""><figcaption></figcaption></figure>

Select Platform: Linux

Select  Agent Type: OpenTelemettry Collector

Click 'Proceed'

<figure><img src="../../.gitbook/assets/image (500).png" alt=""><figcaption></figcaption></figure>

Click on "Download All"

* Open 'README' file for detailed instructions.

<figure><img src="../../.gitbook/assets/image (501).png" alt=""><figcaption></figcaption></figure>

### Go to Your Linux Terminal:

NOTE: Transfer 'Fleet Installation File' to the Linux host that you will collect data from.

* make sure file has permissions to allow to 'execute'
* Execute the following command to install the Agent Manager:
* `$ sudo ./fleet-install.sh`

<figure><img src="../../.gitbook/assets/image (502).png" alt=""><figcaption></figcaption></figure>

Verify that the hostname is in the Fleet "Agents" UI tab:&#x20;

<figure><img src="../../.gitbook/assets/image (504).png" alt=""><figcaption></figcaption></figure>

Go to "Configurations" tab and search for:

* 'otelcol linux default config'

<figure><img src="../../.gitbook/assets/image (505).png" alt=""><figcaption></figcaption></figure>

Then, click into the file to open the configuration file:

<figure><img src="../../.gitbook/assets/image (507).png" alt=""><figcaption></figcaption></figure>

Copy the below code block of the Configuration file:

NOTE: You will have to insert your \[ENV\_URL\_HERE]

* Your \[ENV\_URL\_HERE] is your domain name:

<figure><img src="../../.gitbook/assets/image (508).png" alt=""><figcaption></figcaption></figure>

Copy the below code block into the "Update Configuration" section in the UI:

```
receivers:
  hostmetrics:
    collection_interval: 60s
    scrapers:
      cpu:
        metrics:
          system.cpu.utilization:
            enabled: true
      memory:
        metrics:
          system.linux.memory.available:
            enabled: true
          system.memory.utilization:
            enabled: true
      disk:
      network:
      load:
      filesystem:
        include_virtual_filesystems: true
        metrics:
          system.filesystem.inodes.usage:
            enabled: true
          system.filesystem.usage:
            enabled: true
          system.filesystem.utilization:
            enabled: true
      paging:
      processes:
  filelog:
    include:
      - /var/log/syslog
      - /var/log/auth.log
    start_at: beginning
    operators:
      - type: add
        field: attributes.log_source
        value: ubuntu
      - type: move
        from: attributes["log_source"]
        to: resource["log_source"]
processors:
  attributes/os:
    actions:
      - key: ostype
        value: "linux"
        action: upsert
  attributes/host:
    actions:
      - key: hostname
        value: "{{$ .Agent.host_name }}"
        action: upsert
  batch:
    timeout: 5s
    send_batch_size: 2048
exporters:
  debug:
    verbosity: detailed
  prometheus:
    endpoint: 0.0.0.0:9464
  otlphttp/apicametrics:
    compression: gzip
    disable_keep_alives: true
    encoding: proto
    metrics_endpoint: "{{$ .Agent.secret.otelmetrics.endpoint }}"
    headers:
      Authorization: "Bearer {{$ .Agent.secret.otellogs.token }}"
    tls:
      insecure: false
      insecure_skip_verify: true
  otlphttp:
    compression: gzip
    disable_keep_alives: true
    encoding: json
    logs_endpoint: "https://<ENV_URL_HERE>/v1/json_batch/otlplogs?namespace=Linux&application=otellogs"
    headers:
      Authorization: "Bearer {{$ .Agent.secret.otellogs.token }}"
    tls:
      insecure: false
      insecure_skip_verify: true
    sending_queue:
      queue_size: 10000
service:
  pipelines:
    metrics/out:
      receivers: [hostmetrics]
      processors: [attributes/host, attributes/os]
      exporters: [otlphttp/apicametrics]
    logs/out:
      receivers: [filelog]
      processors: [attributes/host, attributes/os, batch]
      exporters: [otlphttp]
```

NOTE: Currently, this configuration file is set up to collect syslogs. If you would like to collect different types of logs adjust the path to the logs you want to ingest:

```
   filelog:
    include:
      - /var/log/syslog
      - /var/log/auth.log
```

Copy the below code block into the "Update Configuration" section in the UI:

<figure><img src="../../.gitbook/assets/image (509).png" alt=""><figcaption></figcaption></figure>

Click "Update".

Then, go back to the "Agent" tab and click into the Linux hostname (where you'll be ingesting data from):

<figure><img src="../../.gitbook/assets/image (510).png" alt=""><figcaption></figcaption></figure>

Verify that logs are coming in and that it shows as "active":

<figure><img src="../../.gitbook/assets/image (511).png" alt=""><figcaption></figcaption></figure>

Finally, go to Explore -> 'Logs & Insights' to verify datasource is there:

<figure><img src="../../.gitbook/assets/image (512).png" alt=""><figcaption></figcaption></figure>

Optional\* click on "Source Application" where you'll be able to see your logs:

<figure><img src="../../.gitbook/assets/image (513).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (514).png" alt=""><figcaption></figcaption></figure>

