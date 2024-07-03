# Splunk Forwarding Overview

Apica's plugins include creating one or more Splunk Output configurations that can be then used to send data to Splunk. We support all the enterprise modes for forwarding, including sending data to a Standalone Server, a list of indexers, and sending data to indexers using Peer discovery.

#### Architecture <a href="#architecture" id="architecture"></a>

Splunk S2S Forwarding architecture

<figure><img src="https://logflow-docs.logiq.ai/~gitbook/image?url=https%3A%2F%2F3717450363-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252F8WGNQCWSTnL2NgouIRTq%252Fuploads%252FDUEHhPJBH4HITAyxqJR1%252Fsplunk-arch.png%3Falt%3Dmedia%26token%3Dcca9c8fb-04f8-4816-90d1-201074f5a74f&#x26;width=768&#x26;dpr=4&#x26;quality=100&#x26;sign=ca4273af&#x26;sv=1" alt=""><figcaption></figcaption></figure>

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

<figure><img src="https://logflow-docs.logiq.ai/~gitbook/image?url=https%3A%2F%2F3717450363-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252F8WGNQCWSTnL2NgouIRTq%252Fuploads%252Fu49WQWhMr2rmfqHGaBI8%252FScreen%2520Shot%25202023-01-02%2520at%25205.25.13%2520PM.png%3Falt%3Dmedia%26token%3D7f08d97e-e104-4874-a437-7d167c0ae74a&#x26;width=768&#x26;dpr=4&#x26;quality=100&#x26;sign=bc1d261d&#x26;sv=1" alt=""><figcaption></figcaption></figure>

Selecting the _"Forwarding Proxy"_ app gives you the configured proxies as well as the ability to create a new one.

List of configured Splunk Forwarding Proxies

<figure><img src="https://logflow-docs.logiq.ai/~gitbook/image?url=https%3A%2F%2F3717450363-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252F8WGNQCWSTnL2NgouIRTq%252Fuploads%252FgoIvoyEIPpcyN8BKcFjW%252FScreen%2520Shot%25202022-08-01%2520at%25209.20.16%2520PM.png%3Falt%3Dmedia%26token%3D07dce234-09a9-420a-855b-644e71c619f5&#x26;width=768&#x26;dpr=4&#x26;quality=100&#x26;sign=5084634c&#x26;sv=1" alt=""><figcaption></figcaption></figure>

You can expand on the proxy to see its settings. The "hec\_token" can be used to setup the forwarder.

<figure><img src="https://logflow-docs.logiq.ai/~gitbook/image?url=https%3A%2F%2F3717450363-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252F8WGNQCWSTnL2NgouIRTq%252Fuploads%252FRjFXbU8V50FoUfIIKaE4%252FScreen%2520Shot%25202023-01-04%2520at%25201.45.42%2520PM.png%3Falt%3Dmedia%26token%3D90bf900e-c0ec-41fc-b416-229bc2a01945&#x26;width=768&#x26;dpr=4&#x26;quality=100&#x26;sign=b2e4e9f4&#x26;sv=1" alt=""><figcaption></figcaption></figure>

<figure><img src="https://logflow-docs.logiq.ai/~gitbook/image?url=https%3A%2F%2F3717450363-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252F8WGNQCWSTnL2NgouIRTq%252Fuploads%252FdlGeSIboOYED6YGWkLsT%252FScreen%2520Shot%25202022-08-01%2520at%25209.20.44%2520PM.png%3Falt%3Dmedia%26token%3D6686aa64-048a-4183-9ab1-83ed54defa17&#x26;width=768&#x26;dpr=4&#x26;quality=100&#x26;sign=f6da0efc&#x26;sv=1" alt=""><figcaption></figcaption></figure>
