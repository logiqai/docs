# Migrating To A New Cluster

In contrast to [rebuilding individual nodes](rebuilding-irondb-nodes.md) or [resizing a cluster](resizing-clusters.md), operational needs may call for migrating a cluster to a new set of machines entirely. This may be due to hardware lifecycle requirements and/or the desire to modify the topology all at once.

As with individual node reconstitution, this is a "pull"-type operation, where the new cluster's nodes pull the necessary metric data from the source cluster. The following procedure will be run on each of the new cluster's nodes. Multiple new-cluster nodes can reconstitute simultaneously if the source cluster has sufficient read capacity, but exercise care, since every reconstituting node will read from every source cluster node.

## Prerequisites

Reconstitution requires that at least one replica of every metric stream stored on the existing cluster be available. A reconstitute operation cannot complete if more than `W-1` nodes of the existing cluster are unavailable (`W` is the number of `write_copies` configured for the existing cluster's topology.)

For example, given a cluster of 10 nodes (`N=10`) with 3 write copies (`W=3`), a new cluster may be reconstituted if at least `10-(3-1)`, or 8, of its nodes are available and healthy.

As this can be a long-running procedure, a terminal multiplexer such as `tmux` or `screen` is recommended to avoid interruption.

## Procedure

On each of the new cluster nodes, after [installing](../getting-started/installation.md) and [configuring the new topology](../getting-started/installation.md#cluster-configuration), perform the following steps to reconstitute each of the new nodes from the source cluster.

1. [Disable the service](operations.md#service-management)
2. Make sure there is no lock file located at `/irondb/logs/snowth.lock`. If there is, remove it with the following command:

```
rm -f /irondb/logs/snowth.lock
```

1. Note the topology hash from the source cluster. This is the value of the `active` attribute in `/opt/circonus/etc/topology.conf` on one of the source cluster's nodes. The hash will be referred to below as `<source_cluster_topo_hash>`.
2. Run IRONdb in reconstitute mode using the following command:

```
/opt/circonus/bin/irondb-start -B -E \
  -T <source_cluster_topo_hash> \
  -O <source_cluster_node_ip>:<port>
```

where the argument to `-O` is the IP address and port of a node in the source cluster. The port is the cluster API port, typically 8112. The reconstitute will get the topology information from the source cluster node using the specified topology. Actual metric data fetches will be done against all source cluster nodes, using the topology information to determine the primary owner of each metric stream.

1. Wait until the reconstitute operation has fetched 100% of its data from the source cluster. You can access the current percentage done at:

```
http://<node ip address>:<node port>/
```

In reconstitute mode, the normal UI is replaced with a special one giving reconstitute status. Note that there may not be messages appearing on the console while this runs. This is normal; do not stop the reconstitute. Current progress will be saved - if the process stops for any reason, everything should pick back up approximately where it was. If the download stops partway for any reason, you may resume it with the following command:

```
/opt/circonus/bin/irondb-start -B \
  -T <source_cluster_topo_hash> \
  -O <source_cluster_node_ip>:<port>
```

1. Once the reconstituting node has retrieved all of its data, you will see the following on the console:

```
Reconstitute Finished!
```

1. [Start the service](operations.md#service-management).
