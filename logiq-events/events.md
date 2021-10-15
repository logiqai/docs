---
description: >-
  LOGIQ supports automatic detection of relevant events in your log stream.
  Events use a combination of built-in and user defined rules to give immediate
  insight into critical changes
---

# Events

### Events UI

Events are shown in the user interface in the Events tab.

![](<../.gitbook/assets/Screen Shot 2020-08-09 at 7.56.01 PM.png>)

It is easy to narrow down and search for events that you care about using search and filtering

![](<../.gitbook/assets/Screen Shot 2020-08-09 at 7.56.40 PM.png>)

### Event rules

Events are captured based on _**event rules**_. Many event rules are built into LOGIQ. For customizing this further, we provide a simple UI to add new rules into the system.

See section on [Event Rules ](event-rules.md)for further information.

### Event De-duplication

Events generated within a namespace are deduplicated by the LOGIQ platform. This reduces the amount of data stored at rest over time. At peak data rates, it is possible to get a 1000x reduction in the amount of events generated.
