# Non Metric Indexes

Apica supports forwarding to non-metrics indexes. Creating a splunk forwarder is straight forward and uses the _"\_json"_ type when creating the forwarder

The following formation is obtained from the Apica UF Proxy App extension for the forwarder

1. The **"Host"** key is set to the Apica UF Proxy App extension that was created and should not use the Splunk host name.
2. The **"Password"** is set to the hec\_token from the Apica UF Proxy App extension
3. The **"Port"** is set to 8088
4. The **"User"** is set to **"admin"**

{% hint style="info" %}
The **Host**, **Password**, **Port**, **User** can also be set to use an external Splunk HEC endpoint directly
{% endhint %}

<figure><img src="https://logflow-docs.logiq.ai/~gitbook/image?url=https%3A%2F%2F3717450363-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252F8WGNQCWSTnL2NgouIRTq%252Fuploads%252FR5QUxMZLgiQEAKL9bGGY%252FScreen%2520Shot%25202023-01-04%2520at%25202.24.53%2520PM.png%3Falt%3Dmedia%26token%3Deb5d1f9b-a849-44df-8abf-e23113a9524a&#x26;width=768&#x26;dpr=4&#x26;quality=100&#x26;sign=ee405902&#x26;sv=1" alt=""><figcaption></figcaption></figure>
