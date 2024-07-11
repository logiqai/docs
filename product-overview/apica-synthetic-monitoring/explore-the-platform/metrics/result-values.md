# Result Values

## Result Values  <a href="#result-values" id="result-values"></a>

In Synthetic Monitoring, various processes and formulas are used to calculate result values.

## Result Severity <a href="#result-severity" id="result-severity"></a>

Check results can be assigned different severities, depending on the resulting value.

| <h3 id="term">Term</h3>                     | <h3 id="definition-comments"><strong>Definition/Comments</strong></h3>                                                                                                                                                                                                                                                                                                                                                                           |
| ------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| <h4 id="result">Result</h4>                 | When a check runs, it returns a **result**—for example, a response time value.                                                                                                                                                                                                                                                                                                                                                                   |
| <h4 id="severity">Severity</h4>             | <p>Depending on the check type, the result value will result in a <strong>severity</strong> level for the check, displayed in the various views in Synthetic Monitoring.</p><p><strong>Severity</strong> is a level indicator used to indicate the status of a check based on the results. The severity is used in various displays and alerts, notifications, and events.</p>                                                                   |
| <h4 id="check-status">Check Status</h4>     | <p>Four colors represent the current check status</p><ul><li><strong>Green: Information</strong></li><li><strong>Yellow: Warning</strong></li><li><strong>Orange: Error</strong></li><li><strong>Red: Fatal</strong></li></ul><p>The colors are used in any context where the check status is displayed.</p>                                                                                                                                     |
| <h4 id="configuration">Configuration</h4>   | <p>The configuration of the check affects how the value is converted into a severity.</p><p>The result interpretation settings apply some modifications to the result. For example, You can ignore particular combinations of file types and HTTP response codes.</p><p>A failed check will, by default, get the severity <strong>Fatal</strong>.</p><p>This can be configured to a different severity with the Check Fail Severity setting.</p> |
| <h4 id="preserve-value">Preserve Value</h4> | <p>With the Preserve Value setting enabled, the returned value will be used and included in aggregated/calculated values.</p><p><strong>Note:</strong> When a check has failed, the return value is considered <code>Null</code>, and there is no value to store.</p>                                                                                                                                                                            |
| <h4 id="thresholds">Thresholds</h4>         | <p>The various Threshold settings are used to select a severity for the check result.</p><p>The thresholds define an upper (High) and lower (Low) bound on the result for Warning and Error. Values above and below these bounds will cause the corresponding severity.</p><p><strong>Note:</strong> Preserve that value must enable the thresholds to have any effect since it uses the result value.</p>                                       |
| <h4 id="mapping">Mapping</h4>               | In addition to the thresholds, you can also configure Severity Mapping to customize rules to assign severities to different error types.                                                                                                                                                                                                                                                                                                         |

## Result Value SLA <a href="#result-value-sla" id="result-value-sla"></a>

In Synthetic Monitoring, SLA is calculated according to a formula, based on the duration of the result types.

### Calculation <a href="#calculation" id="calculation"></a>

SLA calculations are affected negatively by the number of Fatal and Error results in a check.

The formula is:

(`info` + `warning`) / `total`

| **Item**  | **Description**                                                                                |
| --------- | ---------------------------------------------------------------------------------------------- |
| `Info`    | The duration that the check has the severity Information.                                      |
| `Warning` | The duration that the check has the severity Warning.                                          |
| `Total`   | The sum of the duration of all the severities including Information, Warning, Error and Fatal. |

#### Example: <a href="#example" id="example"></a>

Let´s say that for the period of 11:00 – 12:00 our check has the following severities:

<figure><img src="../../../.gitbook/assets/image (25).png" alt=""><figcaption></figcaption></figure>

11:00-11:10 `Error`, duration = 10 min

11:10-11:20 `Fatal`, duration = 10 min

11:20-11:40 `Warning`, duration = 20 min

11:40-11:50 `Error`, duration = 10 min

11:50-12:00 `Information`, duration = 10 min

The SLA calculation for this example would look like this:

(10 min `Information` + 20 min `Warning`) / 60 min `Total` = 0.5 = 50% SLA

&#x20;

## Data Retention <a href="#data-retention" id="data-retention"></a>

Your monitoring results are stored on Apica servers for a limited time. The storage time varies with the type of data.

### 1. Checks  <a href="#id-1.-checks" id="id-1.-checks"></a>

#### 1A. All Checks  <a href="#id-1a.-all-checks" id="id-1a.-all-checks"></a>

* Check Result Graph: 65 days

#### 1B. Check Specific Data Retention  <a href="#id-1b.-check-specific-data-retention" id="id-1b.-check-specific-data-retention"></a>

**Firefox, Chrome, iPhone (Mobile Website), iPad (Mobile Website), Android (Mobile Website), Windows Phone (Mobile Website)**

* [Details Toolbar](https://apica-kb.atlassian.net/wiki/spaces/ASMDOCS/pages/2132901910/Result+Values): 14 Days
* [Elapsed Time](https://apica-kb.atlassian.net/wiki/spaces/ASMDOCS/pages/2132901910/Result+Values): 14 Days
* [Waterfall](https://apica-kb.atlassian.net/wiki/spaces/ASMDOCS/pages/2132901910/Result+Values): 14 Days
* [Expanded View](https://apica-kb.atlassian.net/wiki/spaces/ASMDOCS/pages/2132901910/Result+Values): 14 Days
* [Domains](https://apica-kb.atlassian.net/wiki/spaces/ASMDOCS/pages/2132901910/Result+Values):14 Days
* [Slowest URLs](https://apica-kb.atlassian.net/wiki/spaces/ASMDOCS/pages/2132901910/Result+Values): 14 Days
* [Details Result Scenario](https://apica-kb.atlassian.net/wiki/spaces/ASMDOCS/pages/2132901910/Result+Values): 14 days
* [Details Errors](https://apica-kb.atlassian.net/wiki/spaces/ASMDOCS/pages/2132901910/Result+Values): 14 Days
* [Details Result Screenshots](https://apica-kb.atlassian.net/wiki/spaces/ASMDOCS/pages/2132901910/Result+Values): 14 Days
* [Extracted Values](https://apica-kb.atlassian.net/wiki/spaces/ASMDOCS/pages/2132901910/Result+Values): 14 Days

**ZebraTester, Mobile browser, iPhone (Mobile App), iPad (Mobile App), Android (Mobile App), Windows Phone (Mobile App)**

* [Details Toolbar](https://apica-kb.atlassian.net/wiki/spaces/ASMDOCS/pages/2132901910/Result+Values): 7 Days
* [Elapsed Time](https://apica-kb.atlassian.net/wiki/spaces/ASMDOCS/pages/2132901910/Result+Values): 7 Days
* [Waterfall](https://apica-kb.atlassian.net/wiki/spaces/ASMDOCS/pages/2132901910/Result+Values): 2 Days
* [Expanded View](https://apica-kb.atlassian.net/wiki/spaces/ASMDOCS/pages/2132901910/Result+Values): 2 Days
* [Domains](https://apica-kb.atlassian.net/wiki/spaces/ASMDOCS/pages/2132901910/Result+Values):14 Days
* [Slowest URLs](https://apica-kb.atlassian.net/wiki/spaces/ASMDOCS/pages/2132901910/Result+Values): 2 Days
* [Details Errors](https://apica-kb.atlassian.net/wiki/spaces/ASMDOCS/pages/2132901910/Result+Values): 7 Days

**Internet Explorer**&#x20;

* [Details Toolbar](https://apica-kb.atlassian.net/wiki/spaces/ASMDOCS/pages/2132901910/Result+Values): 14 Days
* [Elapsed Time](https://apica-kb.atlassian.net/wiki/spaces/ASMDOCS/pages/2132901910/Result+Values): 7 Days
* [Waterfall](https://apica-kb.atlassian.net/wiki/spaces/ASMDOCS/pages/2132901910/Result+Values): 2 Days
* [Expanded View](https://apica-kb.atlassian.net/wiki/spaces/ASMDOCS/pages/2132901910/Result+Values): 2 Days
* [Domains](https://apica-kb.atlassian.net/wiki/spaces/ASMDOCS/pages/2132901910/Result+Values):14 Days
* [Slowest URLs](https://apica-kb.atlassian.net/wiki/spaces/ASMDOCS/pages/2132901910/Result+Values): 2 Days
* [Details Errors](https://apica-kb.atlassian.net/wiki/spaces/ASMDOCS/pages/2132901910/Result+Values): 2 Days

**Command Check, Ping, Port, DNS, Appdynamics, Traceroute, FTP, New Relic, SSL:**

* [All](https://apica-kb.atlassian.net/wiki/spaces/ASMDOCS/pages/2132901910/Result+Values): 14 Days

#### Analyze Metrics  <a href="#analyze-metrics" id="analyze-metrics"></a>

**Response time and Return Value (Only for the 3rd dropdown):**

* [All Checks](https://apica-kb.atlassian.net/wiki/spaces/ASMDOCS/pages/2132901910/Result+Values) = 13 months

**Response time and Return Value for the 4th drop-down:**

* [Proxy Sniffer Scenario](https://apica-kb.atlassian.net/wiki/spaces/ASMDOCS/pages/2132901910/Result+Values): 7 days
* [Browser Scenario, check-level](https://apica-kb.atlassian.net/wiki/spaces/ASMDOCS/pages/2132901910/Result+Values): 14 days

**All Other Metrics**

* [Proxy Sniffer Scenario](https://apica-kb.atlassian.net/wiki/spaces/ASMDOCS/pages/2132901910/Result+Values): 7 days
* [Firefox & Chrome](https://apica-kb.atlassian.net/wiki/spaces/ASMDOCS/pages/2132901910/Result+Values): 14 days
* [Browser Scenario, check-level](https://apica-kb.atlassian.net/wiki/spaces/ASMDOCS/pages/2132901910/Result+Values): 14 days
* [Browser Scenario, step-level](https://apica-kb.atlassian.net/wiki/spaces/ASMDOCS/pages/2132901910/Result+Values): 10 days
* [Internet Explorer](https://apica-kb.atlassian.net/wiki/spaces/ASMDOCS/pages/2132901910/Result+Values): 14 days
* [URL](https://apica-kb.atlassian.net/wiki/spaces/ASMDOCS/pages/2132901910/Result+Values): 7 days

**Analyze Trends**&#x20;

* [Hourly](https://apica-kb.atlassian.net/wiki/spaces/ASMDOCS/pages/2132901910/Result+Values) = 13 months
* [Daily](https://apica-kb.atlassian.net/wiki/spaces/ASMDOCS/pages/2132901910/Result+Values) = Unlimited
