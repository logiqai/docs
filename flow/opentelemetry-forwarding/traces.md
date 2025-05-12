# Traces

The **OTLP Trace Forwarder** lets you send traces in OTLP format (OpenTelemetry Protocol) to any external HTTP-compatible backend. This is useful for integrating Ascent with Jaeger, custom observability platforms, or third-party tracing services that support OTLP.

You can find it in the **Forwarders** section:

<figure><img src="../../.gitbook/assets/image (417).png" alt=""><figcaption></figcaption></figure>

***



## Configuration

<table><thead><tr><th width="154.4453125">Field</th><th width="82.66015625">Type</th><th width="88.203125">Required</th><th>Description</th></tr></thead><tbody><tr><td><code>endpoint</code></td><td>string</td><td>✅</td><td>Full URL to which OTLP traces will be sent. Example: https://example.com/v1/traces</td></tr><tr><td><code>name</code></td><td>string</td><td>✅</td><td>Name of the forwarder</td></tr></tbody></table>

#### How it Works

Once you create a forwarder, it can be mapped to any of your namespaces/apps that are currently receiving OTEL-formatted traces.



All trace events that conform to the OTEL protocol will be automatically forwarded to the specified endpoint via OTLP over HTTP.
