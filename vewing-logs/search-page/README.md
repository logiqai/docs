---
description: >-
  The search happens at the namespace level, select namespace enter the search
  term to get started.
---

# Search Page

On the search Page, you can:

* Access every log entry in the selected namespace that matches your search pattern.
* Make use of advanced search modal to build complex queries
* Filter the search results using Facets
* Get field-level details about the entries that match your search
* Create a **Metric**
* Create a **Report**
* Export data&#x20;

![](<../../.gitbook/assets/flash-high-level-search-empty (1).png>)

The search happens at the namespace level, select the namespace and applications, enter the search term to get started. By default, Search shows data for the last 15 minutes. If no data displays, try increasing the time range. Using the time filter, you can specify a common or recently-used time range, a relative time from now, or an absolute time range.

With the help of the advanced search modal, complex search expressions can be created. &#x20;

![](<../../.gitbook/assets/flash-high-level-advanced search.png>)

A successful search reveals a graph with a time-series view of logs, a table with facets and logs.

![](<../../.gitbook/assets/flash-high-level-search-available (1).png>)

### Filter data using Facets

Use facets to narrow your search results. Logiq's intelligent parsing engine extracts facets at the time of data ingestion. By default selecting a facet only filters the data loaded in the browser. If the data is not available, click on the "apply" button to fetch more results.

### View Log Detail

Expand the caret available in each row to see the log in detail.&#x20;

![](../../.gitbook/assets/flash-high-level-search-expand.png)

The dots available on each line will reveal additional options to export individual log lines as json, to define a **metric **and** create a report**.&#x20;

![](../../.gitbook/assets/flash-high-level-options\(1\).png)

### Context Logs

When you’ve narrowed down your results to a single log line and now you want to see the logs around it. You can do that by clicking the context logs option. This brings up the logs modal and you can view the logs from the selected application and process. The log line of interest will be highlighted so that you can look around it.

![](../../.gitbook/assets/flash-high-level-context-logs.png)
