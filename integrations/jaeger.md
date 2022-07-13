# Jaeger

LOGIQ.AI supports direct ingest of logs and traces from Jaeger agent and hosts the Jaeger Collector protocol port. Running the Jaeger agent to push traces can be done by specifiying the GRPC host port on the LOGIQ.AI Instance

```
#jaeger-agent --reporter.grpc.host-port=<logiq-endpoint>:14250
```

