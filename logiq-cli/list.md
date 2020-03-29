---
description: This page documents command-line usage for the List command
---

# List

## Help

```bash
#./logiqbox ls -h
NAME:
   logiqbox list - List of applications that you can tail

USAGE:
   logiqbox list [command options] [arguments...]

OPTIONS:
   --namespaces  -namespaces (default: false)
   --help, -h    show help (default: false)
```

## List All applications

_**logiqbox**_ cli provides the ls command to show the list of applications from which logs have been ingested. In the below example we see 3 different applications have sent log data from two namespaces

```bash
#./logiqbox ls
Host             | Namespace       | Application     | ProcId
pool-1-5d4f3e6a-8nln | wordpress       | mysql_wordpress | wordpress-
pool-1-d498bffb-njv1 | wordpress       | mysql           | mysql-5d9f966696-slmft
pool-1-7d00dbc2-mfl6 | redis           | redis           | redis-5d9f966696-slmft
```

## Filter by Namespace

Using thee --namespaces filter, one can restrict the application listing for one or more namespaces only

```bash
#./logiqbox ls --namespaces kube-logging
Host             | Namespace       | Application      | ProcId
pool-1-d498bffb-njv1 | kube-logging     | fluentd          | fluentd-7z2jv
pool-1-7d00dbc2-mfl6 | kube-logging     | fluentd          | fluentd-kdztz
pool-1-5d4f3e6a-8nln | kube-logging     | fluentd          | fluentd-lhwg2
```

