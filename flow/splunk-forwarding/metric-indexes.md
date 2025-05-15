# Metric Indexes

Apica supports forwarding to splunk metrics indexes. Both old metrics format and new format with multiple metrics per event are supported.

Creating a splunk metrics forwarder is straight forward and uses the _"\_metric"_ type when creating the forwarder

The following formation is required for the forwarder

1. The **"Host"** key is set to the Splunk host name.
2. The **"Password"** is set to the **`hec_token`** from Splunk
3. The **"port"** is set to splunk HEC port, default is `8088`
4. The **"user"** is set to "admin" or the user for which you are providing the HEC token
5. Select the type field and set it to `_metric`

{% hint style="info" %}
The **Host**, **Password**, **Port**, **User** can also be set to use an external Splunk HEC endpoint directly
{% endhint %}



<figure><img src="https://logflow-docs.logiq.ai/~gitbook/image?url=https%3A%2F%2F3717450363-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252F8WGNQCWSTnL2NgouIRTq%252Fuploads%252FoinuTxixZ6lLoD4xYJot%252FScreen%2520Shot%25202023-01-03%2520at%252010.45.54%2520AM.png%3Falt%3Dmedia%26token%3D9771e013-3c2a-4613-87af-8e029dc1406e&#x26;width=768&#x26;dpr=4&#x26;quality=100&#x26;sign=3b0fa581&#x26;sv=1" alt=""><figcaption></figcaption></figure>
