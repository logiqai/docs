# Ascent 2.10.3

We are excited to introduce the **v2.10.3** release of Flow, focused on expanding metrics capabilities, enhancing pipelines, and improving system performance.

{% hint style="info" %}
"Ascent v2.10.3 is now Generally Available — with OTEL Metrics support in Apica Telemetry Pipeline, and new JSON functions!"
{% endhint %}

***

### Flow

#### OpenTelemetry Metrics Support in Apica Telemetry Pipeline is GA.

* **OpenTelemetry Metrics in Telemetry Pipelines**:\
  Apica Flow now fully supports **receiving and forwarding OpenTelemetry (OTLP)-compatible metrics** within Apica telemetry pipelines.
* **OTLP Metrics Endpoint**:\
  You can now ingest metrics through the `/v1/metrics` OTLP-compatible endpoint.
* **Flexible Storage Options**:\
  Configure whether metrics are sent to internal Ascent Prometheus storage or forwarded externally to another OTLP compatible metric storage OR archive to an external object store.

***

### Pipelines and Rules Enhancements

#### New Functions

* **`flatten(input: object)`**:\
  Flattens nested JSON structures into simple key-value pairs.
* **`unflatten(input: object)`**:\
  Reconstructs nested JSON objects from flattened structures, enabling full roundtrip transformations.

***

This release further strengthens Apica Flow’s telemetry capabilities, giving you more flexibility, deeper observability, and better control over your pipelines and metrics.
