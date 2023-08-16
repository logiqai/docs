---
description: Log Pattern-Signature explained, usage, and configure.
---

# Log Pattern-Signature

## Log Pattern-Signature Explained

Machine log is known difficult to analyze due to its non-structured or semi-structured nature.  The non-conforming format plus its volume growth velocity make it challenging to extract values using conventional means such as search and monitoring.  Apica Ascent normalizes all incoming logs into Pattern-Signature (PS).  PS grouping or clustering all the ingested logs based on their underlying logging structure, in the structure-data term, Schema.&#x20;

The current logging method tries to unify the logs into a machine-like format such as homogeneous field assignments or key-value pair JSON format for simplifying the post analytics.  The practice, however, limits logging capability which is analogous to limiting all the observability log data to only one schema.  Moreover, a homogeneous machine log form is not intuitive and notoriously difficult to interpret.  The use of the advanced Pattern-Signature AI/ML method will make it fruitful.&#x20;

Apica Ascent Pattern-Signature autonomously derives the underlying schema for every log stream, see the example below,

```
PS_ID	Log Line
------------------------------------------------------------------------------------------------------------
18	2022-06-08T00:20:18.600784-07:00 #:1757:# Facet6=v18 Facet2=v20 Facet3=v-2 POSSIBLE BREAK-IN ATTEMPT
18	2022-06-08T00:20:18.621094-07:00 #:1759:# Facet6=v18 Facet2=v20 Facet3=v-2 POSSIBLE BREAK-IN ATTEMPT
27	2022-06-08T00:20:19.240826-07:00 #:1821:# Facet1=v19 Facet2=v20 Facet4=v-1 FacetU=b24f2b55-2ec4-4102-a70b-d48863ee7b7d in "quote here"  [ in bracket ] abcdeghijklmn19  ] ) }  POSSIBLE BREAK-IN ATTEMPT
18	2022-06-08T00:20:19.280237-07:00 #:1825:# Facet5=v19 Facet2=v20 Facet4=v-1 POSSIBLE BREAK-IN ATTEMPT
18	2022-06-08T00:20:20.090611-07:00 #:1859:# Facet6=v20 Facet2=v20 Facet3=v0 POSSIBLE BREAK-IN ATTEMPT
18	2022-06-08T00:20:20.251025-07:00 #:1875:# Facet1=v20 Facet2=v20 Facet4=v0 FacetU=b22fb734-1f08-45b3-ad90-facb807e5adb in "quote here"  [ in bracket ] abcdeghijklmn20  ] ) }  POSSIBLE BREAK-IN ATTEMPT
171	2022-06-08T00:20:20.360466-07:00 #:1886:# Facet5=v20 Facet2=v20 HERETWO [ NewPat20FW20 ] NewGen20LX20 ] ) } POSSIBLE BREAK-IN ATTEMPT
27	2022-06-08T00:20:20.580295-07:00 #:1908:# Facet1=v20 Facet2=v20 Facet4=v0 FacetU=abb9e25c-7335-48d5-9385-c7b278daf840 in "quote here"  [ in bracket ] abcdeghijklmn20  ] ) }  POSSIBLE BREAK-IN ATTEMPT
171	2022-06-08T00:20:20.681448-07:00 #:1918:# Facet5=v20 Facet2=v20 HERETWO [ NewPat20FW20 ] NewGen20LX20 ] ) } POSSIBLE BREAK-IN ATTEMPT
27	2022-06-08T00:20:20.850556-07:00 #:1935:# Facet1=v20 Facet2=v20 Facet4=v0 FacetU=1e79b620-6213-492f-8ac9-9a88bbac66e4 in "quote here"  [ in bracket ] abcdeghijklmn20  ] ) }  POSSIBLE BREAK-IN ATTEMPT
18	2022-06-08T00:20:21.481182-07:00 #:1949:# Facet6=v21 Facet2=v20 Facet3=v1 POSSIBLE BREAK-IN ATTEMPT
27	2022-06-08T00:20:21.490098-07:00 #:1950:# Facet1=v21 Facet2=v20 Facet4=v1 FacetU=005b2b1a-cf62-4a79-96b5-9d3d3639fff8 in "quote here"  [ in bracket ] abcdeghijklmn21  ] ) }  POSSIBLE BREAK-IN ATTEMPT
27	2022-06-08T00:20:21.520614-07:00 #:1953:# Facet1=v21 Facet2=v20 Facet4=v1 FacetU=49a539fa-5ec1-4e95-bf5a-231a8b233d7c in "quote here"  [ in bracket ] abcdeghijklmn21  ] ) }  POSSIBLE BREAK-IN ATTEMPT
18	2022-06-08T00:20:21.680362-07:00 #:1969:# Facet6=v21 Facet2=v20 Facet3=v1 POSSIBLE BREAK-IN ATTEMPT
27	2022-06-08T00:20:21.730095-07:00 #:1974:# Facet1=v21 Facet2=v20 Facet4=v1 FacetU=afb071b0-bc69-424b-91fb-0c78d941a202 in "quote here"  [ in bracket ] abcdeghijklmn21  ] ) }  POSSIBLE BREAK-IN ATTEMPT
171	:w2022-06-08T00:20:21.750926-07:00 #:1976:# Facet5=v21 Facet2=v20 HERETWO [ NewPat21FW20 ] NewGen21LX20 ] ) } POSSIBLE BREAK-IN ATTEMPT

```

Derived Pattern-Signatures (PS) or log data Schemas are shown below

```
Psid	Pattern-Signatures
-----------------------------------------------------------------------------------
171	* * * = * * = * HERETWO * * ] ) } POSSIBLE BREAK-IN ATTEMPT
27	* * * = * * = * * = * FacetU = * in * * * ] ) } POSSIBLE BREAK-IN ATTEMPT
18	* * * = * * = * * = * POSSIBLE BREAK-IN ATTEMPT
Notice that * are the variable or mutable fields that can potentially be extracted for reporting.  Everything else is fixed keyword or syntax.  

```

Symbol \* from the PS line is a variable or mutable field that can be extracted for reporting, monitoring, or anomaly tracking.  Everything else is a fixed token or constant that gives PS its attribute.

Pattern-Signature (PS) has many use cases.

### Log Reduction Based on Pattern Signature (PS)

The logs can be forwarded or dropped based on their structure form or Pattern-Signature Id.&#x20;

For example, debugging logs are useful for a specifically targeted instance/time.  The developers often do not always remove them when done troubleshooting the code.  Added logs to the already overloaded log ingestion pipeline.  SRE’s/DevOps, on the other hand, are never sure what logs are to be dropped and forwarded for storing and therefore took all in.  Apica Ascent PS generation will examine and analyze log pattern signatures holistically and therefore better and more accurately assess the log state for logging efficiency.

To get to the PS listing, one first goes to the log explorer page and set the namespace and application parameters for the log records to display.&#x20;

![](../.gitbook/assets/t1-2022-06-21\_14-36-24.jpg)

Example log display from namespace selection

![](../.gitbook/assets/t2-ex-s1-2022-06-21\_13-25-25.jpg)

After that, go to the right side and click on the log summary button (see below) to display the PSes. See the final log PS display below.

![](../.gitbook/assets/t3-ex-s3aa-2022-06-21\_13-37-36.jpg)

Annotation explanations

* 1\)-2) Display PS action will change the tab organization and now there are two levels of tabs
* 3\) 2nd row right-most tab shows the PS in sort count order
* 4\) 1st row right-most tab corresponding to this log query state.  Notice that this log query state is called Investigate Group (IG) and the query is fixed at namespace(s), application(s), and time period specification.&#x20;
* 5\) 2nd row left-most tab shows the queried logs.
* 6\) The main ingesting log window.  This is the place one specifies and initiates the log query.
* 7\) One can display all the logs of similar PS via the search icon, see outputs below.  _Notice that the new specific PS id search tab appears on the top row now._

![](../.gitbook/assets/t4-ex-s4-2022-06-21\_14-11-10.jpg)

## Log Outlier/Anomaly Isolation

Pattern signature grouping gives the user a way to quickly pick out anonymous logs based on infrequent PS logs. For the example below, one apparent failed SSL log is shown from thousands of 24-hour ingress logs.

![](../.gitbook/assets/t5-2022-06-18\_04-02-55.jpg)

## Log Trending Analysis

A deterministic quantity of logs signifies the system executes in steady stead.  The logging quantity of the frequent identical PS logs is evenly distributed over time.  Excessive or decreased logs hint that the logging subject experiences an anomaly.&#x20;

Click on the search icon to further drill down to one PS type.&#x20;

![](<../.gitbook/assets/t6-clipboard-image (3).png>)

## Log Comparison Analysis

Apica Ascent provides a robust platform for comparing logs from two different periods or different log partition spaces such as different namespaces or applications.  See the figure below where the PS comparison is made for the different time intervals of 12 hours.&#x20;

Investigation Group #1, IG1.  Notice that there are two tab groups; IG#1 and IG#2.  The tab group access method is shown below.&#x20;

![](../.gitbook/assets/ig1-ig2-2022-06-21\_14-26-57.jpg)

Investigation Group #2, IG2.

![](../.gitbook/assets/t8-t5-2022-06-18\_04-02-55.jpg)

## Configuring Pattern-Signature

Pattern-Signature feature is activated and controlled via the configuration steps below,

* 1\) Go to the menu item “Ingest Configuration” to display the PS configuration fillers.
* 2\) Four rows are used to manage PS features: “PS\_Configure”, “PS\_STREAM\_ENABLE”, “PS\_STEAM\_MAX\_SIZE”, “PS\_TOTAL\_STREAM\_MAX\_SIZE”.

![](../.gitbook/assets/ps-cfg-1-2022-06-21\_20-36-10.jpg)

### PS\_STREAM\_MAX\_SIZE

Maximum number of Pattern-Signatures (PS) that each namespace-application log stream can create. The ingestion turns off the Pattern-Signature engine and assigns default null PS id \*6 to that log stream. The default max count is set to 8,000.

### PS\_TOTAL\_STREAM\_MAX\_SIZE

A maximum number of total Pattern-Signatures (PS) the cluster can create. Once the total maximum count is reached, subsequent log event PS will be set to default PS id \*6. The default max count is set to 20,000.

### PS\_STREAM\_ENAB <a href="#ps_stream_enable" id="ps_stream_enable"></a>

**\[ ( \<ns> \<app>,)\*]**

\<ns> is the namespace string, a valid namespace specifier.

\<app> is the application name string, a valid application specifier.

### PS\_CONFIG

Reserved for internal uise.

### PS Id Default Code

* \*3 : Disable PS generation at the top level.
* \*4 : PS feature is turned off from log stream configuration or FlashOps level.
* \*6 : Exceed PS count at either total PS count or per log stream PS count max.
