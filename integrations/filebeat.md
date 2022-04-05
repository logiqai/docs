# Filebeat

Filebeat is a lightweight shipper for **forwarding and centralizing log data**. Installed as an agent on your servers, Filebeat monitors the log files or locations that you specify, collects log events, and forwards them either to Elasticsearch or Logstash for indexing.

LOGIQ supports data ingestion from Filebeat. The following section describes the steps for configuring log forwarding from Filebeat to LOGIQ by modifying the Filebeat configuration file.&#x20;

### Configuring Filebeat to forward logs to LOGIQ

To configure Filebeat, you need to configure the Filebeat configuration file. The location of your Filebeat configuration file can vary depending on your platform. Locate and access the configuration file and modify it as described below.&#x20;

Under the `input` section, include the `processors` section in addition to your existing Filebeat configuration along with `namespace`, `application`, and `cluster_id`. Doing so ensures that the logs you forward to LOGIQ can be identified and partitioned easily.&#x20;

The following is an example Filebeat configuration file for forwarding logs to LOGIQ without SSL.&#x20;

```
output.logstash:
  hosts: ["logs.mycompany.com:5044"]
   "/etc/client.key"
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
    hosts:["Logiq-endpoint>:25224"]
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

#### Enabling log forwarding from Filebeat to LOGIQ using SSL

To configure Filebeat to use SSL while forwarding logs, specify the key/SSL certificate information under the `ssl` field. You must also specify `25225` as the port for your LOGIQ endpoint in the `output` section.&#x20;

The following is an example of a Filebeat configuration file with `processors` and `ssl` configured to forward logs to LOGIQ using SSL.&#x20;

```
output.logstash:
  hosts: ["logs.mycompany.com:5044"]
   "/etc/client.key"
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
    hosts:["Logiq-endpoint>:25225"]
    ssl.certificate_authorities: "/etc/ssl/LOGIQ/certs/LOGIQ.crt"
    ssl.certificate: "/etc/ssl/LOGIQ/certs/client.crt"
    ssl.key: "/etc/ssl/LOGIQ/certs/client.key"
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

Your logs will now be forwarded from Filebeat into LOGIQ and will start appearing in the LOGIQ UI.&#x20;
