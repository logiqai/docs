# Credentials

A credential gives access details to the S3 storage resource so LOGIQ can drain the logs to your S3 compatible persistent store.

A credential is referenced in the destination section. For e.g.

```text
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

One or more credentials can be defined using the _**"credentials"**_ keyword. 

```text
credentials:
  - s3:
      name: production
      secret_key: wJalrXUtnFA9I/K7BDENA/bPxRfiCYEXNMPLEKEY
      access_key: AKIAIOSFODNN7EXAMPLE
```

The attributes for defining a single credential are defined below.

## s3 \[required\]

The _**"s3"**_ keyword is used to specify credentials for any S3/S3 compatible object store.

## name \[required\]

Every credential requires a unique name. It is referenced by this name in the configuration file when specified in a destination. The _**"name"**_ keyword is used to specify the name for the credential.

## secret\_key \[required\]

The _**"secret\_key"**_ keyword provides a secret or password that is part of the Access key used by the LOGIQ server to sign the request when it uses the S3 SDK to connect to an S3 compatible service.

## access\_key \[required\]

The _**"access\_key"**_ keyword provides an access or user identifier that is part of the Access key used by the LOGIQ server to sign the request when it used the S3 SDK to connect to an S3 compatible service.



