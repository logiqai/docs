# Groupings

Incoming data can be tagged with user defined key value pairs for facilitating analytics. The key value pair is called a grouping in the LOGIQ platform. A destination may specify one or more groupings to be applied to the incoming data message.

```
destinations:
  - name: t_webservers
    partition: p_by_day
    s3:
      bucket: logiqcloud
      region: us-east-1
      prefix: dev-logs
      credential: athenas3
      groupings:
        - name: Environment
          value: Production
        - name: Tier
          value: Web
```

The LOGIQ platform provides the below built-in groupings that are common. Additional groupings can be defined by the user when setting up the configuration file.

```
 groupings:
   -
    name: Environment
    values:
      - Production
      - Staging
      - Development
      - QA
      - UAT
    description: The Environment for which the log is being collected
  -
    name: Tier
    values:
      - Database
      - Web
      - Cache
      - LoadBalancer
      - Queue
      - Analytics
      - Logger
      - Unknown
    description: The Tier of the app typically in a multi-tier application
```

Built-in groupings can be extended by adding extra values. This is done by creating a grouping definition in the configuration file with the same name. The user defined values are merged with the built-in values.

Custom groupings are defined using the _**"groupings"**_ keyword and related attributes.&#x20;

```
groupings:
  - 
    name: CustomGrouping
    values:
      - foo
      - bar
      - baz
```

The attribute details for defining custom groupings are defined below.

## name \[required]

Every grouping definition needs to have a name. The name defines a key for the grouping.&#x20;

## values \[required]

A grouping key can have one or more possible values. The values keyword enumerates all possible values allowed for a grouping key.

## description \[required]

A description for a grouping is a human readable text that explains the purpose of the grouping/classification being done.

## Cardinality

When specifying a grouping for a destination, multiple values for the same key are allowed.
