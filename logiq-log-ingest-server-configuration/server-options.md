# Server options

## Options

The options section in the LOGIQ configuration file is for changing default server parameters. Below are the commonly used options for typical deployments. Options can be either specified as quoted strings / non-quoted e.g. "2514" or 2514

### ca \[optional\]

CA Certificate file path

### cert \[optional\]

Server Certificate file path

### host \[optional\]

Host IP's which server binds to - default is 0.0.0.0

### key \[optional\]

Server certificate key

### relp\_port \[optional\]

The RELP port where server listens for RELP connection. Default port is _**20514**_

### **relp\_port\_tls** \[optional\]

The RELP port where server listens for RELP connection. Default port is _**2514**_

### syslog\_port \[optional\]

The syslog port where server listens for syslog connection. Default port is _**514**_

### **syslog\_port\_tls** \[optional\]

The syslog port where server listens for syslog connection. Default port is _**7514**_

### cli\_port \[optional\]

The port where the LOGIQ CLI is accessed. Default port is _**9998**_

### cli\_user \[optional\]

Login for LOGIQ CLI console

### cli\_password \[optional\]

Password for LOGIQ CLI console

### glue\_iam\_service\_role \[optional\]

ARN of the glue service role. See [here](../running-on-aws/aws-iam-resources.md#iam-service-role-for-glue) for more details. This only applies if you are trying to run LOGIQ in AWS.

## Example

options:

```yaml
    ca: "/etc/ssl/logiq/certs/logIQ.crt"
    cert: "/etc/ssl/logiq/certs/syslog.crt"
    host: 0.0.0.0
    key: "/etc/ssl/logiq/certs/syslog.key"
    relp_port_tls: "2514"
    relp_port: "20514"
    cli_port : "9998"
    syslog_port_tls: "7514"
    syslog_port: "514"
    cli_user : "logiq_access"
    cli_password : "logiq_secret"
    glue_iam_service_role: "arn:aws:iam::199500300922:role/LogIQ-Glue_role"
```

