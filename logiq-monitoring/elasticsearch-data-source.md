---
description: >-
  Elasticsearch data source provides a quick and flexible way to issue queries
  to one or more indexes in an Elasticsearch cluster
---

# Elasticsearch Data source

## Create the Elasticsearch data source

The first step in to create the data source and provide the Elasticsearch cluster URL and optionally provide  the basic auth `login` and `password`.

![Configuring the Elasticsearch data source](<../.gitbook/assets/Screen Shot 2020-08-10 at 5.26.18 PM.png>)

## Writing queries

In the query editor view, select the _Elasticsearch data source_ created above. On the left column, click on the refresh ![](<../.gitbook/assets/Screen Shot 2020-08-10 at 10.07.50 PM.png>) icon to refresh the schemas (indexes). The schemas are expandible and show the schema details.

![Refresh and lookup Elasticsearch indexes](<../.gitbook/assets/Screen Shot 2020-08-10 at 10.06.48 PM.png>)

 You can then proceed to the query editor and run the search query. The query uses JSON as passed to the Elasticsearch search API

![Writing a search query against an Elasticsearch index](<../.gitbook/assets/Screen Shot 2020-08-10 at 10.09.21 PM.png>)

