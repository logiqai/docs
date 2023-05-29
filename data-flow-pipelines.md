---
description: >-
  The pipeline is a series of processes or stages through which data flow
  systematically and efficiently. It helps to visualize the flow between nodes,
  rules, and filters applied for the data flow.
---

# Data Flow Pipelines

## Create Pipeline View

Navigate to explore view, and click on the New Pipeline button to create a new pipeline view

<figure><img src=".gitbook/assets/Screenshot from 2023-05-27 15-48-39.png" alt="" width="254"><figcaption></figcaption></figure>

On click of the new pipeline button, a new dialog opens, select the desired date-time range, select the desired namespace, and click Create to create a new pipeline view.

<figure><img src=".gitbook/assets/Screenshot from 2023-05-27 15-46-20.png" alt=""><figcaption></figcaption></figure>

On click of create button a new pipeline tab will get added with the pipeline view as shown bellow

<figure><img src=".gitbook/assets/Screenshot from 2023-05-27 16-37-17.png" alt=""><figcaption></figcaption></figure>

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
&#x20;1\. Change the theme\
&#x20;2\. Change the default title of the pipeline tab\
&#x20;3\. Select a different date time range\
&#x20;4\. Select a different namespace, can do multi-select\
&#x20;5\. Shows the overall EPS and Valume savings.

### Add/Choose the existing rule(FILTER, EXTRACT, SIEM, TAG, REWRITE), for namespace and application.

Click the + icon to create or choose the existing rule&#x20;

<figure><img src=".gitbook/assets/Screenshot from 2023-05-27 22-24-40.png" alt="" width="54"><figcaption><p>Add/Choose existing rule</p></figcaption></figure>

On click of add rule button, add rule dialog will show, with the options \
1\. Choose Existing Rule\
2\. Create New Rule

<figure><img src=".gitbook/assets/Screenshot from 2023-05-27 22-27-04.png" alt=""><figcaption></figcaption></figure>

Select the existing rule to choose an existing rule for the namespace application

Select create rule button to create new rules for the namespace and application

<figure><img src=".gitbook/assets/Screenshot from 2023-05-27 22-33-34.png" alt=""><figcaption><p>Choose Existing Rule</p></figcaption></figure>

<figure><img src=".gitbook/assets/Screenshot from 2023-05-27 22-33-54.png" alt=""><figcaption><p>Create New Rule</p></figcaption></figure>

The selected/created rule will be displayed under the respective group nodes

<figure><img src=".gitbook/assets/Screenshot from 2023-05-27 22-50-15.png" alt=""><figcaption><p>Pipeline view with rule groups in the oder which rules will be applied</p></figcaption></figure>

### Add Rule(Forwarder)

Before adding the forwarder rule.  create a forwarder and map the forwarder in the data flow tab.

<figure><img src=".gitbook/assets/Screenshot from 2023-05-29 07-06-26.png" alt=""><figcaption><p>Map a forwarder</p></figcaption></figure>

After adding the forwarder the new node will be added as bellow

<figure><img src=".gitbook/assets/Screenshot from 2023-05-29 07-12-25.png" alt=""><figcaption><p>Pipeline with the forwaarder</p></figcaption></figure>

Click on the + icon to choose an existing or create a new forwarder rule for the application and target.\
After adding the forwarder rule, a new node will be shown between the application and the forwarder.

<figure><img src=".gitbook/assets/Screenshot from 2023-05-29 07-28-03.png" alt=""><figcaption><p>With the forwarder rule</p></figcaption></figure>

### Rule group node

<figure><img src=".gitbook/assets/Screenshot from 2023-05-29 07-30-50.png" alt=""><figcaption><p>Rule Group</p></figcaption></figure>

Each rule type will have separate rule groups(FILTER, EXTRACT, SIEM, TAG, REWRITE, FORWARDER).\
Each rule node will have the following details.\
1\. Rule active status within the time range\
2\. Info icon, on click will show the rule details\
3\. Name of the rule\
4\. Savings done by the rule if any

### Rule details

To view rule details, click on the info icon which is present at the top right corner, new popup shows with rule details on click of the icon.

<figure><img src=".gitbook/assets/Screenshot from 2023-05-29 09-10-14.png" alt=""><figcaption><p>Rule details</p></figcaption></figure>

Activate/Deactivate: On checking/unchecking the Active check box, the rule will get activated/deactivated.&#x20;
