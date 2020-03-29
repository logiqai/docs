---
description: This page documents command-line usage for the Tail command
---

# Tail

## Help

```text
NAME:
   logiqbox tail - tail logs filtered by namespace, application, labels or process / pod name

USAGE:
   logiqbox tail [command options] [-apps application names and/or -namespaces K8S namespace names and/or -labels K8S labels - procs process id / pod name]

OPTIONS:
   --namespaces  -namespaces (default: false)
   --labels      -labels (default: false)
   --apps        -apps (default: false)
   --process     -procs (default: false)
   --help, -h    show help (default: false)
```

## Tail logs for an application

_**logiqbox**_ tailing allows a user to narrow down the logs to a smaller set of applications that the user is interested in and shows the logs from the requested application in the current live logs streaming into the server. 

Tailing does not return historical data. For historical data, please see the [Query](query.md) section

```text
#./logiqbox tail --apps redis
Crunching data for you...
timestamp|severity_string|hostname|source_ip|proc_id|app_name|facility_string|message
2019-12-12T23:57:31Z             |info  |docker-desktop|10.0.1.22|1405 |redis|system daemon|1:C 12 Dec 2019 23:57:31.618 # oO0OoO0OoO0Oo Redis is starting oO0OoO0OoO0Oo
2019-12-12T23:57:31Z             |info  |docker-desktop|10.0.1.22|1405 |redis|system daemon|1:C 12 Dec 2019 23:57:31.618 # Redis version=5.0.7, bits=64, commit=00000000, modified=0, pid=1, just started
2019-12-12T23:57:31Z             |info  |docker-desktop|10.0.1.22|1405 |redis|system daemon|1:C 12 Dec 2019 23:57:31.618 # Warning: no config file specified, using the default config. In order to specify a config file use redis-server /path/to/redis.conf
2019-12-12T23:57:31Z             |info  |docker-desktop|10.0.1.22|1405 |redis|system daemon|1:M 12 Dec 2019 23:57:31.619 # WARNING: The TCP backlog setting of 511 cannot be enforced because /proc/sys/net/core/somaxconn is set to the lower value of 128.
2019-12-12T23:57:31Z             |info  |docker-desktop|10.0.1.22|1405 |redis|system daemon|1:M 12 Dec 2019 23:57:31.619 * Ready to accept connections
2019-12-12T23:57:31Z             |info  |docker-desktop|10.0.1.22|1405 |redis|system daemon|1:M 12 Dec 2019 23:57:31.619 * Running mode=standalone, port=6379.
2019-12-12T23:57:31Z             |info  |docker-desktop|10.0.1.22|1405 |redis|system daemon|1:M 12 Dec 2019 23:57:31.619 # WARNING you have Transparent Huge Pages (THP) support enabled in your kernel. This will create latency and memory usage issues with Redis. To fix this issue run the command 'echo never > /sys/kernel/mm/transparent_hugepage/enabled' as root, and add it to your /etc/rc.local in order to retain the setting after a reboot. Redis must be restarted after THP is disabled.
2019-12-12T23:57:31Z             |info  |docker-desktop|10.0.1.22|1405 |redis|system daemon|1:M 12 Dec 2019 23:57:31.619 # Server initialized
```

## Tail logs for namespaces

```text
#./logiqbox tail --namespaces redis
Crunching data for you...
timestamp|severity_string|hostname|source_ip|proc_id|app_name|facility_string|message
2019-12-12T23:57:31Z             |info  |docker-desktop|10.0.1.22|1405 |redis|system daemon|1:C 12 Dec 2019 23:57:31.618 # oO0OoO0OoO0Oo Redis is starting oO0OoO0OoO0Oo
2019-12-12T23:57:31Z             |info  |docker-desktop|10.0.1.22|1405 |redis|system daemon|1:C 12 Dec 2019 23:57:31.618 # Redis version=5.0.7, bits=64, commit=00000000, modified=0, pid=1, just started
2019-12-12T23:57:31Z             |info  |docker-desktop|10.0.1.22|1405 |redis|system daemon|1:C 12 Dec 2019 23:57:31.618 # Warning: no config file specified, using the default config. In order to specify a config file use redis-server /path/to/redis.conf
2019-12-12T23:57:31Z             |info  |docker-desktop|10.0.1.22|1405 |redis|system daemon|1:M 12 Dec 2019 23:57:31.619 # WARNING: The TCP backlog setting of 511 cannot be enforced because /proc/sys/net/core/somaxconn is set to the lower value of 128.
2019-12-12T23:57:31Z             |info  |docker-desktop|10.0.1.22|1405 |redis|system daemon|1:M 12 Dec 2019 23:57:31.619 * Ready to accept connections
2019-12-12T23:57:31Z             |info  |docker-desktop|10.0.1.22|1405 |redis|system daemon|1:M 12 Dec 2019 23:57:31.619 * Running mode=standalone, port=6379.
2019-12-12T23:57:31Z             |info  |docker-desktop|10.0.1.22|1405 |redis|system daemon|1:M 12 Dec 2019 23:57:31.619 # WARNING you have Transparent Huge Pages (THP) support enabled in your kernel. This will create latency and memory usage issues with Redis. To fix this issue run the command 'echo never > /sys/kernel/mm/transparent_hugepage/enabled' as root, and add it to your /etc/rc.local in order to retain the setting after a reboot. Redis must be restarted after THP is disabled.
2019-12-12T23:57:31Z             |info  |docker-desktop|10.0.1.22|1405 |redis|system daemon|1:M 12 Dec 2019 23:57:31.619 # Server initialized
```

## Tail logs by K8S labels

If you are pushing data from a Kubernetes environment , you can tail logs by kubernetes label match. This applies to all resources that have the label applied

```text
#./logiqbox tail --labels app:redis
Crunching data for you...
timestamp|severity_string|hostname|source_ip|proc_id|app_name|facility_string|message
2019-12-12T23:57:31Z             |info  |docker-desktop|10.0.1.22|1405 |redis|system daemon|1:C 12 Dec 2019 23:57:31.618 # oO0OoO0OoO0Oo Redis is starting oO0OoO0OoO0Oo
2019-12-12T23:57:31Z             |info  |docker-desktop|10.0.1.22|1405 |redis|system daemon|1:C 12 Dec 2019 23:57:31.618 # Redis version=5.0.7, bits=64, commit=00000000, modified=0, pid=1, just started
2019-12-12T23:57:31Z             |info  |docker-desktop|10.0.1.22|1405 |redis|system daemon|1:C 12 Dec 2019 23:57:31.618 # Warning: no config file specified, using the default config. In order to specify a config file use redis-server /path/to/redis.conf
2019-12-12T23:57:31Z             |info  |docker-desktop|10.0.1.22|1405 |redis|system daemon|1:M 12 Dec 2019 23:57:31.619 # WARNING: The TCP backlog setting of 511 cannot be enforced because /proc/sys/net/core/somaxconn is set to the lower value of 128.
2019-12-12T23:57:31Z             |info  |docker-desktop|10.0.1.22|1405 |redis|system daemon|1:M 12 Dec 2019 23:57:31.619 * Ready to accept connections
2019-12-12T23:57:31Z             |info  |docker-desktop|10.0.1.22|1405 |redis|system daemon|1:M 12 Dec 2019 23:57:31.619 * Running mode=standalone, port=6379.
2019-12-12T23:57:31Z             |info  |docker-desktop|10.0.1.22|1405 |redis|system daemon|1:M 12 Dec 2019 23:57:31.619 # WARNING you have Transparent Huge Pages (THP) support enabled in your kernel. This will create latency and memory usage issues with Redis. To fix this issue run the command 'echo never > /sys/kernel/mm/transparent_hugepage/enabled' as root, and add it to your /etc/rc.local in order to retain the setting after a reboot. Redis must be restarted after THP is disabled.
2019-12-12T23:57:31Z             |info  |docker-desktop|10.0.1.22|1405 |redis|system daemon|1:M 12 Dec 2019 23:57:31.619 # Server initialized
```

