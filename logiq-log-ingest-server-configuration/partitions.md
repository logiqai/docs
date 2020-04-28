# Partitions

A partition specifies a partitioning scheme for the incoming data for a given destination. A user can specify a partition scheme using any of the attributes in the incoming data. Partitioning of data is important to ensure good query performance. 

Partitioning schemes are defined in the configuration file using the _**"partitions"**_ keyword. 

```text
partitions:
  - name: p_by_day
    fields:
      - year
      - month
      - day
```

Once defined, the partition scheme can be referred in a destination to control data layout.

```text
destinations:
  - name: t_webservers
    partition: p_by_day
    .......
```

The attributes to define a partitions are detailed below.

## name \[required\]

The _**"name"**_ keyword defines a unique name for the partition scheme. This will be used to refer to the partitioning scheme in the rest of the configuration file

## fields \[required\]

The _**"fields"**_ keyword is a list of attributes that are part of the incoming data. Any of the data attributes can be used in the partition field. _The list of keys in an ordered list and gives the order in which the partition values are created._

NOTE: Once a partition scheme is attached to a destination, it cannot be changed and neither can the partition definition be altered.

## Valid attributes in fields

Following attributes are valid in fields

* namespace
* appname
* year
* month
* day



