# Non Metric Indexes

Apica supports forwarding to splunk log indexes. Creating a splunk hec forwarder for logs is straight forward and uses the _"\_json"_ type when creating the forwarder

The following formation is required for the forwarder

1. The **"Host"** key is set to the Splunk host name.
2. The **"Password"** is set to the **`hec_token`** from Splunk
3. The **"port"** is set to splunk HEC port, default is `8088`
4. The **"user"** is set to "admin" or the user for which you are providing the HEC token
5. Select the type field and set it to `_json`

{% hint style="info" %}
The **Host**, **Password**, **Port**, **User** can also be set to use an external Splunk HEC endpoint directly
{% endhint %}

<figure><img src="https://logflow-docs.logiq.ai/~gitbook/image?url=https%3A%2F%2F3717450363-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252F8WGNQCWSTnL2NgouIRTq%252Fuploads%252FR5QUxMZLgiQEAKL9bGGY%252FScreen%2520Shot%25202023-01-04%2520at%25202.24.53%2520PM.png%3Falt%3Dmedia%26token%3Deb5d1f9b-a849-44df-8abf-e23113a9524a&#x26;width=768&#x26;dpr=4&#x26;quality=100&#x26;sign=ee405902&#x26;sv=1" alt=""><figcaption></figcaption></figure>
