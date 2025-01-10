---
description: This page describes how to access report results via API
---

# Accessing Reports results via API

## Finding Query ID Via UI

Once the query is created in the UI editor interface, tested, and executed successfully.  The query ID can be looked at via the web URL address.

<figure><img src="../../../.gitbook/assets/query-id-2023-11-17_9-54-29.jpg" alt=""><figcaption><p><strong>Query ID</strong></p></figcaption></figure>

The query can then be accessed via API's using the query ID.

## Get Query By Id

<mark style="color:blue;">`GET`</mark> `/api/queries/:queryid`

Use this API to access the latest report result id

#### Path Parameters

| Name    | Type   | Description     |
| ------- | ------ | --------------- |
| queryid | number | Id of the query |

{% tabs %}
{% tab title="200 " %}
```
{
    '...' : '...",
    'latest_query_data_id' : 123,
    '...' : '...",
}
```
{% endtab %}
{% endtabs %}

The query result can be extracted via API via the query ID after the API query.

## Get Results by result\_id

<mark style="color:blue;">`GET`</mark> `/api/query_results/:result_id`

Access the latest report results

#### Path Parameters

| Name       | Type   | Description             |
| ---------- | ------ | ----------------------- |
| result\_id | number | Latest report result Id |

{% tabs %}
{% tab title="200 " %}
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
{% endtab %}
{% endtabs %}

## Python Example I

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

## Obtain API Key

API key can be obtained via the UI. &#x20;

<figure><img src="../../../.gitbook/assets/API-key-2023-11-17_10-13-15.jpg" alt=""><figcaption><p><strong>Retrieve API Key</strong></p></figcaption></figure>





## Python Example II

Based on a similar method, this query API directly queries the internal Prometheus data using the Prometheus database access API _logiq\_proxy_.

```python
import requests
import simplejson as json
import time

api_key = "<API_KEY>"
uri_result = input("Enter Query Result URL: ")
json_data = json.loads(input("Enter Query JSON Data: "))
file_name = "output_" + str(time.time()) + ".json"

def post_results_query():
    headers = {'Authorization': api_key}
    r = requests.post(uri_result, headers=headers, json=json_data, verify=False)
    r.raise_for_status()
    
    with open(file_name, 'w') as output:
        json.dump(r.json(), output, indent=3)
    print("<QueryResults>")
    print(json.dumps(r.json(), indent=3))
    print("</QueryResults>")
    print("JSON data saved in: " + file_name)

post_results_query()

#==========================================================
# Example for the logiq_proxy
# URL: 
#  https://lqnnn.logiq.ai/api/logiq_proxy
# Query Data: 
#  {"query": "(round(sum by (exported_namespace,app,severity)(increase(logiq_namespace_app_message_count{exported_namespace=~\"logiq:awesj\"}[3600s]))))&start=1700209381&end=1700212981","type": "query"}
#==========================================================
```
