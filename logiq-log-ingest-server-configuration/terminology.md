---
description: >-
  Description of LOGIQ platform terminology that is used elsewhere in the
  documentation.
---

# Terminology

This section covers commonly used terminology in our documentation, ui, source code when referring to the LOGIQ configuration file

## Credential

A credential gives access details to the S3 storage resource so LOGIQ can drain the logs to your S3 compatible persistent store. A credential is referenced in the destination section.

## Destination

A destination is a store for the data. Incoming data streams are processed and eventually land into one or more of the destinations specified in the configuration file.

## Filter

A Filter performs a boolean expression evaluation based on the incoming data fields. It returns a _**"true"**_ or _**"false"**_ evaluation. A filter is attached to a rule. The filter condition must evaluate to _**"true"**_  for the data to be stored at the destination specified in the rule.

## Grouping

A Grouping is a key value pair that tags data ingested by the LOGIQ server. It is defined on a destination.&#x20;

## Partition

A partition specifies a partitioning scheme for the incoming data for a given destination. A user can specify a partition scheme using any of the attributes in the incoming data.

## Rule

A Rule determine how incoming data is mapped to a bucket. LOGIQ server can manage multiple buckets and manage data flowing into them simultaneously via multiple rules.

## Source

A source is one or more clients sending data to the LOGIQ server.
