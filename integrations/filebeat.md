# Filebeat

Filebeat is a lightweight shipper for **forwarding and centralizing log data**. Installed as an agent on your servers, Filebeat monitors the log files or locations that you specify, collects log events, and forwards them either to Elasticsearch or Logstash for indexing.

Logiq supports data ingestion from filebeats, the below page describes how to send logs from Filebeat to LOGIQ by making changes on the filebeat configuration to enable logs to be forwarded to Logiq endpoint.

{% hint style="info" %}
We need to add the processors under input section as an addition to the current filebeat configuration along with namespace, application and cluster-id that needs to be seen on Logiq
{% endhint %}

```
filebeat:
  inputs:
  - enabled: true
    paths:
    - <path to your log>
    type: filestream
    processors:
      - add_fields:
          target: logiq
          fields:
            namespace: myproject
            application: test
            cluster_id: foo

output:
#  console:
#   pretty: true
  logstash:
    hosts:
    - <Logiq-endpoint>:25224
processors:
- add_host_metadata:
    when:
      not:
        contains:
          tags: forwarded
- add_cloud_metadata: null
- add_docker_metadata: null
- add_kubernetes_metadata: null
setup:
  kibana: null
  template:
    settings:
      index:
        number_of_shards: 1
```



