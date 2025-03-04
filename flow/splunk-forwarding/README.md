# Splunk Forwarding

Apica's plugins include creating one or more Splunk Output configurations that can be then used to send data to Splunk. We support all the enterprise modes for forwarding, including sending data to a Standalone Server, a list of indexers, and sending data to indexers using Peer discovery.

## Architecture

<figure><img src="../../.gitbook/assets/image (9) (1) (1) (1) (1).png" alt=""><figcaption><p>Splunk S2S Forwarding architecture</p></figcaption></figure>

#### Required components <a href="#required-components" id="required-components"></a>

Follow the below steps to create an S2S forwarder to a splunk indexer

1. Create a UF Proxy app extension
2. Create a forwarder to use the UF proxy app extension created in step 1 above
   * One or more forwarders can be created to use the same UF Proxy app
     * Forwarders can be of type \__json or \_metric_
     * \_metric type can forward to a splunk metric index
     * \_json can forward to a splunk standard index

#### Creating UF proxy app extension <a href="#creating-uf-proxy-app-extension" id="creating-uf-proxy-app-extension"></a>

The Splunk plugin for output configurations can be launched from the _App Extensions_ section under _Explore_.

<figure><img src="../../.gitbook/assets/image (10) (1) (1).png" alt=""><figcaption></figcaption></figure>

Selecting the _"Forwarding Proxy"_ app gives you the configured proxies as well as the ability to create a new one.

\


<figure><img src="../../.gitbook/assets/image (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption><p>List of configured Splunk Forwarding Proxies</p></figcaption></figure>

You can expand on the proxy to see its settings. The "hec\_token" can be used to setup the forwarder.

\


<figure><img src="../../.gitbook/assets/image (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (2) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption><p>Proxy Settings</p></figcaption></figure>
