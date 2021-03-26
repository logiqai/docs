---
description: This page describes how to access report results via API
---

# Accessing Reports results via API

Once the report is created, its results can be accessed via APIs.  

{% api-method method="get" host="/api/queries/:queryid" path="" %}
{% api-method-summary %}
Get Query By Id
{% endapi-method-summary %}

{% api-method-description %}
Use this API to access the latest report result id
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="queryid" type="number" required=true %}
Id of the query
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
{
    '...' : '...",
    'latest_query_data_id' : 123,
    '...' : '...",
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

Once the results id is extracted invoke the results API to get the results 

{% api-method method="get" host="/api/query\_results/:result\_id" path="" %}
{% api-method-summary %}
Get Results by result\_id
{% endapi-method-summary %}

{% api-method-description %}
Access the latest report results
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="result\_id" type="number" required=true %}
Latest report result Id
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

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
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

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





