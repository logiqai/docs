# Rules

Every LOGIQ configuration file must have at least one rule. A rule specifies how the incoming data streams are separated and organized into buckets and objects.

Rules are defined with the _**"rules"**_ keyword in the config file. All rule definitions must have a "_**destination"**_ keyword referring to a destination by name. Optionally, a rule may specify a _"**source"**_ keyword referring to a source by name and a _**"filter"**_ keyword referring to a filter by name. The _config file validator_ will flag an error for destination, source, filter names that are not found but referenced in a rule definition

```text
rules:
  -
    source: s_webservers
    filter: f_debug
    destination: t_webservers_debug
```

A minimal rule is defined with just a destination keyword and nothing else. This matches any client sending data and all data packets that are received.

```text
rules:
-
   destination: t_default_bucket
```

## destination \[required\]

The _**"destination"**_  keyword specifies the name of a destination where data will be stored. Please refer to the [destinations](destinations.md) section for more details on how to define a valid destination.

## source \[optional\]

The "_**source"**_ keyword specifies the name of a source definition to match a sender of the data. This is an optional field. If the source keyword is not specified, all clients that send data to the server are allowed to match against the rule. Please refer to the [sources](sources.md) section for more details on how to define a valid source.

## filter \[optional\]

The "_**filter"**_ keyword specifies the name of a filter definition that is used to specify a filtering rule. The destination is selected if the incoming data stream matches the filter. The filter is applied after the source match is made.

If a filter is not specified, the destination is selected based on the source match or if no source if specified for the destination. Please refer to the [filters](filters.md) section for more details on how to define a valid filter.

