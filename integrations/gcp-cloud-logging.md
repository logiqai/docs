---
description: >-
  This article describes the process to export logs from GCP Cloud Logging to
  LOGIQ.
---

# GCP Cloud Logging

To set up log forwarding from GCP Cloud Logging to LOGIQ, you must:

* Create a user-managed service account
* Create a Cloud Pub/Sub topic
* Create a log sink and subscribe it to the Pub/Sub topic
* Create a VM for Logstash

The examples in this document use the `gcloud` command-line interface. Google Cloud APIs must be enabled through the [Services and APIs page](https://console.cloud.google.com/apis/dashboard?\_ga=2.18765881.1654975943.1641548418-621078828.1639568318) in the console before they can be used with `gcloud`. To perform the steps in this tutorial, enable the following APIs:

* Compute Engine
* Pub/Sub
* Identity and Access Management (IAM)
* Cloud Logging

### Create a service account

Activate and login to the Cloud Shell. Create a service account to attach to the VM

{% hint style="info" %}
The commands use [project name](https://cloud.google.com/storage/docs/projects#what\_is\_a\_project) `gcp-customer-1.`Replace it with a valid project name from the target account.
{% endhint %}

```
gcloud iam service-accounts create logstash --display-name="Logstash to Logiq"
```

Provide IAM permissions allowing the new service account to access Pub/Sub using the `pubsub.subscriber` role.

```
gcloud projects add-iam-policy-binding gcp-customer-1 \
--member serviceAccount:logstash@gcp-customer-1.iam.gserviceaccount.com \
--role roles/pubsub.subscriber

//Replace the customer name 'gcp-customer-1' with a valid one
```

### Create a Pub/Sub topic and subscription <a href="#create_a_pubsub_topic_and_subscription" id="create_a_pubsub_topic_and_subscription"></a>

Create a Pub/Sub topic where Cloud Logging will send events to be picked up by Logstash using the following command.

```
gcloud pubsub topics create logiq-topic
```

Next, create a subscription by running the following command.

```
gcloud pubsub subscriptions create logstash-sub --topic=logiq-topic \
 --topic-project=gcp-customer-1
```

### Create a log sink <a href="#create_a_log_sink" id="create_a_log_sink"></a>

Create a [log sink](https://cloud.google.com/logging/docs/routing/overview#sinks) to be used to export logs to the new Pub/Sub topic.

```
gcloud logging sinks create \
logstash-sink pubsub.googleapis.com/projects/gcp-customer-1/topics/logiq-topic

//Response
Created [https://logging.googleapis.com/v2/projects/scalesec-dev/sinks/logstash-sink].
Please remember to grant `serviceAccount:p3520xx273005-05xx3@gcp-sa-logging.iam.gserviceaccount.com` Pub/Sub
Publisher role to the topic.
More information about sinks can be found at /logging/docs/export/ 
```

The second part of the output is a reminder to verify that the service account used by Cloud Logging has permission to publish events to the Pub/Sub topic.&#x20;

```
gcloud beta pubsub topics add-iam-policy-binding logiq-topic \
--member serviceAccount:p245061149305-777814@gcp-sa-logging.iam.gserviceaccount.com \
--role roles/pubsub.publisher
```

### Create the Logstash VM <a href="#create_the_logstash_vm" id="create_the_logstash_vm"></a>

Create a VM to run `logstash` to pull logs from the Pub/Sub logging sink and send them to ElasticSearch:

```
gcloud compute --project=gcp-customer-1 instances create logstash \
--zone=us-west1-a \
--machine-type=n1-standard-1 \
--subnet=default \
--service-account=logstash@gcp-customer-1.iam.gserviceaccount.com \
--scopes="https://www.googleapis.com/auth/cloud-platform" \
--image-family=ubuntu-1804-lts \
--image-project=ubuntu-os-cloud \
--boot-disk-size=10GB \
--boot-disk-type=pd-ssd \
--boot-disk-device-name=logstash
```

Once the VM is running, SSH into the VM and then configure Logstash, as shown below.

```
gcloud compute ssh logstash --zone us-west1-a

sudo apt-get update
sudo apt-get -y upgrade
sudo apt -y install openjdk-8-jre-headless
echo "export JAVA_HOME=\"/usr/lib/jvm/java-8-openjdk-amd64\"" >> ~/.profile
sudo reboot
```

After a few moments, the VM will complete its reboot and can be accessed again via `gcloud`.

```
gcloud compute ssh logstash --zone us-west1-a
```

Install Logstash as shown below.

```
wget -qO - https://artifacts.elastic.co/GPG-KEY-elasticsearch | sudo apt-key add -
echo "deb https://artifacts.elastic.co/packages/6.x/apt stable main" | sudo tee -a /etc/apt/sources.list.d/elastic-6.x.list
sudo apt-get update
sudo apt-get install logstash

# Install Logstash google_pubsub plugin
cd /usr/share/logstash
sudo -u root sudo -u logstash bin/logstash-plugin install logstash-input-google_pubsub
```

#### Configure Logstash <a href="#configure_logstash" id="configure_logstash"></a>

Logstash comes with no default configuration. Create a new file `/etc/logstash/conf.d/logstash.conf` with these contents, modifying values as needed:

```
input
{
   google_pubsub {
       project_id => "gcp-customer-1"
       topic => "logiq-topic"
       subscription => "logstash-sub"
       include_metadata => true
       codec => "json"
   }
}
filter {
      json {
         source => "message"
       }
        mutate {
           add_field => { "namespace" => "%{[resource][labels][project_id]}" }
           add_field => { "cluster_id" => "dev" }
           add_field => { "app_name" => "%{[resource][labels][service_name]}" }
           add_field => { "proc_id" => "%{[resource][labels][revision_name]}"  }
        }
}
output {
 http {
       url => "http://<logiq-endpoint>.logiq.ai/v1/json_batch"
       headers => { "Authorization" => "Bearer <SECURE_INGEST_TOKEN>" }
       http_method => "post"
       format => "json_batch"
       content_type => "json_batch"
       pool_max => 2000
       pool_max_per_route => 100
       socket_timeout => 300
      }
}

```

You can obtain an ingest token from the LOGIQ UI as described [here](generating-a-secure-ingest-token.md#obtaining-an-ingest-token-using-ui). You can customize the `namespace` and `cluster_id` in the Logstash configuration based on your needs.

![GCP Cloud Run Logs](<../.gitbook/assets/image (19).png>)

Your GCP Cloud Logging logs will now be forwarded to your LOGIQ instance.&#x20;