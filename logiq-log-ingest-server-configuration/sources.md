# Sources

Sources provide matching rules for sender ip addresses. Sources can specify a single IP, a range of IP addresses or a list of IP addresses. A source definition can specify one or more of single IP, range of IP addresses or a list of IP addresses. In this case the source condition evaluates true if any of these source definitions are a match.

```text
sources:
  -
    name: localhost
    ipv4: 127.0.0.1
  -
    name: 3164_ip_1
    ipv4: 192.168.55.20
  -
    name: 3164_ip_2
    ipv4: 192.168.55.21
  -
    name: qa_lab
    ipv4: 192.168.40.3
    ipv4_range: 10.0.1.5/24
    ipv4_list: 192.168.1.1, 192.168.1.10
```

Sources are defined with the _**"sources"**_ keyword in the config file. All source definitions must have a "_**name"**_. Sources are referred in rules using their name. The _config file validator_ will flag an error for names that are not found and or source definitions that have a missing name.

## name \[required\]

This key is used to specify a unique name for source matching rules.

```text
-
    name: qa_lab
    ipv4_list: 192.168.1.1, 192.168.1.10
```

The source matching conditions are referenced in message [rules](/flash-configuration/rules.md) using their names

```text
rules:
  -
    source: localhost
    destination: t_debug
```

## Client IP/Network details \[optional\]

{% hint style="info" %}
At least one of ipv4, ipv4\_list and ipv4\_range is required when selecting a Client IP/Network based source
{% endhint %}

### ipv4 - Specify a single ip address

```text
sources:
  - 
     name: qa_lab_dns
     ipv4: 192.168.4.21
```

### ipv4\_list - Specify a list of ip addresses

An IP address list is specified by individual ip addresses separated by commas. Note that in the _**"ipv4\_list"**_ keyword, only individual ip addresses are allowed and not CIDR ranges.

```text
sources:
  -    
    name: qa_lab
    ipv4_list: 192.168.1.1, 192.168.1.10
```

### ipv4\_range - Specify a range of ip addresses

The IP address range is specified using the CIDR notation. E.g. 10.0.1.5/24 represents a range of ip's starting from 10.0.1.0 - 10.0.1.255 or a total of 256 addresses.

```text
sources:
  -
    name: qa_lab
    ipv4_range: 10.0.1.5/24
```

## Cloud S3 storage buckets

### Stackdriver logs from GCP cloud storage

LOGIQ can directly ingest from Stackdriver's Google cloud storage sink. You do not need to incur additional pub sub costs for this. Create a `google_cloud_storage` source in LOGIQ config for this.

```text
-
    name: stackdriver_gcp_storage_bucket
    s3:
      type: google_cloud_storage
      credential: >
        {
          "type": "service_account",
          "project_id": <google_project_id>,
          "private_key_id": <private_key_id>,
          "private_key": <private_key_string>,
          "client_email": <client_email>,
          "client_id": <client_id>,
          "auth_uri": "https://accounts.google.com/o/oauth2/auth",
          "token_uri": "https://oauth2.googleapis.com/token",
          "auth_provider_x509_cert_url": "https://www.googleapis.com/oauth2/v1/certs",
          "client_x509_cert_url": <client cert url>
        }
      bucket: <cloud storage bucket name>
```

