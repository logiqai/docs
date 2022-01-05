# Docker Swarm logging

Shipping Docker Swarm logs to LOGIQ

To forward logs from Docker Swarm to LOGIQ, do the following.

**Step1:** Download the following configuration files:

* [parsers.conf](https://logiq-scripts.s3.ap-south-1.amazonaws.com/parsers.conf)
* [fluent-bit.conf](https://logiq-scripts.s3.ap-south-1.amazonaws.com/fluent-bit-linux-http.conf)

Next, in `fluent-bit.conf`, edit the `OUTPUT` section to add your `Logiq-endpoint` details and `Token`.

```
For HTTPS
[OUTPUT]
    name     http
    match    *
    host     <Logiq-endpoint>
    port     443
    URI      /v1/json_batch
    Format   json
    tls      on
    tls.verify  off
    net.keepalive  off
    compress      gzip
    Header Authorization Bearer <Token>

For HTTP:
[OUTPUT]
    name     http
    match    *
    host     <Logiq-endpoint>
    port     80
    URI      /v1/json_batch
    Format   json
    tls      off
    tls.verify  off
    net.keepalive  off
    compress      gzip
    Header Authorization Bearer <TOKEN>

```

**Step 2:** Ensure that the Fluent Bit Docker Compose uses the `parsers.conf` and `fluent-bit.conf` while we prepared in the previous step.&#x20;

```
version: "3.7"

services:
  fluent-bit:
    image: fluent/fluent-bit:latest
    container_name: fluent-bit
    volumes:
      - ./fluent-bit.conf:/fluent-bit/etc/fluent-bit.conf
      - ./parsers.conf:/fluent-bit/etc/parsers.conf
    ports:
      - "24224:24224"
      - "24224:24224/udp"
```

**Step 3:** Run the following command to get Fluent Bit running in your Docker Swarm cluster.

```
docker stack deploy --compose-file docker-compose.fluent.yaml fluent-bit
```

**Step 4:** Add the logging configuration to your Docker Compose YAML file using the **fluentd** and **YAML** anchors.&#x20;

If your default Docker Compose file looks like this:

```
version: "3.4"

Services:
  log_creator:
        image: alpine:3.12.4
         command: >
            sh -c '
                counter=0
                while :
                do
                    sleep 1
                    echo "{\"message\": \"log line $$counter\", \"something\": \"else\"}"
                    counter=$$(($$counter + 1))
                done'


```

After you’ve added the logging configuration, your Docker Compose file should look like this.

```
version: "3.4"

x-logging: &default-logging
  options:
        env: SERVICE_NAME
  driver: fluentd

services:
      log_creator:
        image: alpine:3.12.4
        logging: *default-logging
        command: >
            sh -c '
                counter=0
                while :
                do
                    sleep 1
                    echo "{\"message\": \"log line $$counter\", \"something\": \"else\"}"
                    counter=$$(($$counter + 1))
                done'
        Environment:
            SERVICE_NAME: log_creator
            Namespace: logiq-namespace
            AppName: Application-name
        logging:
            driver: fluentd
            options:
                env: "Namespace,AppName"
```

Run the following command to run the container.&#x20;

```
docker stack deploy --compose-file docker-compose.yaml logger
```

Your Docker Swarm logs will now be ingested into LOGIQ.
