---
description: >-
  JSON Data source provides a quick and flexible way to issue queries to
  arbitrary RESTful endpoints that return JSON data.
---

# JSON Data source

## Create the JSON Data source

The first step in to create the data source and provide `basic auth` credentials. Note that basic auth credentials are optional and you can provide a bearer token if that is your means of authenticating against the API&#x20;

![Creating a JSON data source](<../.gitbook/assets/Screen Shot 2020-08-10 at 6.08.15 PM.png>)

## Writing queries

In the query editor, select the JSON data source created above and enter the query parameters. The query parameters use the YAML syntax. For E.g.

![](<../.gitbook/assets/Screen Shot 2020-08-10 at 6.07.39 PM.png>)

## Providing HTTP Options

The following HTTP options are used for sending a query

{% hint style="info" %}
The URL parameter is the only required parameter
{% endhint %}

* `url` - This is the URL where the RESTful API is exposed
* `method` - the HTTP method to use (default: `get`)
* `headers` - a dictionary of headers to send with the request
* `auth` - basic auth username/password (should be passed as an array: `[username, password]`)
* `params` - a dictionary of query string parameters to add to the URL
* `data` - a dictionary of values to use as the request body
* `json` - same as `data` except that it’s being converted to JSON

## Filtering response data: path and fields

The response data can be filtered by specifying the `path` and `fields` parameters. The `path` filter allows accessing attributes within the response for e.g. if a key `foo` in the response contains rows of objects you want to access, specifying `path` `foo` will convert each of the objects into rows.&#x20;

In the example below, we are then selecting `fields` _volumeInfo.authors, volumeInfo.title, volumeInfo.publisher and accessInfo.webReaderLink_

```
url: https://www.googleapis.com/books/v1/volumes?q=isbn:0747532699
path: items
fields: ["volumeInfo.authors","volumeInfo.title","volumeInfo.publisher","accessInfo.webReaderLink"]
```

The resulting data from the above query is a nicely formatted table that can be searched in LOGIQ or made available as a widget in a dashboard

![](<../.gitbook/assets/Screen Shot 2020-08-10 at 6.25.44 PM.png>)

