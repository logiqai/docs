# Syslog Forwarding

You can also create a forwarder to send data in syslog format to Splunk. Note his needs you to enable the syslog receive ports on the Splunk instance

There are two types for syslog forwarding that are supported

1. Raw Syslog
2. Syslog CEF

Apica does not support sending to syslog UDP ports. Only TCP ports are supported.

Create the appropriate forwarder type when creating the forwarder

<figure><img src="https://logflow-docs.logiq.ai/~gitbook/image?url=https%3A%2F%2F3717450363-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252F8WGNQCWSTnL2NgouIRTq%252Fuploads%252Fe9K6fb4HEdkUUf0Ulk0O%252FScreen%2520Shot%25202023-01-04%2520at%25202.31.48%2520PM.png%3Falt%3Dmedia%26token%3D54eadb1f-d42b-4ae5-8b34-a40560bd879b&#x26;width=768&#x26;dpr=4&#x26;quality=100&#x26;sign=aa78d148&#x26;sv=1" alt=""><figcaption><p>Splunk Forwarder Syslog / CEF</p></figcaption></figure>

Once selected, provide the syslog port details for sending the syslog data

<figure><img src="https://logflow-docs.logiq.ai/~gitbook/image?url=https%3A%2F%2F3717450363-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252F8WGNQCWSTnL2NgouIRTq%252Fuploads%252FkefsYvvYjln3CEpjwo8I%252FScreen%2520Shot%25202023-01-04%2520at%25202.28.38%2520PM.png%3Falt%3Dmedia%26token%3Ddfa2ef2a-770d-4aff-8be0-4a10650d1db5&#x26;width=768&#x26;dpr=4&#x26;quality=100&#x26;sign=f0dc9cf0&#x26;sv=1" alt=""><figcaption><p>Syslog configuration</p></figcaption></figure>
