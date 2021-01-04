---
description: Below resource will help in configuring fluentd forward to logiq.
---

# Fluentd configuration

Fluentd `out-forward`  Buffered Output plugin forwards events to other fluentd nodes. Logiq has the capability to act as one of the fluentd node.

Below code block defines the minimal changes to be added to fluentd configuration to start sending log events to flash

```bash
<source>
  @type tail
  path /var/log/*.log
  pos_file /var/log/tty.txt.pos
  <parse>
    @type none
  </parse>
</source>


<filter>
  @type record_transformer
  enable_ruby
  <record>
    hostname "#{Socket.gethostname}"
    namespace "#{Socket.gethostname}"
    log ${record["message"]}
  </record>
</filter>



<match>
  @type forward
  send_timeout 10s
  recover_wait 10s
  hard_timeout 20s


<format>
  @type msgpack
  time_type unixtime
  utc
 </format>
  <buffer time,tag,message>
    @type memory
    timekey 2s
    timekey_wait 1s
    flush_mode interval
    flush_interval 1s
    retry_max_interval 2s
    retry_timeout 10s
  </buffer>

   
  <server>
    name logiq
    host development.logiq.ai
    port 24224
    weight 100
  </server>

   <secondary>
    @type secondary_file
    directory /var/log/forward-failed
  </secondary>
</match>


```



