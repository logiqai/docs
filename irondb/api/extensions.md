# Extensions

## Getting the List of Lua Extensions

This API call returns a list of all currently available Lua extensions on the node.

Data will be returned as a JSON object. The fields in this document are described below.

### Description

**URI**[**​**](https://docs.circonus.com/irondb/api/extensions#uri)

`/extension/lua`

**Method**[**​**](https://docs.circonus.com/irondb/api/extensions#method)

GET

**Inputs**[**​**](https://docs.circonus.com/irondb/api/extensions#inputs)

none

**Output**[**​**](https://docs.circonus.com/irondb/api/extensions#output)

* `<name>` : This key is the name of the upcoming extension. The value is another JSON object, defined as follows:
  * `params` : A JSON object containing the parameters for the extension. The JSON object is defined as follows:
    * `<param_name>` : This key is the name of the parameter. Each parameter will contain a JSON object defined as follows:
      * `name` : A description of the parameter.
      * `type` : The type of the parameter.
  * `description` : A text description of the Lua extension.

### Examples

```sh
curl http://127.0.0.1:8112/extension/lua
```

**Example 1 Output**[**​**](https://docs.circonus.com/irondb/api/extensions#example-1-output)

```json
{
  "example_ext": {
    "params": {
      "sample_param": {
        "name": "sample_param",
        "type": "integer"
      },
      "sample_param2": {
        "name": "sample_param2",
        "type": "string"
      }
    },
    "description": "A sample extension"
  },
  "example_ext2": {
    "params": {
      "sample_param": {
        "name": "sample_param",
        "type": "integer"
      },
      "sample_param2": {
        "name": "sample_param2",
        "type": "string"
      }
    },
    "description": "Another sample extension"
  }
}
```

## Executing a Lua Extension

This API call will execute a loaded Lua extension and return the results.

Refer to Getting The List of Lua Extensions for instructions on finding the list of available extensions.

### Description

**URI**[**​**](https://docs.circonus.com/irondb/api/extensions#uri-1)

`/extension/lua/<extension>`

**Method**[**​**](https://docs.circonus.com/irondb/api/extensions#method-1)

GET

**Inputs**[**​**](https://docs.circonus.com/irondb/api/extensions#inputs-1)

* `extension` : The extension to call. Any parameters for the extension may be passed via a query string.

**Output**[**​**](https://docs.circonus.com/irondb/api/extensions#output-1)

The output will vary based on the Lua extension called.

### Examples

```sh
curl http://127.0.0.1:8112/extension/lua/example_extension
```

In this example:

* `extension` : This is the command to execute an extension.
* `lua` : Indicates a Lua extension.
* `example_extension` : Extension name.

**Example 1 Output**[**​**](https://docs.circonus.com/irondb/api/extensions#example-1-output-1)

```json
{"got_result":"true"}
```

## Issuing CAQL Queries

The Circonus Analytics Query Language (CAQL) allows the user to issue complex queries against metric data residing in IRONdb. The CAQL Reference provides comprehensive documentation about functionality offered by the language.

### Description

**URI**[**​**](https://docs.circonus.com/irondb/api/extensions#uri-2)

`/extension/lua/caql_v1`

**Method**[**​**](https://docs.circonus.com/irondb/api/extensions#method-2)

GET

**Inputs**[**​**](https://docs.circonus.com/irondb/api/extensions#inputs-2)

Parameters can be submitted as url-encoded query string parameters or as JSON payload.

The following parameters are supported:

* `query` : The query to execute.
* `start` : The start time from which to pull data, represented in seconds since the epoch. This value is inclusive (data for the given start time will be pulled).
* `end` : The end time up to which data is pulled, represented in seconds since the epoch. This value is exclusive (data up to, but not including, the given end time will be pulled).
* `period` : The period, in seconds, for which to get data rollups.
* `_timeout` : Specify a timeout for CAQL processing in seconds. Optional. Default = 4.5.

### nExamples

```sh
echo '{
  "query":"12+3",
  "start":1474275000,
  "end":1474275240,
  "period":60
}' | curl http://127.0.0.1:8112/extension/lua/caql_v1 --data @-
```

Equivalently we can pass the paraemeters via the query string:

```sh
curl  'http://127.0.0.1:8112/extension/lua/caql_v1?start=1474275000&end=1474275240&period=60&query=12+3'
```

**Output**[**​**](https://docs.circonus.com/irondb/api/extensions#output-2)

```json
[
 [1474275000,[15]],
 [1474275060,[15]],
 [1474275120,[15]],
 [1474275180,[15]]
]
```
