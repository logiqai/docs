---
description: >-
  New rule type is introduced with the latest release, where user can add the
  JavaScript code to enhance the logs.
---

# CODE RULE:

With the help of Code Block, add Code Rule to improve your pipelines. Code Rules takes in a JavaScript function that gets integrated with your pipeline.&#x20;

&#x20;With Code Rules add:&#x20;

* Data Parsing Rules: These rules define how log data should be parsed to extract \
  relevant information. This includes defining regular expressions or specific patterns to identify log fields such as timestamp, log level, and message    &#x20;
* Data Validation Rules: Validation rules ensure that ingested log data meets certain \
  criteria or standards. For example, validating timestamps to ensure they are in the \
  correct format, checking for required fields, or filtering out invalid log entries.&#x20;
* &#x20;Data Transformation Rules: Sometimes log data must be transformed into a \
  centralised system before ingestion. This could involve converting timestamps to a \
  standardised format, anonymizing sensitive information, or enriching log entries with additional contextual data.&#x20;

Code Blocks is enriched with JavaScript code completion and syntax highlighting. Easily add or update your JS code by typing or importing a code file.&#x20;

<figure><img src="../.gitbook/assets/Screenshot from 2024-06-19 00-05-33.png" alt=""><figcaption><p>CODE RULE</p></figcaption></figure>

The Code Rule empowers users to create and execute custom scripts or rules for processing incoming logs. This flexibility allows for highly tailored log processing logic to be implemented, beyond what can be achieved with predefined rewrite or extraction rules. Users can leverage their programming skills to manipulate log data in sophisticated ways, enabling tasks such as complex data transformations, enrichment, filtering, or integration with external systems. This Rule offers advanced customization options for handling diverse log processing requirements.



Added the code block support for the following two code rules.&#x20;

* REWRITE RULE&#x20;
* EXTRACT RULE&#x20;

**REWRITE RULE:**

The Rewrite Rule is responsible for modifying log events by applying rules defined through regular expressions. These rules are used to mask or replace sensitive information within the logs, ensuring data privacy and security.&#x20;

For example, it can replace credit card numbers, social security numbers, or any other sensitive data with placeholder values, thus anonymizing the logs while retaining their informational value.

Rewrite Code rule has an optional code field. Clicking on the toggle Code field, you can add or remove your code from your rule. Clicking on the import button you can import the code file whose contents are immediately hydrated in the Code Block.

<figure><img src="../.gitbook/assets/Screenshot from 2024-06-19 00-08-18.png" alt=""><figcaption><p>REWRITE RULE</p></figcaption></figure>



**EXTRACT RULE:**

The Extract Rule parses and extracts specific labels or fields from unstructured log events using regular expressions. This process helps to convert raw log data into a more structured format by identifying and extracting key pieces of information.

&#x20;For instance, it can extract timestamps, IP addresses, user agents, or any other relevant data points from log entries, facilitating easier analysis and categorisation of the logs.&#x20;

Like REWRITE RULE, you can add an optional code field to your rule by clicking the toggle code button.

<figure><img src="../.gitbook/assets/Screenshot from 2024-06-19 00-08-31.png" alt=""><figcaption><p>EXTRACT RULE</p></figcaption></figure>

**View CODE:**

In the Rules section, an option is available for viewing your code. You can filter rules according to your preference and examine their configuration by selecting the dropdown ('+' icon). To view the code for a specific code rule, locate the NodeJS icon within the dropdown description. Clicking on it will open a modal that displays the code in a read-only code block.&#x20;

Please be informed that the code block is set to read-only mode. To modify the code, please proceed with the standard edit-rule procedure.&#x20;

<figure><img src="../.gitbook/assets/Screenshot from 2024-06-19 00-15-48.png" alt=""><figcaption><p>View CODE</p></figcaption></figure>



**JS CODE FORWARDER:**

This forwarder, equipped with JavaScript execution capabilities, revolutionizes log shipping by allowing users to dynamically process transported logs in real-time with custom JavaScript functions. &#x20;

For example, users can define JavaScript functions to scan incoming logs, identify specific patterns or anomalies, and automatically trigger actions, like filing tickets in response to detected issues. This seamless integration of JavaScript-based log processing directly within the forwarder streamlines the log management workflow, enabling organizations to swiftly and efficiently respond to critical events or conditions detected within their log data, thereby enhancing operational efficiency and proactive incident management.&#x20;



<figure><img src="../.gitbook/assets/Screenshot from 2024-06-19 00-17-37.png" alt=""><figcaption><p>JS CODE FORWARDER</p></figcaption></figure>
