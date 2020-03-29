---
description: >-
  This page documents the logiq-box CLI for log tailing, command line queries on
  the ingested log data
---

# Overview

## Help

```text
NAME:
   Logiq-box - Logiq CLI Tool

USAGE:
   logiqbox [global options] command [command options] [arguments...]

VERSION:
   1.0.0

AUTHOR:
   Logiq Inc

COMMANDS:
     configure, c  Configure Logiq-box
     list, ls      List of applications that you can tail
     tail, t       tail sudo cron
     query, q      query "sudo cron" 2h
     help, h       Shows a list of commands or help for one command

GLOBAL OPTIONS:
   --st value     Relative start time. (default: "10h")
   --et value     Relative end time. (default: "10h")
   --debug value  --debug true (default: "false")
   --help, -h     show help
   --version, -v  print the version
```

