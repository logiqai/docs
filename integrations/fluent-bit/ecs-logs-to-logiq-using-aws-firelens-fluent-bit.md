# ECS logs to Logiq using AWS Firelens (Fluent-bit)

[Amazon Web Services (AWS) Fargate](http://amazon%20web%20services%20%28aws%29%20fargate/) is a serverless compute engine for containers that works on Amazon ECS and EKS. AWS FireLens is a log routing agent built for ECS containers and enables administrators to use task definition attributes to route logs to external log aggregators. AWS FireLens unifies data collection across the ECS cluster, and its pluggable architecture allows adding data sources, parsers, filters/buffering, and output plugins.

### Configuring AWS FireLens to forward logs <a href="#1-configuring-aws-firelens-to-forward-logs" id="1-configuring-aws-firelens-to-forward-logs"></a>

Possibly the most significant advantage with AWS FireLens is that you can connect it to almost any service endpoint as long as data sinks can process general-purpose JSON over HTTP, FluentForward, or TCP protocols. FireLens magically transforms log outputs of ECS containers and generates the routing configuration needed for sending logs to the logging service.&#x20;

The **“awsfirelens**” log driver allows you to specify Fluentd or Fluent Bit output plugin configurations. Your application container logs are routed to a sidecar or independent Firelens container inside your cluster, which further routes your container logs to their destination as defined in your task **“logConfiguration**“. Additionally, you can use the options field of the \`FireLensConfiguration\` object in the task definition to serve any advanced use case.

Go to the task definition that you need logs to be sent to Logiq from, click on "Edit container", navigate to the "STORAGE AND LOGGING" section

![](<../../.gitbook/assets/image (22).png>)

by default, the container will be sending logs to CloudWatch, Uncheck the "Auto configure to CloudWatch Logs", choose Log driver as "awsfirelens" and the below variables in the "Log options" section.

![](<../../.gitbook/assets/image (23).png>)

Below are the mandatory fields that need to be passed, in order to forward logs to Logiq

```
    Name     http
    Match    *
    Host     
    Port     443 
    URI      /v1/json_batch
    Format   json
    tls      on
    tls.verify  off
    net.keepalive  off
    compress      gzip
    Header Authorization Bearer
```

After saving the container definition, In the Log Router integration section, you should see, "Enable FireLens integration Type" as checked and show you the image which will be used (might differ as per region).

![](<../../.gitbook/assets/image (19).png>)

If you are using the "Configure via JSON" option, in the container definition section, add the below.

```
        {
            "dnsSearchDomains": null,
            "environmentFiles": null,
            "logConfiguration": {
                "logDriver": "awsfirelens",
                "secretOptions": null,
                "options": {
                    "tls.verify": "off",
                    "net.keepalive": "off",
                    "Format": "json",
                    "compress": "gzip",
                    "Port": "443",
                    "match": "*",
                    "Header Authorization Bearer": "<LOGIQ-TOKEN>",
                    "Host": "<LOGIQ-ENDPOINT>",
                    "tls": "on",
                    "URI": "/v1/json_batch",
                    "Name": "http"
                }
            }
```

Once you are done with the setup, you should see a logrouter container along with your container(wordpress below).

![](<../../.gitbook/assets/image (15).png>)

You should see logs on Logiq UI, "Namespace" will be mapped to ECS Cluster name and "Application" will be the task-definition name.&#x20;

![](<../../.gitbook/assets/image (18).png>)



If you have custom parsers that need to be included in the fluent bit configuration, you will need a custom fluent-bit image, refer [https://www.logiq.ai/monitoring-ecs-fargate-logs-with-firelens-and-logiq/](https://www.logiq.ai/monitoring-ecs-fargate-logs-with-firelens-and-logiq/)
