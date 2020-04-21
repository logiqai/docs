---
description: This page documents command-line usage for the List command
---

# List

## Help

```bash
#./logiqctl ls -h
NAME:
   logiqctl list - List of applications that you can tail

USAGE:
   logiqctl list [command options] [arguments...]

OPTIONS:
   --namespaces  -namespaces (default: false)
   --help, -h    show help (default: false)
```

## List All applications

_**logiqctl**_ cli provides the ls command to show the list of applications from which logs have been ingested. In the below example we see 3 different applications have sent log data from two namespaces

```bash
#./logiqctl ls
Namespace | Application        | ProcId                        | Last Seen    | First Seen
logiq     | logiq-flash        | logiq-flash-2                 | 244h:32m ago | 15m ago
logiq     | pithos             | pithos-69d44b5db7-2x8nw       | 17h:07m ago  | 32m ago
logiq     | coffee-worker      | coffee-worker-79b6b96879-wt7mg| 19h:29m ago  | 08h:28m ago
logiq     | logiq-flash        | logiq-flash-0                 | 244h:32m ago | 12h:10m ago
logiq     | flash-discovery    | logiq-discovery-0             | 235h:46m ago | 15h:14m ago
logiq     | beetle-coordinator | beetle-coordinator-55c8d6766c | 20h:09m ago  | 16h:39m ago
logiq     | check-postgres     | pithos-69d44b5db7-2x8nw       | 17h:07m ago  | 17h:07m ago
logiq     | check-postgres     | pithos-554d576564-65hf7       | 17h:12m ago  | 17h:12m ago
logiq     | pithos             | pithos-554d576564-65hf7       | 17h:12m ago  | 17h:12m ago
logiq     | pithos             | pithos-86c99db679-fmqnf       | 20h:11m ago  | 17h:20m ago
```

## Filter by Namespace

Using thee --namespaces filter, one can restrict the application listing for one or more namespaces only

```bash
#./logiqctl ls --namespaces kube-logging
Namespace    | Application | ProcId        | Last Seen    | First Seen
kube-logging | fluentd     | fluentd-7tfc6 | 244h:37m ago | 03h:23m ago
kube-logging | fluentd     | fluentd-jjmjk | 244h:36m ago | 17h:48m ago
kube-logging | fluentd     | fluentd-2k2j8 | 244h:36m ago | 23h:09m ago
```

