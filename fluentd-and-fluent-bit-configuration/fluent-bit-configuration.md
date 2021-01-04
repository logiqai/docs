---
description: Below resource will help in configuring fluent-bit forward to logiq.
---

# Fluent-bit configuration

_Forward_ is the protocol used by [Fluentd](http://www.fluentd.org) to route messages between peers. The **forward** output plugin allows to provide interoperability between compatible systems, Logiq being one.

Below code block defines the minimal changes to be added to fluentd configuration to start sending log events to flash.

```bash
[INPUT]
    Name              tail
    Path              /var/log/*
    Path_Key          On
    Tag               logiq
    Buffer_Max_Size   1024k
    Read_from_Head    On

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
    Name                         forward
    Match                        logiq
    host                         localhost
    port                         24224


```



