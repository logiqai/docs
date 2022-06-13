# Kafka

LOGIQ can run streaming analytics on any Kafka streams. The data in Kafka can be pushed to LOGIQ if the Kafka servers are running inside the customer network. If the Kafka endpoint is accessible to the LOGIQ network LOGIQ can pull the data directly from Kafka.

## Pushing data to Logiq

![Push data to Kafka](../.gitbook/assets/kafka\_push.png)

Logstash instances deployed in the customer network can read data from Kafka and push it to LOGIQ. Use the below configuration to read from Kafka.

### Input Logstash configuration

```
input {
    kafka {
            bootstrap_servers => "localhost:9092"
            topics => "test_topic"
    }
}
```

### Output Logstash Configuration&#x20;

```
output {
   http {
        url => "https://logiq-dns-or-ip/v1/json_batch"
        headers => { "Authorization" => "Bearer <Auth token>" }
        http_method => "post"
        format => "json_batch"
        content_type => "json_batch"
        pool_max => 300
        pool_max_per_route => 100
        socket_timeout => 60
       }
}
```

You can additionally control the data organization by specifying additional fields

```
filter {
  mutate {
    add_field => { "cluster_id" => "demo-http-test" }
    add_field => { "namespace" => "namespace_name" }
    add_field => { "app_name" => "application_name" }
  }
}
```

## Pulling Data from Kafka

LOGIQ can pull data using Kafka Input Plugins. This method requires the Kafka endpoint to be reachable from LOGIQ network.&#x20;

Kafka endpoint, Topic name, namespace, and application name are needed to configure the Kafka input plugin. Namespace and Application define how the data is partitioned in LOGIQ, see [here for more information](../vewing-logs/logs-terminology.md).&#x20;

![](../.gitbook/assets/kafka\_pull.png)
