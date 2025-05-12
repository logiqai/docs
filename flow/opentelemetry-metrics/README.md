---
description: >-
  Apica Flow supports OpenTelemetry metrics in telemetry pipelines for both
  receiving from OpenTelemetry compatible metrics sources and forwarding to
  OpenTelemetry Compatible Metric destinations.
---

# OpenTelemetry Metrics

{% hint style="info" %}
Apica Flow exclusively supports telemetry pipelines through the OTLP metrics endpoints. You can confidently utilize the OTLP-compatible endpoint hosted at **/v1/metrics**.
{% endhint %}

### Turning on OpenTelemetry compatible metrics in the telemetry pipeline

Navigate to **Settings -> Admin Settings -> Ingest Configuration** and enable the metrics ingest into the pipeline. You can also disable the metrics going to the Ascent Prometheus storage backed by InstaStore, but if you want to view metrics in the Apica Ascent UI, keep this option disabled. This setup allows you to send metrics to the telemetry pipeline and visualize them in the Ascent UI seamlessly.

* Enable the **`METRICS_TO_PIPELINE_EVENTS`** toggle to activate metrics flow in the telemetry pipeline. This feature is initially turned off
* `METRICS_STORE_DISABLE` - Enable this option to skip storing metrics in InstaStore. By default, it is off. Activate this when the telemetry pipeline forwards metrics to an external forwarder

<figure><img src="../../.gitbook/assets/Screenshot 2025-05-12 at 2.45.19 PM.png" alt=""><figcaption><p>Apica Ascent Settings page for Ingest configuration</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/Screenshot 2025-05-12 at 2.45.06 PM.png" alt=""><figcaption><p>OpenTelemetry Metrics settings for telemetry pipeline</p></figcaption></figure>

