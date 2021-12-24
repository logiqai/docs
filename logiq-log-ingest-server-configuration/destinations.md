# Destinations

Every LOGIQ server configuration file must have one or more destination for the data to be written to.&#x20;

```
destinations:
  -
    name: t_webservers
    s3:
      bucket: production
      prefix: webservers/
      credential: production
      groupings:
        -
          name: Environment
          value: Production
        -
          name: Tier
          value: Web
```

_NOTE: A missing destination in a rule is equivalent to evaluating the rule but dropping the incoming packet once a rule is matched_.  However, it is possible other rules with properly configured destinations may still process and successfully write the incoming packet.This also implies that an incoming data message can go to multiple destinations simultaneously.

Destinations are defined using the _**"destinations"**_ keyword in the configuration file. All destination definitions must have a _**"name"**_, a destination specific section and and optional _**"partition"**_ section defining data partitioning scheme.

The config validator will flag an error for destination names that are not defined but referenced in rules. In addition, depending on the type of the destination e.g. AWS S3 or On-prem S3, additional mandatory fields may be required when defining a destination.

## name \[required]

This key is used to specify a unique name for a destination definition

```yaml
-
    name: qa_lab
    ipv4_list: 192.168.1.1, 192.168.1.10
```

The destination for an incoming message is specified in the message [rules](https://app.gitbook.com/flash-configuration/rules.md) using their names

```yaml
rules:
  -
    source: debug_instances
    destination: t_debug
```

## partition \[optional]

An optional partition reference can be provided which tells the LOGIQ server on how to organize the data at the destination.

In the example below, there are two destinations defined: _**t\_webservers** and **t\_debug**_**.** A partition reference ** **_**p\_by\_day**_** ** is specified for the destination ** **_**t\_webservers** \_but not for_  **t**\_**debug.** The p\_by\_day is a named reference to a partition definition. See section on [Partitions](partitions.md) on how to specify a partitioning scheme for destination data.

```yaml
destinations:
  -
    name: t_webservers
    partition: p_by_day
    s3:
      bucket: production
      prefix: webservers/
      credential: production
      groupings:
        -
          name: Environment
          value: Production
        -
          name: Tier
          value: Web
  -
    name: t_debug
    s3:
      bucket: debug
      credential: debug
```

## Destination types

A destination definition must specify one of the below defined types. A destination with no subsection for one of the types, is not a valid destination and the config parser will issue an error.

## s3 \[required]

An S3 destination is used for AWS S3 and AWS S3 compatible object stores.&#x20;

_NOTE: For AWS S3 compatible object store, the AWS SDK should work on the object store and support bucket listing, creation and multi-part uploads._

Below are two examples. The first destination _**t\_webservers**_ is a definition of a bucket in AWS S3. The second destination ** **_**t\_minio\_webservers**_ is a definition of a bucket hosted in an S3 compatible object store. An S3 compatible object stores supports an optional endpoint key in the s3 definition that points to the http endpoint where the object store is hosted.

```
-
    name: t_webservers
    partition: p_by_day
    s3:
      bucket: logiqf978a
      region: us-east-1
      prefix: webservers
      credential: athena_and_s3_access
      groupings:
        -
          name: Environment
          value: Production
        -
          name: Tier
          value: Web
  -
    name: t_webservers
    partition: p_by_day
    s3:
      bucket: logiq-f978b
      endpoint: http://10.0.1.49:9000
      region: us-east-1
      prefix: webservers
      credential: compatible_s3
      groupings:
        -
          name: Environment
          value: Development
        -
          name: Tier
          value: Web
```

### bucket \[required]

The bucket key specifies the bucket in the S3 compatible store where LOGIQ will upload the log data. This is a required parameter and the bucket must exist. LOGIQ currently doesn't support creating the bucket automatically.

### credential \[required]

Every S3 destination must provide a credential to use. The credential key is a reference to a credential name that is defined in the credentials section of the config. Please refer to the [Credentials](credentials.md) section for more details on how to specify a credential.

### endpoint \[required for s3 compatible object stores]

If you want to write data to any S3 compatible object store thats not AWS S3 e.g. Nutanix Objects, Cloudian, Azure blob  etc., you need to specify the endpoint for the s3 compatible object store. The endpoint URL will either be an http or and https URL along with a port e.g. [http://10.1.0.49:9000](http://10.1.0.49:9000).

If an endpoint is not provided, it is implicitly assumed that we are talking with AWS S3.

### groupings \[optional]

Groupings provide a way to group incoming data streams that share similar characteristics. E.g. a user may want to tag all traffic coming from 10.0.20.0/24 subnet to be Production data stream. See section on [Groupings](groupings.md) for more details.

### prefix \[optional]

The prefix key is an optional key that specifies a prefix to use for all the objects being created in S3. E.g. if bucket is _**foo**_ and prefix is _**bar/**_, all of the uploaded data objects will be under _**foo/bar/**_

_NOTE: If a prefix is not specified, the destination name is used as a prefix._
