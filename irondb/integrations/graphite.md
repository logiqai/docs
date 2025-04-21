# Graphite

IRONdb is a drop-in replacement for Graphite's Whisper database.

It supports ingestion from Carbon sources like carbon-relay and carbon-c-relay. [Graphite-irondb](../tools/graphite-plugin.md) is a storage finder plugin that allows IRONdb to seamlessly integrate with an organization's existing Graphite-web deployment.

The [IRONdb Relay](../tools/irondb-relay.md) is a scalable, drop-in replacement for carbon-relay or carbon-c-relay.

## Graphite Ingestion

The format for ingestion is the typical Carbon plaintext format:

`dot.separated.metric.name<space>12345.56<space>1480371755`

If you desire higher resolution data capture, IRONdb does support a variant of the unix epoch timestamp (3rd field) where you can suffix the timestamp with a period, followed by the number of milliseconds in the second. For example:

`dot.separated.metric.name<space>12345.56<space>1480371964.123`

This example means `123 milliseconds` into the timestamp `1480371964` or `November 28, 2016 10:26:04 and 123ms PM UTC`

**Note that, while it resembles a floating point number, this is not a float.**

Starting with IRONdb release `0.12` you can also ingest _tagged_ graphite data. Tagged graphite data has the following format:

`dot.separated.metric.name;category1=value1;category2=value2`

Where tags are appended to the normal name and are separated by semicolons (`;`).

For more info on the graphite tag format see: [Graphite Tag Support](http://graphite.readthedocs.io/en/latest/tags.html).

## Namespacing

Graphite ingestion into IRONdb requires namespacing your graphite data. This lets you associate a UUID/Name and numeric identifier with the incoming metrics. This is useful, for example, if you want to use a single IRONdb installation to service multiple different internal groups in your organization but keep metrics hidden across the various groups.

All metrics live under a numeric identifier (you can think of this like an account\_id). Metric names can only be associated with an "account\_id". This allows you have separate graphite-web or Grafana instances that segregate queries for metric names, or combine them all together under a single "account\_id", or even separate your internal groups but recombine them under graphite-web/Grafana for visualization purposes. It's really up to you.

## Optional Configuration

Graphite ingestion will, by default, accept timestamps up to 1 year in the past. When retrieving Graphite data, a floor of 1-minute resolution is used, to prevent gaps if the requested period is shorter. These values may be changed through [configuration](../getting-started/configuration.md#graphite-config).

## Writing Graphite Data with Network Listener

The network listener requires that we associate an account\_id, uuid, and name with a network port. This is added to the [IRONdb configuration file](../getting-started/configuration.md#listeners) during initial installation, for the default Graphite text protocol port (2003). Additional stanzas may be added, associating different IDs with different ports to segregate incoming traffic.

```xml
    <listener address="*" port="2004" type="graphite">
      <config>
        <check_uuid>8c01e252-e0ed-40bd-d4a3-dc9c7ed3a9b2</check_uuid>
        <account_id>1</account_id>
      </config>
    </listener>
```

You can then use:

```sh
echo "my.metric.name.one 1 `date +%s`" | nc 2004
```

to send metrics to IRONdb.

See also the [IRONDB-relay](../tools/irondb-relay.md)

## Graphite Rendering

IRONdb has a graphite-web Storage Backend which makes the following Graphite Rendering seamless with an existing graphite-web installation. The Storage Backend requires graphite 0.10 or newer and can be obtained [here](../tools/graphite-plugin.md):

Follow the instructions in the README in that repo to install and utilize the IRONdb graphite storage backend.

That Storage Backend plugin simply utilizes the endpoints described below.

## Query Result Limits

All query results are subject to limits to control the number of results returned. If not otherwise specified, queries will be limited to the first 10,000 results returned.

This limit may be changed by setting a request header, `x-snowth-advisory-limit`, with one of the following values:

* A positive integer representing the desired limit
* -1 or "none" to remove the limit

If the header contains any other value or is not present, the default of 10,000 will be used.

## Searching for Metric Names

Graphite metrics can be fetched (rendered) from IRONdb using the following endpoints. Glob style wildcards are supported.

`http://<host:port>/graphite/<account_id>/<optional_query_prefix>/metrics/find?query=foo.*`

This will return a JSON document with metrics matching the prefix: `foo.` which terminate at that level. Continuing on the example in Graphite Ingestion, the above example could return the following:

```json
[
        {"leaf": false, "name":"foo.dev"},
        {"leaf": false, "name":"foo.prod"}
]
```

When a metric is a leaf node, `leaf` will be true and that metric will be queryable for actual datapoints.

The `optional_query_prefix` can be used to simplify metric names. You can place any non-glob part of the prefix of a query into the `optional_query_prefix` and that prefix will be auto-prefixed to any incoming query for metric names. For example:

`http://<host:port>/graphite/1/foo./metrics/find?query=*`

Will return:

```json
[
        {"leaf": false, "name":"dev"},
        {"leaf": false, "name":"prod"}
]
```

Note that the `optional_query_prefix` is omitted from the response json. You would use this feature to simplify all metric names in graphite-web or Grafana.

If you do not want to utilize the `optional_query_prefix` you can leave it off the URL:

`http://<host:port>/graphite/1/metrics/find?query=foo.*`

```json
[
        {"leaf": false, "name":"foo.dev"},
        {"leaf": false, "name":"foo.prod"}
]
```

## Searching for Tags

Graphite metrics can be fetched (rendered) from IRONdb using multi-dimensional tag queries.

`http://<host:port>/graphite/<account_id>/<optional_query_prefix>/tags/find?query=<tag query>`

This will return a JSON document with metrics matching the `<tag query>`. Tag query syntax is the same as supported by Graphite version >= 1.1. See [Graphite Tag Querying](http://graphite.readthedocs.io/en/latest/tags.html#querying)

The syntax is:

```
tag=spec    tag value exactly matches spec
tag!=spec   tag value does not exactly match spec
tag=~value  tag value matches the regular expression spec
tag!=~spec  tag value does not match the regular expression spec
```

`http://<host:port>/graphite/1/tags/find?query=category1=value1`

```json
[
        {"leaf": false, "name":"graphite.dev;category1=value1", "leaf_data": {...}},
        {"leaf": false, "name":"graphite.prod;category1=value1", "leaf_data": {...}}
]
```

## Retrieving Datapoints

There are 2 methods for retrieving datapoints from IRONdb. A GET and a POST.

### GET

For retrieving an individual metric name, use:

`http://<host:port>/graphite/<account_id>/<optional_query_prefix>/series?start=<start_timestamp&end=<end_timestamp>&name=<metric_name>`

where `<start_timestamp>` and `<end_timestamp>` are expressed in unix epoch seconds, and `<metric_name>` is the originally ingested leaf node returned from the `/metrics/find` query above. `optional_query_prefix` follows the same rules as described in the prior section.

### POST

For fetching batches of time series data all at once, IRONdb provide a POST interface to send multiple names at the same time. To use this, POST a json document of `Content-type: application/json` to the following url:

`http://<host:port>/graphite/<account_id>/<optional_query_prefix>/series_multi`

The document format:

```json
{
        "start": <start_timestamp>,
        "end" : <end_timestamp>,
        "names" : [ "graphite.dev.metric.one", "graphite.prod.metric.two"]
}
```

`optional_query_prefix` follows the same rules as the prior sections. If you provide an `optional_query_prefix` you would omit that portion of the metric name from the names in the JSON document. For example:

`http://<host:port>/graphite/1/graphite./series_multi`

The document format:

```json
{
        "start": 0,
        "end" : 12345,
        "names" : [ "dev.metric.one", "prod.metric.two"]
}
```

## Native Whisper Read Support

IRONdb has the capability of reading Whisper database files directly, making historical Graphite data available to be queried. Writing new data to Whisper format is not supported.

To make an existing hierarchy of Whisper content available, the starting directory must be made available to all IRONdb nodes. Depending on operator preference, this may involve copying the directory structure and its files to each IRONdb node, or making a shared mountpoint available over a networked filesystem such as NFS, and mounting it at the same location on each IRONdb node. In all cases, the filesystem should be mounted read-only.

Multiple collections of Whisper data are also supported, such as from disparate Graphite installations. Each collection can be exposed to IRONdb individually, and may be segregated from one another using different IRONdb check UUIDs and/or account IDs. See [Namespacing](graphite.md#namespacing) above for details on how check UUIDs and account IDs are used.

To configure one or more Whisper directories, see [Graphite Configuration](../getting-started/configuration.md#graphite-config).

Once Whisper directories are configured, they must be scanned and indexed in order for IRONdb to actually find and read them. The `whisper_loader` tool will read the IRONdb configuration and build an inventory. The inventory file records each metric name, along with the time range it covers, the aggregation function it uses, and the check UUID and account ID that it will be associated with.

**NOTE:** IRONdb only supports `average` and `sum` aggregation functions. Whisper databases using `min`, `max`, or `last` will be treated as if they were using `average`.

This inventory is then used as input on each IRONdb node to populate its local metric name index. The IRONdb service must be running on all nodes.

Full usage information may be obtained via:

```sh
/opt/circonus/bin/whisper_loader -h
```

Procedure:

1. Make the desired Whisper directory (or directories) visible on each IRONdb node. The directory structure must look the same to each node, whether via locally copied files or shared filesystem mount.
2.  Select one IRONdb node on which to run the loader tool in "discovery mode", and run it:

    ```sh
    /opt/circonus/bin/whisper_loader -c /opt/circonus/etc/irondb.conf \
        -i /var/tmp/whisper_inventory
    ```
3. Copy the inventory file to the remaining IRONdb nodes.
4.  On each IRONdb node, including the one where discovery was done, run the tool in "submit mode", which will read the inventory file and create local metric name index entries:

    ```sh
    /opt/circonus/bin/whisper_loader -c /opt/circonus/etc/irondb.conf \
        -i /var/tmp/whisper_inventory -s
    ```

As with ordinary metric ingestion, each Whisper metric will be "owned" by a subset of IRONdb nodes. As the inventory is processed in submit mode, any metric that is not owned by the local node will simply be skipped.
