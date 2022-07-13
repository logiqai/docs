# Fluent Bit

## Fluent Bit configuration

_HTTP_ output plugin allows flushing your records into an HTTP endpoint. The **HTTP** output plugin allows to provide interoperability between compatible systems, Logiq being one.

The below code block defines the minimal changes to be added to the fluent-bit configuration using the HTTP plugin to start sending log events to flash.

```
[SERVICE]
    Flush        1
    Parsers_File /etc/td-agent-bit/parsers.conf
    Log_Level    error
    
[INPUT]
    Name              tail
    Path              /var/log/*
    Path_Key          On
    Tag               logiq
    Buffer_Max_Size   1024k
    Read_from_Head    On
    Mem_Buf_Limit     1MB

[FILTER]
    Name          record_modifier
    Match         logiq
    Record cluster_id flash

[FILTER]
    Name          record_modifier
    Match         logiq
    Record namespace mesos

[FILTER]
    Name          record_modifier
    Match         logiq
    Record app_name fluentbit


[OUTPUT]
    Name          http
    Match         *
    Host          localhost
    Port          80
    URI           /v1/json_batch
    Format        json
    tls           off
    tls.verify    off
    net.keepalive off
    compress      gzip
    Header Authorization Bearer ${LOGIQ_TOKEN}
```

## Fluent Bit for Windows

You can use Fluent Bit to ship Windows logs to LOGIQ by leveraging the following Fluent Bit configuration.

The instruction to install fluent-bit for windows is available at the following git repository - [<mark style="color:blue;">https://github.com/logiqai/logiq-installation/tree/main/fluent-bit/windows</mark>](https://github.com/logiqai/logiq-installation/tree/main/fluent-bit/windows)<mark style="color:blue;"></mark>

The folder in the git repository includes a PowerShell script to set up the windows fluent-bit agent. The PowerShell script downloads the fluent-bit agent and installs the agent as a service. Continue below to see how to set up an example fluent conf and start service on windows.

{% hint style="info" %}
NOTE: You will need to finalize the fluent configuration and then restart the service. Below is an example of fluent configuration
{% endhint %}

```
[SERVICE]
    Flush           1
    Daemon          yes
    Log_Level       info


[FILTER]
    Name          record_modifier
    Match         *
    Record namespace Windows 

[FILTER]
    Name modify
    Match *
    Rename SourceName AppName
    Rename ComputerName Hostname


[INPUT]
    Name                   winlog
    Channels               Setup,Windows PowerShell,Security
    Tag                    Windows-events
    Interval_Sec           5



[OUTPUT]
    name                   http
    match                  *
    host                   Logiq-Hostname
    port                   443
    URI                    /v1/json_batch
    Format                 json
    tls                    on
    tls.verify             off
    net.keepalive          off
    compress               gzip
    Header Authorization Bearer <token>
```

To forward Windows logs to LOGIQ using Fluent Bit, do the following.&#x20;

1. Copy the configuration provided above and save it locally in a temporary folder.&#x20;
2. Edit the fields in the `[OUTPUT]` section of the configuration file to match your LOGIQ instance.&#x20;
3. Clone the LOGIQ installation GitHub repository locally and navigate to the `windows` folder.
4. Copy and paste the `fluent-install.ps1` script into the folder where you saved the Fluent Bit configuration file.&#x20;
5.  Since Windows does not allow you to execute scripts due to default PowerShell script execution policies, you should update the set execution policy by running:&#x20;

    ```
    Set-ExecutionPolicy unrestricted
    ```
6. Navigate to **Windows** > **PowerShell** and run it in Administrator mode.&#x20;
7.  Execute the `fluent-install.ps1` script, as shown in the following example:

    ```
    PS D:\test> .\fluentbit-install.ps1
    [SC] CreateService SUCCESS
    The fluent-bit service is starting.
    The fluent-bit service was started successfully.
    ```
8. Navigate to **Windows** > **Run**. &#x20;
9. Type `services.msc` and hit Enter.&#x20;

You'll now see a Fluent Bit service running on your Windows machine.&#x20;



