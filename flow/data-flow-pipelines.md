---
description: >-
  The pipeline is a series of processes or stages through which data flow
  systematically and efficiently. It helps to visualize the flow between nodes,
  rules, and filters applied for the data flow.
---

# Data Flow Pipelines

## Create Pipeline View

Navigate to explore view, and click on the New Pipeline button to create a new pipeline view

<figure><img src="../.gitbook/assets/Screenshot from 2024-07-12 11-56-52.png" alt=""><figcaption><p>Hover over the Actions button on the top-right</p></figcaption></figure>

On click of the New Pipeline button, a new dialog opens, select the desired date-time range, select the desired namespace along with the linked applications, and click Create to create a new pipeline view.

<figure><img src="../.gitbook/assets/Screenshot from 2024-07-11 14-13-24.png" alt=""><figcaption></figcaption></figure>

On click of the Create button a new pipeline tab will get added with the pipeline view as shown below

<figure><img src="../.gitbook/assets/Screenshot from 2024-07-12 12-27-18.png" alt=""><figcaption></figcaption></figure>

**Pipeline View**: The pipeline view shows the data flow between the nodes. each node is connected with the edges to show the data flow between the nodes. The node will have the following details.

\
1\. Name of the node\
2\. Total number of Events\
3\. Total volume size of the events\
4\. Total savings for application and target node\
**Minimap**: Minimap is a tool for quick preview and exploration of large graphs.\
**Time Range Slider**: Helps to select the time range between the selected date and time\
**Zoom In/Out:** Tool to zoom in and zoom out the graph\
**Side Bar**: Helps to make the following changes\
1\. Change the theme\
2\. Change the default title of the pipeline tab\
3\. Select a different date time range\
4\. Select a different namespace, can do multi-select\
5\. Shows the overall EPS and Valume savings.

### Add/Choose the existing rule(FILTER, EXTRACT, SIEM, TAG, REWRITE, Code), for namespace and application.

Click the + icon to create or choose the existing rule

<figure><img src="../.gitbook/assets/Screenshot from 2023-05-27 22-24-40.png" alt="" width="54"><figcaption><p>Add/Choose existing rule</p></figcaption></figure>

On click of + icon, Add Rule dialog will show, with the options\
1\. Choose Existing Rule\
2\. Create New Rule

<figure><img src="../.gitbook/assets/Screenshot from 2024-07-12 12-30-02.png" alt=""><figcaption></figcaption></figure>

Select the Choose Existing Rule to choose an existing rule for the namespace and application

Select Create New Rule button to create new rules for the namespace and application

<figure><img src="../.gitbook/assets/Screenshot from 2024-07-12 12-31-51.png" alt=""><figcaption><p>Choose Existing Rule</p></figcaption></figure>

<figure><img src="../.gitbook/assets/Screenshot from 2024-07-12 12-32-49.png" alt=""><figcaption><p>Create New Rule</p></figcaption></figure>

The selected/created rule will be displayed under the respective group nodes

<figure><img src="../.gitbook/assets/Screenshot from 2024-07-12 13-51-49.png" alt=""><figcaption><p>Pipeline view with rule groups in the oder which rules will be applied</p></figcaption></figure>

### Add Rule(Forwarder)

Before adding the forwarder rule, create a forwarder and map the forwarder in the data flow tab.

<figure><img src="../.gitbook/assets/Screenshot from 2024-07-12 14-02-16.png" alt=""><figcaption><p>Map a forwarder</p></figcaption></figure>

After adding the forwarder the new node will be added as below

<figure><img src="../.gitbook/assets/Screenshot from 2024-07-12 14-55-43.png" alt=""><figcaption><p>Pipeline with the forwarder</p></figcaption></figure>

Click on the + icon to choose an existing or create a new forwarder rule for the application and target.\
After adding the forwarder rule, a new node will be shown between the application and the forwarder.

<figure><img src="../.gitbook/assets/Screenshot from 2023-05-29 07-28-03.png" alt=""><figcaption><p>With the forwarder rule</p></figcaption></figure>

### Rule group node

<figure><img src="../.gitbook/assets/Screenshot from 2023-05-29 07-30-50.png" alt=""><figcaption><p>Rule Group</p></figcaption></figure>

Each rule type will have separate rule groups(FILTER, EXTRACT, SIEM, TAG, REWRITE, FORWARDER).\
Each rule node will have the following details.\
1\. Rule active status within the time range\
2\. Info icon, on click will show the rule details\
3\. Name of the rule\
4\. Savings done by the rule if any

### Rule details

To view rule details, click on the info icon which is present in the top right corner, new popup shows with rule details on click of the icon.

<figure><img src="../.gitbook/assets/Screenshot from 2024-07-12 15-01-29.png" alt=""><figcaption><p>Rule details</p></figcaption></figure>

Activate/Deactivate: On checking/unchecking the Active check box, the rule will get activated/deactivated.

There is no need to create an additional pipeline tab or manage your existing pipeline alongside other tabs in the explore section to view an application's pipeline. A new pipeline tab is added within the search section of an application with which the pipeline relevant to that particular application can be easily visualized.

<figure><img src="../.gitbook/assets/Screenshot from 2024-07-11 12-42-08.png" alt=""><figcaption></figcaption></figure>
