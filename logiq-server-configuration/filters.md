# Filters

Incoming data streams can be filtered before they are written to the final store in the S3 / S3 compatible bucket. Filter expressions allow fine-grained matching on key attributes from the ingested data.

Filters are defined using the _**"filters"**_ keyword in the Apica Ascent configuration file. A filter definition consists of a name and a condition. E.g.

```text
filters:
  -
    name: f_debug
    condition: severity == 'debug'
  -
    name: f_macbook_ubuntu_vm
    condition: app_name == 'macbook_ubuntu_vm'
```

## name \[required\]

This name key is used to specify a unique name for the filter

```text
filters:
  -
    name: f_ubuntu_vm
    condition: app_name == 'ubuntu_vm'
```

Filter for a rule is specified by including the filter name in the rule definition.

```text
rules:
  -
    source: s_ubuntuvm
    filter: f_ubuntu_vm
    destination: t_default_destination
```

Once an incoming stream matches the source definition in the rule, the filter, if one is specified, is applied to determine a rule match.

## condition \[required\]

The condition key is used to specify a boolean expression that is used for computing a rule match. The boolean condition is specified on key fields that are extracted from the ingested data.

```text
filters:
  -
    name: f_ubuntu_vm
    condition: app_name == 'ubuntu_vm'
```

### Syslog data attributes for condition expressions

The attribute values are of type string unless otherwise specified

* severity, Severity
* facility, Facility
* priority, Priority
* app\_name, appname, Appname, AppName
* timestamp, Timestamp
* message, Message
* host\_name, hostname, Hostname, HostName
* boolean: tag.Exists, Tag.Exists
* string: tag.Value, Tag.Value \(RFC3164 only\)
* boolean: protocol.RFC5424, Protocol.RFC5424, Protocol.RFC3164, protocol.RFC3164
* MsgId, Msgid, msg\_id \(RFC5424 only \)

### Condition expression syntax

* Modifiers: `+` `-` `/` `*` `&` `|` `^` `**` `%` `>>` `<<`
* Comparators: `>` `>=` `<` `<=` `==` `!=` `=~` `!~`
* Logical ops: `||` `&&`
* Numeric constants, as 64-bit floating point \(`12345.678`\)
* String constants \(single quotes: `'foobar'`\)
* Date constants \(single quotes, using any permutation of RFC3339, ISO8601, ruby date, or unix date; date parsing is automatically tried with any string constant\)
* Boolean constants: `true` `false`
* Parenthesis to control order of evaluation `(` `)`
* Arrays \(anything separated by `,` within parenthesis: `(1, 2, 'foo')`\)
* Prefixes: `!` `-` `~`
* Regex comparators `=~` `!~`



