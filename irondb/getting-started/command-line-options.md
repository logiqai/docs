# Command Line Options

Reference to available options and arguments.

* [Synopsis](command-line-options.md#process-control-options)
* [Process Control](https://docs.circonus.com/irondb/getting-started/command-line-options#process-control-options)
* [Operating Modes](command-line-options.md#operating-mode-options)
* [Loader Options](command-line-options.md#loader-options)
* [Maintenance Actions](command-line-options.md#maintenance-options)
* [Behavioral Options](command-line-options.md#behavioral-options)
* [Reconstitute Options](command-line-options.md#reconstitute-options)

To obtain the most current usage summary: `/opt/circonus/sbin/snowthd -h`

## Synopsis

```
process control flags:
        -k start                start the process (default)
        -k stop                 stop a running process
        -k status               report the status via exit code

mutually exclusive flags:
        -e                      boot this node ephemerally (compute node)
        -i <uuid>               identify this node

standalone loader flags for use with -i
        -m                      merge text reconstitution files (deprecated)
        -H                      merge hist reconstitution files (deprecated)

standalone maintenance flags for use with -i
        -r text/metrics         repair text inventory
        -r text/changelog       repair text datastore
        -r hist/metrics         repair hist inventory
        -r hist/<period>        repair hist rollup for configured <period>
        -j                      only write journal data to other nodes

optional behavior flags:
        -c <file>               load config from <file> (full path)
                                        default: /opt/circonus/etc/snowth.conf
        -d                      debugging
        -D                      foreground operations (don't daemonize)
        -u <user>               run as <user>
        -g <group>              run as <group>
        -t <path>               chroot to <path>
        -l <logname>            enable <logname>
        -L <logname>            disable <logname>
        -q                      disable gossip on this node

reconstitute parameters:
        -B                      Reconstitute mode
        -T <topo_hash>          Reconstitute new cluster from remote topology
        -O <ip>[:<port>]        Reconstitute from remote host
        -A <type>               Reconstitute type
                                Acceptable values: nntbs,text,hist,raw,surrogate
                                May be specified multiple times
                                All if omitted
        -S <node_uuid>          Skip/ignore this node during reconstitute
                                May be specified multiple times

this usage message:
        -h                      usage
```

## Process Control Options

* `-k <start|stop|status>`

`status` will exit `0` if the process is running, non-zero otherwise.

## Operating Mode Options

These options are mutually exclusive of one another. One or the other is required.

* `-i <uuid>`

Identify this node with `<uuid>`. This is the normal mode of operation.

* `-e`

Boot the node in ephemeral mode. Ephemeral nodes are read-only participants in the cluster. They do not appear in the cluster topology, and do not accept incoming metrics, but may be used to read metric data from other nodes and perform intensive computation that would add unreasonable load to the main nodes.

## Loader Options

These options imply foreground operation and perform a specific task, then exit. They are only valid in identified mode (`-i`).

* `-m`

Merge text reconstitution files. **DEPRECATED**

* `-H`

Merge histogram reconstitution files. **DEPRECATED**

The above 2 options were used in a previous version of the reconstitute process and are no longer strictly required. They may be removed in a future version.

## Maintenance Options

These options imply foreground operation and perform a specific task, then exit. They are only valid in identified mode (`-i`).

* `-r text/metrics`

Repair text inventory.

* `-r text/changelog`

Repair text datastore.

* `-r hist/metrics`

Repair histogram inventory.

* `-r hist/<rollup>`

Repair a histogram rollup. The value is one of the existing histogram rollup periods from the config file, e.g., `hist/60` to repair the 1-minute histogram rollups.

* `-j`

Journal-drain mode. Does not start a network listener, so this node will appear "down" to its peers, but will send any pending journal data to them. This is useful if you are planning to retire and replace a cluster node, and want to ensure that it has sent all outgoing journal data without accepting any new input.

## Behavioral Options

These determine optional behavior, and are not required.

* `-c <file>`

Load configuration from `<file>`. Must be a full path. If not specified, the default path is `/opt/circonus/etc/snowth.conf`.

* `-d`

Activate additional debug logging. Use with caution; can generate a large volume of logs.

* `-D`

Stay in the foreground, rather than daemonizing. If specified once, run as a single process with no watchdog. If specified twice, run as a parent/child pair, with the parent (watchdog) process in the foreground.

See the [libmtev documentation](http://circonus-labs.github.io/libmtev/development/mtev_main.html#foreground) for details on foreground operation.

* `-u <user>`

Drop privileges after start and run as this user.

* `-g <group>`

Drop privileges after start and run as this group.

* `-t <path>`

Chroot to `<path>` for operation. Ensure that log file locations may be accessed within the chrooted environment.

* `-l <logname>`

Enable `<logname>`, even if it is disabled in the configuration file. The specified log stream must exist.

* `-L <logname>`

Disable `<logname>`, even if it is enabled in the configuration file. The specified log stream must exist.

## Reconstitute Options

These operations are used when [rebuilding a node](../administration/rebuilding-irondb-nodes.md).

* `-B`

Enable reconstitute mode.

* `-T <topo_hash>`

Reconstitute from this remote/foreign topology. Used when creating a new cluster from an existing one.

* `-O <ip>[:<port>]`

Bootstrap remote reconstitute from this node in the source cluster. Used when creating a new cluster from an existing one. The reconstituting node will fetch information about the source cluster's topology from this node, but actual metric data will be fetched from all source cluster nodes.

* `-A <type>`

Reconstitute one type of data, or all if the option is omitted. May be specified multiple times to reconstitute multiple data types.

* `-S <node_uuid>`

Skip the specified node(s) when pulling data for reconstitute. This is useful if a node is unavailable at the time a reconstitute is started. May be specified multiple times to skip more than one node. **Use with caution. If the number of skipped nodes exceeds the number of data copies, the reconstitute may be incomplete.**
