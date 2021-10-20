# Minimal server configuration

## Creating a minimal configuration

LOGIQ server needs a configuration file that describes how to handle incoming data and where to store it. See below for a minimal configuration to get started. In the below example we are connecting LOGIQ to ingest data into an AWS backed S3 compatible store. The data stored will be partitioned by day.

NOTE: Change the below config to work with your environment. If you are using AWS deployment using CloudFormation, the config file is automatically generated during the install. If you are using a Kubernetes cluster to run LOGIQ, the configuration is passed as a config map.

```
options:
    ca: "/etc/ssl/logiq/certs/logIQ.crt"
    cert: "/etc/ssl/logiq/certs/logiq-server.crt"
    key: "/etc/ssl/logiq/certs/logiq-server.key"
    host: 0.0.0.0
credentials:
  -
    name: aws_logging_bucket
    s3:
      secret_key: logiq_secret
      access_key: logiq_access 
partitions:
  -
    name: p_by_day
    fields:
      - year
      - month
      - day      
destinations:
  -
    name: default_log_store
    partition: p_by_day
    s3:
      bucket: logiq-bucket-1fbc-1
      region: us-east-1
      credential: aws_logging_bucket
rules:
  -
    destination: default_log_store          
```

The above configuration defines a simple rule that all incoming data needs to go to the destination _default\_log\_store_.

See the section on [_LOGIQ server configuration_](terminology.md) on additional configuration options.
