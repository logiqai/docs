---
description: This page describes how to access report results via API
---

# Accessing Reports results via API

Once the report is created, its results can be accessed via APIs. &#x20;

{% swagger baseUrl="/api/queries/:queryid" path="" method="get" summary="Get Query By Id" %}
{% swagger-description %}
Use this API to access the latest report result id
{% endswagger-description %}

{% swagger-parameter in="path" name="queryid" type="number" %}
Id of the query
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
{
    '...' : '...",
    'latest_query_data_id' : 123,
    '...' : '...",
}
```
{% endswagger-response %}
{% endswagger %}

Once the results id is extracted invoke the results API to get the results&#x20;

{% swagger baseUrl="/api/query_results/:result_id" path="" method="get" summary="Get Results by result_id" %}
{% swagger-description %}
Access the latest report results
{% endswagger-description %}

{% swagger-parameter in="path" name="result_id" type="number" %}
Latest report result Id
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
{
   "query_result": {
      "id": 612,
      "query_hash": "e3a2707903f76a662079c4eb1376ecad",
      "query": "...",
      "data": {
         "rows": [
            {
               "timestamp": 1616729294000,
               "value": "39590",
               "groupby_host": "host1",
            },
            {
               "timestamp": 1616729294000,
               "value": "28555",
               "groupby_host": "host2",
            },
            {
               "timestamp": 1616729294000,
               "value": "2055",
               "groupby_host": "host3",
            }
         ],
         "columns": [
            {
               "friendly_name": "timestamp",
               "type": "datetime",
               "name": "timestamp"
            },
            {
               "friendly_name": "value",
               "type": "float",
               "name": "value"
            },
            {
               "friendly_name": "groupby_host",
               "type": "string",
               "name": "groupby_host"
            }
         ]
      },
      "data_source_id": 2,
      "runtime": 20.210840940475464,
      "retrieved_at": "2021-03-26T03:28:17.019Z"
   }
}
```
{% endswagger-response %}
{% endswagger %}

## Python Example

```python
import requests
import json


uri_query = 'https://logs.logiq.ai/api/queries/<query_id>'
uri_result = 'https://logs.logiq.ai/api/query_results/'

def post_query():
    # Add api key to header
    headers = {'Authorization': 'Key see_below_to_get_api_key'}
    # GET Query API to get latest_query_data_id
    r = requests.get(uri_query, headers=headers, verify=False)
    r.raise_for_status()
    # From the queries API extract the latest report id
    latest_report_id = r.json()['latest_query_data_id']
    # Construct the results url
    uri_result_end = uri_result + str(latest_report_id)
    # GET Results API
    qr = requests.get(uri_result_end, headers=headers, verify=False)
    qr.raise_for_status()
    # Prints results
    print(json.dumps(qr.json()['query_result']['data']['rows'], indent = 3))

post_query()
```

{% hint style="info" %}
[Refer here to get the API key ](../logiqctl/obtaining-api-key.md)
{% endhint %}



