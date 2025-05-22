# SIEM and TAG

SIEM and TAG rules are Log2Metric rules that can be used to tag data for any interesting events. Apica Ascent Log2Metrics is a powerful feature that helps you convert your log data into a real-time metric. Using Log2Metrics, you can visualize your log data, plot distributions, create a custom index, and create alerts for events.

This is useful for identifying the interesting events that may occur in logs in real-time. For example track, user login failures, track load balancer or ingress status codes, etc... See the section about [Log2Metrics](../../log-management/metrics-and-custom-indices.md) for additional information.

Apica Ascent has hundreds of inbuilt SIEM rules which can be accessed on the "Explore -> Pipeline -> Rules" tab .

<figure><img src="../../.gitbook/assets/Screenshot from 2025-05-22 13-42-30.png" alt=""><figcaption><p>Rules List</p></figcaption></figure>

### Creating an SIEM and TAG Rule in Apica Ascent

#### 1. Navigate to the Configure Pipeline

* Go to the pipeline where you want to apply the rule.
* Click on `Configure Pipeline` from the pipeline’s action menu.

<figure><img src="../../.gitbook/assets/Screenshot from 2025-05-21 17-48-48.png" alt=""><figcaption><p>Pipelines List</p></figcaption></figure>

#### 2. Add a New SIEM/TAG Rule

* Hover over the `+ Add Rule` button.
* Select `SIEM/TAG` from the rule type dropdown.
* A modal will open with a form organized into tabs.

<figure><img src="../../.gitbook/assets/Screenshot from 2025-05-21 17-57-39.png" alt=""><figcaption><p>Create Rule</p></figcaption></figure>

#### 3. Fill in Rule Details

In the **Details** tab:

* Specify the **rule name**, **description**, and other required fields.
* Click `+ Add More Parameters` to define matching conditions.&#x20;

Example:



![A sample Log2Metrics dashboard that tracks Security Incidents and status codes](<../../.gitbook/assets/image (39) (1) (1).png>)
