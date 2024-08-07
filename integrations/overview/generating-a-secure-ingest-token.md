# Generating a secure ingest token

Apica Ascent uses an ingest token to secure the ingestion of log data from your data sources into your Apica Ascent deployment. You can generate a secure ingest token using the Apica Ascent UI and the command-line tool, [apicactl](https://github.com/ApicaSystem/apicactl).&#x20;

### Obtaining an ingest token using UI

You can obtain a secure ingest token from the Edit Profile page on the Apica Ascent UI.

To begin, click on the username on the navbar, and then click "**Edit Profile**". Your secure ingest token will be displayed under the **Ingest Token** field. Click the **Copy** icon next to the token to copy it to your clipboard.&#x20;

![Ingest Token](../../.gitbook/assets/inesttoken.png)

### Generating using apicactl

To generate a secure ingest token, do the following.&#x20;

1. [Install](https://github.com/ApicaSystem/apicactl?#quickstart) and [configure](https://github.com/ApicaSystem/apicactl/blob/main/docs/config/apicactl_config.md) `apicactl`, if you haven't already.&#x20;
2.  Run the following command to generate a secure ingest token:

    ```bash
    apicactl get httpingestkey
    ```
3. Copy the ingest key generated by running the command above and save it in a secure location.&#x20;

You can now use this ingest token while configuring Apica Ascent to ingest data from your data sources, especially while using log forwarders like Fluent Bit or Logstash.&#x20;

