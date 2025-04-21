# Data Retrieval

## Searching Tag Data

Find metrics using boolean tag search. Output is a JSON array of objects.

### Description

**URIs**[**​**](https://docs.circonus.com/irondb/api/data-retrieval#uris)

* `/find/<account_id>/tags?query=<query>&activity_start_secs=<start>&activity_end_secs=<end>&latest=<0|1|2>`
* `/find/<account_id>/tag_cats?query=<query>`
* `/find/<account_id>/tag_vals?query=<query>`

**Method**[**​**](https://docs.circonus.com/irondb/api/data-retrieval#method)

GET

**Inputs**[**​**](https://docs.circonus.com/irondb/api/data-retrieval#inputs)

* `account_id` : The account to search
* `query` : See [Tag Queries](../metric-names-and-tags.md#tag-queries) for more info on tag queries.
* `activity_start_secs` : (optional) The start time from which to pull data, represented in seconds since the unix epoch.
* `activity_end_secs` : (optional) The end time up to which data is pulled, represented in seconds since the unix epoch.
* `activity` : (optional, default 1) Specify if the return set should include activity window data.
  * 0 : Do not return activity window data. This is useful for reducing payload size if the data is not needed.
  * 1 : Include activity window in the return set.
* `latest` : (optional, default 0) Specify if the latest values for the metric should be returned. Parameters:
  * 0 : Do not return latest values.
  * 1 : Return latest values if it is a no-work operation
  * 2 : Return latest values even if work must be performed, and turn on tracking for this metric so it will be "free" for later calls.
* `count_only` : (optional, default 0) Only return the total count, not individual metrics. Will also return an "estimate" boolean. This will be true if a node is down making a true count impossible.
* 'X-Snowth-Verify-Owner\` : (optional, normally default false, during a cluster rebalance default true) This HTTP Header can be set to "true" on a request forcing validation of a node's locality of data. This extra validation step is expensive and should not be used typically outside of debugging.

### Output

**`/find/174/tags?query=and(__name:foo)`**[**​**](https://docs.circonus.com/irondb/api/data-retrieval#find174tagsqueryand__namefoo)

Return all metrics matching a tag query along with information about those metrics.

If [activity tracking](../administration/activity-tracking.md) is [turned on](../getting-started/configuration.md#surrogate_database) this will include activity windows for the metric.

If latest value tracking is [turned on](../getting-started/configuration.md#surrogate_database) and/or requested for this metric, this will include the 2 most recent value tuples for the metric, if available. The two most recent values are provided so that a caller can calculate a derivative if desired. If called in "no-work" mode (1) and no value is freely available, an empty object will be returned.

```json
[
  {
    "uuid": "9aae16cd-4427-4330-8bd8-5c4cd176e67e",
    "check_name": "some name here",
    "metric_name": "foo|ST[app:myapp,region:us-east-1]",
    "category": "reconnoiter",
    "type": "numeric",
    "account_id": 174,
    "activity": [
      [ 1558029600, 1558032300 ],
      [ 1559746800, 1569273300 ]
    ],
    "latest": {
      "numeric": [
        [ 1569271882337, 2991012437 ],
        [ 1569271942930, 2991020000 ]
      ]
    }
  }
]
```

**`/find/174/tag_cats?query=and(__name:foo)`**[**​**](https://docs.circonus.com/irondb/api/data-retrieval#find174tag_catsqueryand__namefoo)

Return the categories of the incoming query.

```json
[
   "app",
   "region"
]
```

**`/find/174/tag_vals?query=and(__name:foo)`**[**​**](https://docs.circonus.com/irondb/api/data-retrieval#find174tag_valsqueryand__namefoo)

Return the values of the incoming query.

```json
[
   "myapp",
   "us-east-1"
]
```

## Retrieving and Transforming Data

The /fetch API provides fast, one-request access to common complex data extraction requirements. It allows for fetch submissions in both FlatBuffers and JSON formats, and returns DF4 output format available in both FlatBuffers and JSON encoding.

### Description of API

**URI**[**​**](https://docs.circonus.com/irondb/api/data-retrieval#uri)

`/fetch`

**Method**[**​**](https://docs.circonus.com/irondb/api/data-retrieval#method-1)

POST

**Inputs**[**​**](https://docs.circonus.com/irondb/api/data-retrieval#inputs-1)

* A document describing the streams to fetch, how to transform them, and reduce them into a result set.

**Fetch JSON**[**​**](https://docs.circonus.com/irondb/api/data-retrieval#fetch-json)

```json
{ "start": <double epoch seconds>,
  "period": <double seconds>,
  "count": <positive integer>,
  "streams": [
    { ... stream definition ... },
    ...
  ],
  "reduce": [
    { ... reduce definition ... },
    ...
  ]
}
```

A stream definition form:

```
{ "uuid": <uuid>,
  "name": <canonical name of metric>,
  "kind": <numeric|histogram|text>,
  "transform": <transform>,
  "transform_params": [ string parameter list ]
}
```

A reduce definition form:

```
{ "label": <string label>,
  "method": <reduce method>,
  "method_params": [ string parameter list ]
}
```

**Transforms**[**​**](https://docs.circonus.com/irondb/api/data-retrieval#transforms)

**Numeric (`kind` = `numeric`)**[**​**](https://docs.circonus.com/irondb/api/data-retrieval#numeric-kind--numeric)

* `average` - the average of measurements in the period.
* `sum` - the sum of measurements in the period.
* `count` - the number of measurements in the period.
* `counter` - the positive rate of change of the measurements in the period.
* `counter_stddev` - the standard deviation of the positive rate of change of the measurements in the period.
* `derivative` - the rate of change of the measurements in the period.
* `derivative_stddev` - the standard deviation of the rate of change of the measurements in the period.
* `stddev` - the standard deviation of measurements in the period.

**Histogram (`kind` = `histogram`)**[**​**](https://docs.circonus.com/irondb/api/data-retrieval#histogram-kind--histogram)

* `none` - pass the input through unmodified.
* `count` - the number of samples in each histogram.
* `rate` - the number of samples per second in each histogram (count/period).
* `count_above` - calculate the number of samples that are greater than the supplied parameter.
  * `transform_params` the threshold value for measurements.
* `count_below` - calculate the number of samples that are less than the supplied parameter.
  * `transform_params` the threshold value for measurements.
* `inverse_percentile` - calculate what percentage of the population is smaller than the supplied parameter (output in \[0,100] or NaN)
  * `transform_params` the threshold value for measurements.
* `inverse_quantile` - calculate what ratio of the popultion is smaller than the supplied parameter (output in \[0,1] or NaN)
  * `transform_params` the threshold value for measurements.
* `percentile` - produce a numeric quantile after dividing the parameter by 100.
  * `transform_params` a value in the range \[0,100]
* `quantile` - produce a numeric quantile
  * `transform_params` a value in the range \[0,1]
* `sum` - approximate sum of the samples in each histogram
* `mean` - approximate mean value of the samples in each histogram

**Text (`kind` = `text`)**[**​**](https://docs.circonus.com/irondb/api/data-retrieval#text-kind--text)

* `none` - pass the input through unmodified.
* `count` - return a numeric count of the number of text entries in the period.
* `count_cumulative` - return a cumulative count of text entries starting at zero for the first period requested.
* `count_distinct` - return a numeric count of the number of unique text entries in the period.
* `count_distinct_cumulative` - return the total distinct values seen from the beginning of the first period requested through the end of the current period.
* `count_transition` - return a numeric count of the number of times a text entries changes during the period. The first period's first value does not count as a transition.
* `count_transition_cumulative` - return the cumulative transitions seen from the beginning of the first period requested through the end of the current period.
* `rate` - return the text entries per second seen in each period.
* `rate_distinct` - return the unique text entries per second in each period.
* `rate_distinct_cumulative` - return the newly unique text entries per second in each period.
* `rate_transition` - return the number of text entry changes per second in each period.

**Reductions**[**​**](https://docs.circonus.com/irondb/api/data-retrieval#reductions)

**`pass` - pass the inputs to outputs unmodified**[**​**](https://docs.circonus.com/irondb/api/data-retrieval#pass---pass-the-inputs-to-outputs-unmodified)

* `method_params` none
* Inputs can be numeric, histogram, or text.

**`groupby_mean` - group inputs and calculate a mean over the grouping**[**​**](https://docs.circonus.com/irondb/api/data-retrieval#groupby_mean---group-inputs-and-calculate-a-mean-over-the-grouping)

* `method_params` a list of tag categories on which to perform grouping
* Inputs must be numeric.

**`groupby_sum` - group inputs and calculate a sum over the grouping**[**​**](https://docs.circonus.com/irondb/api/data-retrieval#groupby_sum---group-inputs-and-calculate-a-sum-over-the-grouping)

* `method_params` a list of tag categories on which to perform grouping
* Inputs must be numeric.

**`groupby_merge` - group inputs and merge into a histogram stream**[**​**](https://docs.circonus.com/irondb/api/data-retrieval#groupby_merge---group-inputs-and-merge-into-a-histogram-stream)

* `method_params` a list of tag categories on which to perform grouping
* Inputs must be either numeric or histogram.

**`mean` - calculate the mean across input streams**[**​**](https://docs.circonus.com/irondb/api/data-retrieval#mean---calculate-the-mean-across-input-streams)

* `method_params` none
* Inputs must be numeric.

**`merge` - group inputs and merge into a histogram stream**[**​**](https://docs.circonus.com/irondb/api/data-retrieval#merge---group-inputs-and-merge-into-a-histogram-stream)

* `method_params` none
* Inputs must be either numeric or histogram.

**`sum` - calculate the sum across input streams**[**​**](https://docs.circonus.com/irondb/api/data-retrieval#sum---calculate-the-sum-across-input-streams)

* `method_params` none
* Inputs must be numeric.

**`topk` - filter a set of inputs to the top K**[**​**](https://docs.circonus.com/irondb/api/data-retrieval#topk---filter-a-set-of-inputs-to-the-top-k)

* `method_params` : `[ K, <mech>, <mech_param> ]`
*   Inputs must be either numeric or histogram.

    Allowable `mech` values are `mean` (default), `max`, or `quantile`. The `quantile` `mech` value requires a `mech_param` in the range \[0,1]. All measurements in the input stream are accumulated and a mean or quantile is calculated. This calculated value is used as a rank for the stream and the K largest ranks are selected and passed to the output set.

## Retrieving Graphite Data

Fetches Graphite-style data. This is similar to the [rollup](data-retrieval.md) endpoint but the data returned is always **average** data and this endpoint will scale the `rollup_span` to match the time range of data requested.

See [graphite rendering](../integrations/graphite.md#get).

## Retrieving Raw Data

_This is legacy endpoint. It is recommended to use the_ [_Fetch_](data-retrieval.md) _endpoint for all data reads._

Fetches raw (full resolution) numeric data from the [raw database](../getting-started/configuration.md#raw_database). Data is returned as an array of tuples of `[timestamp in milliseconds, value]`

### Description

**URI**[**​**](https://docs.circonus.com/irondb/api/data-retrieval#uri-1)

`/raw/<uuid>/<metric>?start_ts=<start>&end_ts=<end>`

**Method**[**​**](https://docs.circonus.com/irondb/api/data-retrieval#method-2)

GET

**Inputs**[**​**](https://docs.circonus.com/irondb/api/data-retrieval#inputs-2)

* `metric` : The name of the metric for which to pull data (url encoded).
* `uuid` : The UUID of the check to which the metric belongs.
* `start_ts` : The start time from which to pull data, represented in seconds.milliseconds since the unix epoch.
* `end_ts` : The end time up to which data is pulled, represented in seconds.milliseconds since the unix epoch.

> A note on the `start_ts` and `end_ts` parameters:

The format is `<seconds since epoch>.<milliseconds>`. In terms of printf, it is `%lu.%03lu`, i.e., `1516820826.120`. **While this might look like a float,** it is, in fact, a strict textual format that requires exactly three digits after the decimal point. These must always be included, even if they are `000`.

For example, 12345.6 does **not** mean 12345 seconds and 600 milliseconds; it is an illegal format. The `<milliseconds>` portion of the timestamp must always be 3 digits to represent values from 000 to 999.

### Examples

```sh
curl http://127.0.0.1:8112/raw/fc85e0ab-f568-45e6-86ee-d7443be8277d/online?start_ts=1529509020.000&end_ts=1529509200.000
```

In this example:

* `raw` : The raw command
* `fc85e0ab-f568-45e6-86ee-d7443be8277d` : The UUID of the check
* `online` : The name of the metric to retrieve data for
* `1529509020.000` : 2018-06-20T15:37:00+00:00 and zero milliseconds
* `1529509200.000` : 2018-06-20T15:40:00+00:00 and zero milliseconds

**Example 1 Output**[**​**](https://docs.circonus.com/irondb/api/data-retrieval#example-1-output)

```
[[1529509063064,0],[1529509122985,0],[1529509183764,0]]
```

Note that the returned timestamps are **milliseconds** since unix epoch and represent the timestamp on each incoming data row.

## Retrieving Rollup Data

_This is legacy endpoint. It is recommended to use the_ [_Fetch_](data-retrieval.md) _endpoint for all data reads._

This API call is for retrieving numeric data from the IRONdb cluster with fine grained control over the `rollup_span`. It will return an array with all the timestamps from the time given, along with the attendant data.

Data will be returned in an array of tuples. Each tuple will contain a timestamp and the value that was requested. If "all" data is requested, the value returned is a hash with the name of each value and the value itself.

### Description

**URI**[**​**](https://docs.circonus.com/irondb/api/data-retrieval#uri-2)

`/rollup/<uuid>/<metric_name>?start_ts=<start>&end_ts=<end>&rollup_span=<milliseconds>&get_engine=(dispatch|nnt|recalc)&type=<see below>`

**Method**[**​**](https://docs.circonus.com/irondb/api/data-retrieval#method-3)

GET

**Inputs**[**​**](https://docs.circonus.com/irondb/api/data-retrieval#inputs-3)

* `metric` : The name of the metric for which to pull data (url encoded).
* `uuid` : The UUID of the check to which the metric belongs.
* `start_ts` : The start time from which to pull data, represented in seconds.milliseconds since the unix epoch.
* `end_ts` : The end time up to which data is pulled, represented in seconds.milliseconds since the unix epoch.
* `rollup_span` : The granularity of the rollup with a units suffix (`s` for seconds, `ms` for milliseconds. See example below)
* `get_engine` :
  * `dispatch` means - read first from rolled up data and then fill in with recalculated raw data.
  * `nnt` means - only read already rolled up data.
  * `recalc` means - read only raw data and generate rollups on the fly.
* `type` : The type of data for which to pull results. Possible values for this input are as follows:
  * `count` : The number of data points received for the metric over the specified time period.
  * `average` : The average value for the metric over the specified time period.
  * `derive` : The derivative value for the metric over the specified time period.
  * `derivative` : The derivative value for the metric over the specified time period.
  * `counter` : The counter value for the metric over the specified time period.
  * `average_stddev` : The standard deviation of the average value for the metric over the specified time period.
  * `derive_stddev` : The standard deviation of the derivative value for the metric over the specified time period.
  * `derivative_stddev` : The standard deviation of the derivative value for the metric over the specified time period.
  * `counter_stddev` : The standard deviation of the counter value for the metric over the specified time period.
  * `derive2` : The second-order derivative value for the metric over the specified time period.
  * `derivative2` : The second-order derivative value for the metric over the specified time period.
  * `counter2` : The second-order counter value for the metric over the specified time period.
  * `derive2_stddev` : The standard deviation of the second-order derivative value for the metric over the specified time period.
  * `derivative2_stddev` : The standard deviation of the second-order derivative value for the metric over the specified time period.
  * `counter2_stddev` : The standard deviation of the second-order counter value for the metric over the specified time period.
  * `all` : All of the above data.

If `type` is omitted, the **average** is returned for each period.

> A note on the `start_ts` and `end_ts` parameters:

The format is `<seconds since epoch>.<milliseconds>`. In terms of printf, it is `%lu.%03lu`, i.e., `1516820826.120`. **While this might look like a float,** it is, in fact, a strict textual format that requires exactly three digits after the decimal point. These must always be included, even if they are `000`.

For example, 12345.6 does **not** mean 12345 seconds and 600 milliseconds; it is an illegal format. The `<milliseconds>` portion of the timestamp must always be 3 digits to represent values from 000 to 999.

### Examples

```sh
curl http://127.0.0.1:8112/rollup/fc85e0ab-f568-45e6-86ee-d7443be8277d/online?start_ts=1529509020.000&end_ts=1529509200.000&rollup_span=60000ms&type=all&get_engine=recalc
```

In this example:

* `rollup` : The rollup command
* `fc85e0ab-f568-45e6-86ee-d7443be8277d` : The UUID of the check
* `online` : The name of the metric to retrieve data for
* `start_ts=1529509020.000` : 2018-06-20T15:37:00+00:00 and zero milliseconds
* `end_ts=1529509200.000` : 2018-06-20T15:40:00+00:00 and zero milliseconds
* `rollup_span=60000ms` : Rollup at 60000 milliseconds (1 minute)
* `type=all` : Get all rollup fields
* `get_engine=recalc` : Recalculate the rollup from the raw database

**Example 1 Output**[**​**](https://docs.circonus.com/irondb/api/data-retrieval#example-1-output-1)

```json
[
  [
    1529509020,
    {
      "count": 1,
      "value": 0,
      "stddev": 0,
      "derivative": 0,
      "derivative_stddev": 0,
      "counter": 0,
      "counter_stddev": 0,
      "derivative2": 0,
      "derivative2_stddev": 0,
      "counter2": 0,
      "counter2_stddev": 0
    }
  ],
  [
    1529509080,
    {
      "count": 1,
      "value": 0,
      "stddev": 0,
      "derivative": 0,
      "derivative_stddev": 0,
      "counter": 0,
      "counter_stddev": 0,
      "derivative2": 0,
      "derivative2_stddev": 0,
      "counter2": 0,
      "counter2_stddev": 0
    }
  ],
  [
    1529509140,
    {
      "count": 1,
      "value": 0,
      "stddev": 0,
      "derivative": 0,
      "derivative_stddev": 0,
      "counter": 0,
      "counter_stddev": 0,
      "derivative2": 0,
      "derivative2_stddev": 0,
      "counter2": 0,
      "counter2_stddev": 0
    }
  ]
]
```

Timestamps in the returned data will take on the `<seconds>.<milliseconds>` format if the rollup span requires that resolution.

## Retrieving Text Data

_This is legacy endpoint. It is recommended to use the_ [_Fetch_](data-retrieval.md) _endpoint for all data reads._

This API call is for retrieving text data from the Snowth cluster. It will return an array with all the timestamps from the time given, along with the attendant data.

Data will be returned in an array of tuples. Each tuple will contain a timestamp that indicates when the text value was received (given in milliseconds since the epoch), as well as the text value itself. The database contains all text samples submitted, but the stream is returned, by default, as a front-edge-triggered list. In otherwords, if the same value is submitted multiple times sequentially, the result set fetched will have only the first occurrence or the "front-edge" of the signal.

### Description

**URI**[**​**](https://docs.circonus.com/irondb/api/data-retrieval#uri-3)

`/read/<start>/<end>/<uuid>/<metric>`

**Method**[**​**](https://docs.circonus.com/irondb/api/data-retrieval#method-4)

GET

**Inputs**[**​**](https://docs.circonus.com/irondb/api/data-retrieval#inputs-4)

* `start` : The start time from which to pull data, represented in seconds since the epoch. This value is inclusive (data for the start time given will be pulled).
* `end` : The end time from which to pull data, represented in seconds since the epoch. This value is exclusive (data up to, but not including, the given end time will be pulled).
* `uuid` : The UUID of the check to which the metric belongs.
* `metric` : The name of the metric for which to pull data.

**Querystring Paramters**[**​**](https://docs.circonus.com/irondb/api/data-retrieval#querystring-paramters)

* `get_specific_range=<true|false>` will ensure all timestamps are within the start/end boundary and return every sample (not compressing duplicates to their starting edge. The default is `false`.
* `lead=<true|false>` will include the point before `start` if there is no point exactly at `start` and such a point exists. The default is `true`.

### Examples

```sh
curl http://127.0.0.1:8112/read/1380000000/1380000600/6f6bdc73-2352-4bdc-ab0e-72f66d0dee12/text_example
```

In this example:

* `read` : This is the command to read data from the server.
* `1380000000` : This is the Start Time (September 24, 2013, 05:20:00 GMT).
* `1380000600` : This is the End Time (September 24, 2013, 05:30:00 GMT).
* `6f6bdc73-2352-4bdc-ab0e-72f66d0dee12` : This is the Check UUID.
* `text_example` : This is the Metric Name.

**Example 1 Output**[**​**](https://docs.circonus.com/irondb/api/data-retrieval#example-1-output-2)

```json
[[1380000000555,"test_value"],[1380000300123,"test_value_2"]]
```

## Retrieving Histogram Data

_This is legacy endpoint. It is recommended to use the_ [_Fetch_](data-retrieval.md) _endpoint for all data reads._

This API call is for retrieving histogram data from the IRONdb cluster. It will return an array with all the timestamps from the time given, along with the attendant data.

Data will be returned in an array of arrays. Each sub-array will contain three elements: a timestamp, the period requested, and a JSON object representing the number of times that different values appeared in that time period.

### Description of Arrays

**URI**[**​**](https://docs.circonus.com/irondb/api/data-retrieval#uri-4)

`/histogram/<start>/<end>/<period>/<uuid>/<metric>`

**Method**[**​**](https://docs.circonus.com/irondb/api/data-retrieval#method-5)

GET

**Inputs**[**​**](https://docs.circonus.com/irondb/api/data-retrieval#inputs-5)

* `start` : The start time from which to pull data, represented in seconds since the epoch. This value is inclusive (data for the given start time will be pulled).
* `end` : The end time up to which data is pulled, represented in seconds since the epoch. This value is inclusive (data up to the given end time will be pulled).
* `period` : The period, in seconds, for which to get data rollups.
* `uuid` : The UUID of the check to which the metric belongs.
* `metric` : The name of the metric for which to pull data.

### Examples

```sh
curl http://127.0.0.1:8112/histogram/1380000000/1380000600/300/6f6bdc73-2352-4bdc-ab0e-72f66d0dee12/hist_example
```

In this example:

* `histogram` : This is the command to read histogram data from the server.
* `1380000000` : This is the Start Time (September 24, 2013, 05:20:00 GMT).
* `1380000600` : This is the End Time (September 24, 2013, 05:30:00 GMT).
* `300` : This the Period (300 Seconds or 5 Minutes).
* `6f6bdc73-2352-4bdc-ab0e-72f66d0dee12` : This is the UUID.
* `hist_example` : This is the Metric Name.

For the output of this example, assume that for every five-minute window, a different value between 1 and 5 was received at every one-minute interval.

**Example 1 Output**[**​**](https://docs.circonus.com/irondb/api/data-retrieval#example-1-output-3)

```json
[
  [
    1380000000,
    300,
    {
      "1": 1,
      "2": 1,
      "3": 1,
      "4": 1,
      "5": 1
    }
  ],
  [
    1380000300,
    300,
    {
      "1": 1,
      "2": 1,
      "3": 1,
      "4": 1,
      "5": 1
    }
  ]
]
```
