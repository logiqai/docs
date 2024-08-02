# ALIVE Log Compare

## ALIVE Log Compare Introduction

Log events are massive and difficult to comprehend due to their machine/human-like information nature. Yet they contain helpful information that needs to be harvested to get the process going. This process includes maintaining smooth operation flow, debugging complex modern distributed systems, security overlooks, tracking changes, etc. It is highly desirable to discern anomalies out of the log events.

One simple heuristic technique for discerning anomalies is to compare the subject with a known golden sample, which yields outliers. Nevertheless, comparing event logs is not a trivial task. &#x20;

The ALIVE Log Compare utilizes Apica Ascent's log analysis underlying feature pattern-signature and compares log pattern signatures across different time ranges. This feature is powerful and handy for separating needles from haystacks. &#x20;

Some of the key features

* Simple to use
* Large working set and capable of looking over a large volume of log events
* Isolate subtle and apparent differences
* Tracking log event changes

### Key Usage Direction

Timestamp Selection: Users initiate the pattern compare feature by selecting specific timestamps of interest within the ALIVE interface.

Compare Log Display: Users can activate the "Compare Log" feature upon selecting timestamps and completing the uploading of all the event logs. This feature visually juxtaposes log patterns from different periods, facilitating quick identification of variations or anomalies.

### Example Usage Direction

#### To compare patterns in the ALIVE tab, follow these steps:

1. Navigate to the ALIVE tab from the Search page.

<figure><img src="../../.gitbook/assets/Screenshot from 2024-07-02 00-08-10.png" alt=""><figcaption><p>COMPARE Tab</p></figcaption></figure>

2. Select the COMPARE tab from the left side pane. You will see two charts, both of which are set to the global time range by default.
3. To compare the charts, adjust the time range for chart B using the date-time picker. Select the desired time range to observe and analyze the patterns side by side.

<figure><img src="../../.gitbook/assets/Screenshot from 2024-07-02 00-10-11.png" alt=""><figcaption><p>Selecting Timerange for Comparing pattern.</p></figcaption></figure>

4. Once you select the time range and click on the apply button, it will load and display the pattern. Wait for it to load successfully.

<figure><img src="../../.gitbook/assets/Screenshot from 2024-07-02 00-10-22.png" alt=""><figcaption><p>Clicking on the Apply button to update the pattern.</p></figcaption></figure>

5. After the pattern is loaded, you can compare the pattern.

<figure><img src="../../.gitbook/assets/Screenshot from 2024-07-02 00-16-00.png" alt=""><figcaption><p>Comparing pattern side by side on different timerange.</p></figcaption></figure>

5. Once the pattern is loaded, you can compare the logs corresponding to the selected time range. Navigate to the left side pane and select the LOG COMPARE tab to analyze the logs associated with the generated pattern.

<figure><img src="../../.gitbook/assets/Screenshot from 2024-07-02 00-17-20.png" alt=""><figcaption><p>Comparing logs side by side.</p></figcaption></figure>

### Key Benefits

* **Efficiency**: Reduces the time required to manually sift through logs by visually presenting pattern changes.
* **Accuracy**: Enhances the detection of anomalies or unusual patterns that may indicate security breaches, performance issues, or operational changes.
