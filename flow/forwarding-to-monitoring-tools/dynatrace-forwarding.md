---
description: This page explains how to forward logs to Dynatrace from Apica.
---

# Dynatrace Forwarding

To Generate an API Key from Dynatrace, please follow the instructions in this [link](https://www.dynatrace.com/support/help/dynatrace-api/basics/dynatrace-api-authentication).

### Steps to Create New Relic Forwarding <a href="#steps-to-create-new-relic-forwarding" id="steps-to-create-new-relic-forwarding"></a>

To forward your logs to Dynatrace, begin by logging into Apica's website.

* Navigate to the **`Create`** tab and select the option for **`Forwarder`**.
* Next, choose **`Dynatrace(HTTP event collector)`** from the available options; this will bring up a new form with fields such as `API Key`, `Host`, `Tags`, etc. Fill out the required data in these fields and click **`Create`**.

Create Forwarder:

Copy

```
Api_Key:       <DYNATRACE-API-KEY>
Host:          <DYNATRACE-ENDPOINT>
Tags:          logflow
Type:          _json
Name:          Dynatrace
```

* Next, head over to the **`Explore`** page and pick out a namespace you wish to forward your logs to Dynatrace.
* Click on the three dots icon located next to the calendar and opt for **`Map Forwarder`**; this will open a new modal that allows you to choose the newly created Dynatrace forwarder schema (this can be identified via its Dynatrace icon).
* Confirm your selection by clicking **`OK`**.
* A successful mapping is indicated by a popup showing that namespace-application pairs are connected with respective forwarders; additionally, you'll notice an updated Namespace Forwarder status in effect.
* Your logs are now being forwarded to Dynatrace.

> To help make the steps easier to understand, below are the screenshots illustrating each of the instructions given above.

<figure><img src="https://logflow-docs.logiq.ai/~gitbook/image?url=https%3A%2F%2F3717450363-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252F8WGNQCWSTnL2NgouIRTq%252Fuploads%252FrtBniNrUgD5qJMjsJ18E%252FScreenshot%2520from%25202023-01-03%252017-54-30.png%3Falt%3Dmedia%26token%3D23db4080-656c-41c4-aaf8-da6acab8bc27&#x26;width=768&#x26;dpr=4&#x26;quality=100&#x26;sign=594b6c69&#x26;sv=1" alt=""><figcaption><p>List of Forwarders</p></figcaption></figure>

<figure><img src="https://logflow-docs.logiq.ai/~gitbook/image?url=https%3A%2F%2F3717450363-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252F8WGNQCWSTnL2NgouIRTq%252Fuploads%252Fm3QVFHkzr8OmZs5mc6kr%252FScreenshot%2520from%25202023-01-03%252017-54-43.png%3Falt%3Dmedia%26token%3Deb711d7d-f6f9-45ba-a064-269f565dd30a&#x26;width=768&#x26;dpr=4&#x26;quality=100&#x26;sign=6cb1e062&#x26;sv=1" alt=""><figcaption><p>Create Forwarder</p></figcaption></figure>

<figure><img src="https://logflow-docs.logiq.ai/~gitbook/image?url=https%3A%2F%2F3717450363-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252F8WGNQCWSTnL2NgouIRTq%252Fuploads%252FJsDFr7Np1DZSkbe9IMsU%252FScreenshot%2520from%25202023-01-03%252017-55-41.png%3Falt%3Dmedia%26token%3D48dde201-abaf-455f-9672-4ff932421bec&#x26;width=768&#x26;dpr=4&#x26;quality=100&#x26;sign=e5020d70&#x26;sv=1" alt=""><figcaption><p>Selecting a Namespace</p></figcaption></figure>

<figure><img src="https://logflow-docs.logiq.ai/~gitbook/image?url=https%3A%2F%2F3717450363-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252F8WGNQCWSTnL2NgouIRTq%252Fuploads%252F8ewtk1W2k6BtEqIqzW4k%252FScreenshot%2520from%25202023-01-03%252017-55-50.png%3Falt%3Dmedia%26token%3D128b6ffe-5452-483f-9900-ff70151c622e&#x26;width=768&#x26;dpr=4&#x26;quality=100&#x26;sign=13667539&#x26;sv=1" alt=""><figcaption><p>Map Forwarder</p></figcaption></figure>

<figure><img src="https://logflow-docs.logiq.ai/~gitbook/image?url=https%3A%2F%2F3717450363-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252F8WGNQCWSTnL2NgouIRTq%252Fuploads%252FazPRQyZE6h17iPS839Bm%252FScreenshot%2520from%25202023-01-03%252017-56-17.png%3Falt%3Dmedia%26token%3D32ddca01-4b6c-42d1-9809-3dca9df55355&#x26;width=768&#x26;dpr=4&#x26;quality=100&#x26;sign=3dd09502&#x26;sv=1" alt=""><figcaption><p>Selecting Dynatrace forwarder schema as Forwarder</p></figcaption></figure>

<figure><img src="https://logflow-docs.logiq.ai/~gitbook/image?url=https%3A%2F%2F3717450363-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252F8WGNQCWSTnL2NgouIRTq%252Fuploads%252FMI7aFKMXuoMAax5Dfr2w%252FScreenshot%2520from%25202023-01-03%252017-56-30.png%3Falt%3Dmedia%26token%3D445273b0-f09f-4054-9748-cf490cf9f7a5&#x26;width=768&#x26;dpr=4&#x26;quality=100&#x26;sign=33019bc0&#x26;sv=1" alt=""><figcaption><p>Successful Mapping of Forwarder</p></figcaption></figure>
