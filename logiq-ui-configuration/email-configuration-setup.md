# Email Configuration Setup

LOGIQ insights can be configured to send emails to notify alerts. It uses smtp mail and requires following information for configuration:

1. Mail Server
2. Mail Port
3. Username
4. Password
5. Default Sender

For K8S based LOGIQ insights setup, use following helm command to configure above parameters.

```text
$ helm upgrade --namespace logiq \
    --set global.environment.mail_server=<smtp server ip> \
    --set global.environment.mail_port=<port> \
    --set global.environment.mail_username=<username> \
    --set global.environment.mail_password=<password> \
    --set global.environment.mail_default_sender=<sender email id> \
     logiq logiq-repo/logiq
```

