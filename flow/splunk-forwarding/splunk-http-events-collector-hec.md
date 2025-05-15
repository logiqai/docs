# Splunk HTTP Events Collector (HEC)

*

    <figure><img src="../../.gitbook/assets/Screenshot from 2025-05-15 18-29-11.png" alt=""><figcaption></figcaption></figure>

To send data from Ascent to Splunk using HEC, use the `Splunk HTTP Events Collector Forwarder`. Follow the steps below to create the forwarder:

1. Click on the \`Integrations option in the navbar
2. Choose the `Forwarders` tab.
3. Click on `Add Forwarder`.
4. Under the`Password` section add the `Splunk HEC`token.
5. Under the `Host` section mention the domain of the Splunk instance. (Note: Use the http:// prefix for non-TLS connections).

#### To Create Splunk HEC Token:

1. Go to Settings.
2. Under the Data section, choose `Data Inputs.`&#x20;
3. Choose `HTTP Event Collector` .
4. After creating a token, use the token to create a Splunk HEC Forwarder in Ascent.
