---
description: >-
  The IIS events in Microsoft Windows systems are deposited in file and ASCII
  text format.  The document describes how to install and configure fluent-bit
  to collect these events
---

# IIS Logs for on Windows

## Create IIS Config for fluent-bit

You can download an example configuration for IIS below. Please make sure to edit the config so the correct host and token is provided. Also if your IIS service is generating logs to a different path, please make sure to edit the path where the logs are located as well.

Also, make sure to edit the parsers.conf path to the folder where you installed your fluent-bit agent.

{% file src="../.gitbook/assets/fluent-bit-IIS.conf" %}

```
[SERVICE]
    Flush 1
    Parsers_file  C:\test\td-agent-bit-1.8.6-win64\conf\parsers.conf
    Log_Level error

[INPUT]
    Name              tail
    Parser            iis
    Path              C:\\inetpub\logs\\LogFiles\\W3SVC1\\u_ex*.log
    Path_Key          On
    Tag               IISW3SVC
    Buffer_Max_Size   1024k
    Read_from_Head    On

[FILTER]
    Name          record_modifier
    Match         IISW3SVC
    Record cluster_id windows
    Record namespace iis
    Record app_name IISW3SVC
    Record hostname IISHost

[OUTPUT]
    Name          http
    Match         *
    Host          <host>
    Port          443
    URI           /v1/json_batch
    Format        json
    tls           on
    tls.verify    off
    net.keepalive off
    compress      gzip
    Header Authorization Bearer <Ingest token>
```

### IIS parsers.conf

```
[PARSER]
    # http://rubular.com/r/tjUt3Awgg4
    Name iis_w3svc1
    Format regex
    Regex ^(?<timestamp>\d{4}-\d{2}-\d{2} \d{2}:\d{2}:[\d\.]+) (?<message>.*)$|^(?<raw_message>.*)$
    Time_Key    timestamp
    Time_Keep   On
    Time_Format %Y-%m-%d %H:%M:%S
```

## Installing fluent-bit

Follow the steps in the section Installing[ fluent-bit for windows](https://docs.logiq.ai/integrations/fluent-bit#fluent-bit-for-windows) to setup your fluent-bit agent and service. Use the modified config file above to match your environment during the setup process.
