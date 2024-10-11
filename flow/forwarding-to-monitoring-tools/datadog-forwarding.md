---
description: This page explains how to forward logs to DataDog from Apica
---

# Datadog Forwarding

Generating API Key from DataDog

Generating an API key from DataDog is a simple process that allows you to securely access data from the platform.

To add a Datadog API key or client token:

1. Navigate to Organization settings, then click the **API keys** or **Client Tokens** tab.
2. Click the **New Key** or **New Client Token** button, depending on which you’re creating.
3. Enter a name for your key or token.
4. Click **Create API key** or **Create Client Token**.

For more details on how to generate an API key in DataDog, you can visit this [link](https://docs.datadoghq.com/account\_management/api-app-keys/).

### Steps to Create DataDog Forwarding <a href="#steps-to-create-datadog-forwarding" id="steps-to-create-datadog-forwarding"></a>

To forward your logs to DataDog, begin by logging into Apica's website.

* Navigate to the **`Create`** tab and select the option for **`Forwarder`**.
* Next, choose **`DataDog(JSON)`** from the available options; this will bring up a new form with fields such as `API Key`, `Buffer Size`, `Host` and `Tags`. Fill out the required data in these fields and click **`Create`**.

Create Forwarder:

```
Api_Key:       <DATADOG-API-KEY>
Buffer_size:   16000
Host:          app.datadog.com
Tags:          logs
Type:          _json
Name:          DataDog Forwarder
```

* Next, head over to the **`Explore`** page and pick out a namespace you wish to forward your logs to DataDog from.
* Click on the three dots icon located next to the calendar and opt for **`Map Forwarder`**; this will open a new modal which allows you to choose the newly created DataDog forwarder schema (this can be identified via its datadog icon).
* Confirm your selection by clicking **`OK`**.
* A successful mapping is indicated by a popup showing that `namespace-application pairs are connected with respective forwarders`; additionally, you'll notice an updated Namespace Forwarder status in effect.
* Your logs are now being forwarded to DataDog.

> To help make the steps easier to understand, below are the screenshots illustrating each of the instructions given above.

<figure><img src="../../.gitbook/assets/image (224).png" alt=""><figcaption><p>Create -> Forwarder</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (225).png" alt=""><figcaption><p>Create Forwarder Modal</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (226).png" alt=""><figcaption><p>Explore Page, selected Windows Namespace</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (227).png" alt=""><figcaption><p>Map Forwarder</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (228).png" alt=""><figcaption><p>Selecting the DataDog Forwarder</p></figcaption></figure>
