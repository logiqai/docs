# HEC Forwarder

Apica supports forwarding data to Splunk HEC indexes using the HTTP Event Collector Forwarder

Access the Integrations menu and navigate to Forwarders. Locate the HTTP Event Collector and choose the Splunk HTTP Event Collector option. Follow the sections to configure both Metric and Non-Metric indexes. Remember, when forwarding data to metric indexes, ensure your data is in a metric format compatible with Splunk.

1. [Metric Index](../metric-indexes.md)
2. [Non-Metric Index](../non-metric-indexes.md)

{% hint style="info" %}
NOTE that Splunk HEC may have data rate limits beyond which it can drop data. Make sure your HEC endpoints are configured to ingest data to match your data requirements.
{% endhint %}

<figure><img src="../../../.gitbook/assets/Screenshot 2025-05-15 at 5.50.02 AM.png" alt=""><figcaption><p>Create a Splunk HEC Forwarder</p></figcaption></figure>
