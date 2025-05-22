# Splunk Forwarding

Apica's plugins include creating one or more Splunk Output configurations that can be then used to send data to Splunk. We support all the enterprise modes for forwarding, including sending data to a Standalone Server, a list of indexers, and sending data to indexers using Peer discovery.

## Architecture

<figure><img src="../../.gitbook/assets/Design Documents (3).png" alt=""><figcaption><p>Splunk S2S Forwarding architecture</p></figcaption></figure>

### Required components <a href="#required-components" id="required-components"></a>

Follow the below steps to create an S2S forwarder to an splunk indexer:

1. Create a `Splunk Forwarding Proxy` `Source Extension`.
2. Create a `forwarder` to use the Splunk Forwarding Proxy `source extension` created in step 1 above:
   * One or more forwarders can be created to use the same Splunk Forwarding Proxy Source Extension
     * Forwarders can be of type _`_json` or `_metric`_
     * _`_metric`_ type can forward to a splunk metric index.
     * `_json` can forward to a splunk standard index.

### Creating Splunk UF proxy source extension (Forwarding Proxy) <a href="#creating-uf-proxy-app-extension" id="creating-uf-proxy-app-extension"></a>

The Splunk plugin for output configurations can be launched from the `Source Extensions` section under `Integrations`.

<figure><img src="../../.gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>

Selecting the `Forwarding Proxy` source extension gives you the configured proxies as well as the ability to create a new one.\


<figure><img src="../../.gitbook/assets/image (1) (1) (1).png" alt=""><figcaption><p>List of configured Splunk Forwarding Proxies</p></figcaption></figure>

You can expand on the proxy to see its settings. The `hec_token` can be used to setup the `forwarder`.\


<figure><img src="../../.gitbook/assets/image (2) (1).png" alt=""><figcaption><p>Proxy Settings upon expanding</p></figcaption></figure>
