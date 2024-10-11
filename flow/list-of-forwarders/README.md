---
description: >-
  Apica provides multiple targets to connect with your desired destination to
  collect, optimize, store, route, and replay your observability data –
  whenever, wherever you need it.
---

# List of Forwarders

Currently, **Apica** supports the below targets

| Target                                                                                                              | Type               | Description                                         |
| ------------------------------------------------------------------------------------------------------------------- | ------------------ | --------------------------------------------------- |
| [ArcSight Logger](https://logflow-docs.logiq.ai/security-monitor-forwarding/arc-sight)                              | Syslog, TCP, CEF   | Forward syslog frames over TCP                      |
| [ArcSight Logger](https://logflow-docs.logiq.ai/security-monitor-forwarding/arc-sight)                              | Syslog, TCP        | Forward ArcSight CEF frames over TCP                |
| [DataDog](https://logflow-docs.logiq.ai/forwarding-to-monitoring-tools/datadog-forwarding)                          | JSON               | Batched JSON forward to DataDogDataDog              |
| [Dynatrace HTTP Event Collector](https://logflow-docs.logiq.ai/forwarding-to-monitoring-tools/dynatrace-forwarding) | JSON               | Batched JSON forward to Dynatrace                   |
| [Elastic Compatible](https://logflow-docs.logiq.ai/forwarding-to-monitoring-tools/elasticsearch-forwarding)         | JSON               | Send data to an Elastic index                       |
| [RSA NetWitness Syslog](https://logflow-docs.logiq.ai/security-monitor-forwarding/rsa-new-witness)                  | TCP                | Syslog forwarder for RSA Netwitness                 |
| [RSA NetWitness Syslog (CEF)](https://logflow-docs.logiq.ai/security-monitor-forwarding/rsa-new-witness)            | TCP, CEF           | Syslog CEF forwarder for RSA Netwitness             |
| [NewRelic HTTP Event Collector](https://logflow-docs.logiq.ai/forwarding-to-monitoring-tools/new-relic-forwarding)  | JSON               | Batched JSON forward to NewRelic                    |
| Splunk HTTP Event Collector                                                                                         | JSON               | Batched JSON forward to Splunk                      |
| Splunk Universal / Heavy Forwarder                                                                                  | Syslog, TCP        | Syslog forwarder for Splunk                         |
| Splunk Universal CEF Forwarder                                                                                      | Syslog, TCP, CEF   | Syslog CEF forwarder for Splunk                     |
| Splunk Universal Forwarder / Heavy Forwarder                                                                        | S2S                | Forward data to Apica in Cooked mode                |
| [Object Store](https://logflow-docs.logiq.ai/object-store-forwarding/s3-compatible)                                 | S3 Compatible      | AWS S3, CEPH, Minio, GCP Cloud Storage, OCI Buckets |
| [Object Store](https://logflow-docs.logiq.ai/object-store-forwarding/azure-blob-storage)                            | Azure Blob Storage | Native support for Azure blob storage API's         |

#### Configuring a Forwarder <a href="#configuring-a-forwarder" id="configuring-a-forwarder"></a>

To configure a Forwarder navigate to the Forwarder page first and Select your preferred forwarder

Below, an example of configuring a Splunk HTTP Event Collector is shown

1. **Creating an HTTP Event Collector Data Input key from Splunk**
   * Navigate to your Splunk Environment
   * Locate the Settings menu
   * Locate the Data Inputs sub-menu
   * Click on the New Token option which is located on the top banner
   * Enter a Token name and skip to the last page and click Done
   * Use the generated **HTTP Event Collector** key in Apica
2.  **Creating a Splunk HTTP Event Collector on Apica**

    * Navigate to the Creaet Forwarders page
    * Click on Forwarders
    * Click on the Splunk HTTP Event Collector

    ![](https://logflow-docs.logiq.ai/\~gitbook/image?url=https%3A%2F%2F3717450363-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252F8WGNQCWSTnL2NgouIRTq%252Fuploads%252FNiLIm4VAjVHsbYjVOyPl%252FScreen%2520Shot%25202023-01-02%2520at%25205.31.52%2520PM.png%3Falt%3Dmedia%26token%3Df6b21835-6e93-4eb5-ba60-bc1917cc3f3a\&width=768\&dpr=4\&quality=100\&sign=dfcdc499\&sv=1)Create Forwarder

![](https://logflow-docs.logiq.ai/\~gitbook/image?url=https%3A%2F%2F3717450363-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252F8WGNQCWSTnL2NgouIRTq%252Fuploads%252FykXNAsMPz5f8dnCSDLw7%252FScreenshot%2520from%25202022-07-15%252018-18-28.png%3Falt%3Dmedia%26token%3De174eab1-1651-44d7-adb2-8fa114a692ac\&width=768\&dpr=4\&quality=100\&sign=8ce6d1fb\&sv=1)

* Fill out all the below fields and click save
  * **buffer\_size**: The Buffer size for logs
  * **host**: Splunk Endpoint
  * **password**: Data Input Key created in step 1
  * **port**: Splunk server receiving port (default 8088)
  * **type:** log format (_default_ \__json, or set to \_metric to send to a metric index_)
  * **user:** UI username of Splunk Endpoint
  * **name**: Name of the forwarder

![](https://logflow-docs.logiq.ai/\~gitbook/image?url=https%3A%2F%2F3717450363-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252F8WGNQCWSTnL2NgouIRTq%252Fuploads%252FzIQvhC2Fx85oXRFufJs4%252F2022-07-15\_18-42.png%3Falt%3Dmedia%26token%3D16ed5515-c927-4451-9f3e-7167d63445a8\&width=768\&dpr=4\&quality=100\&sign=9198ca8a\&sv=1)

That's it. You've successfully created the Splunk HTTP Event Collector forwarder. Now navigate to the Explore page and start doing Mapping or Replay operation.
