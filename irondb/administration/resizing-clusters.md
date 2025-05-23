# Resizing Clusters

The essential steps to changing the topology of an existing IRONdb cluster are as follows:

* Create your new topology.
* Load the new topology to all nodes that will be part of the new cluster.
* Start the "rebalance" operation on each node, which begins the migration of metric data to the new topology. Depending on the amount of stored data, this process may take a long time.

Rebalancing involves recalculating the node ownership for each individual metric stream, and then sending that stream to the new owning node. All metric data remain available during a rebalance, under the old topology. New, incoming metric data is replicated to _both_ old and new topologies.

After all nodes complete the rebalance, they will switch their active topology from old to new.

A helper tool exists to simplify the procedure, and its use is illustrated below. Both additions and removals may be performed in the same operation, subject to the restrictions stated in the [Caveats](resizing-clusters.md#caveats) section below.

The helper tool utilizes the IRONdb [REST API](../api/) which, by default, listens on TCP port 8112. See the [Rebalancing APIs reference](../api/api-specs.md) for details. The helper tool is not necessary in order to perform a resize; the same operation may be performed using the APIs directly.

## Caveats

Rebalance cannot be used to transform a cluster with no sides into a sided cluster, or vice versa. Such a change requires [migrating to a new cluster](migrating-to-a-new-cluster.md).

When removing nodes from a cluster, no more than `W-1` (one less than the number of write copies) nodes may be removed in a rebalance operation. For example, a cluster with `W=3` may have a maximum of 2 nodes removed at a time. Removing more than this number of nodes could jeopardize data availability.

If resizing a sided cluster, the new cluster topology must still have at least `W/2` (half the number of write copies) nodes on each side, to ensure that the promise of metric distribution across sides can be maintained. For example, a sided cluster with `W=3` must still have at least 2 nodes on each side in the new topology (fractional values are rounded up to the nearest integer.)

During a rebalance operation, the existing cluster nodes all send their portions of the relocating metrics to the new node(s) simultaneously. Depending on the topology and the amount of existing metric data, this may be too much for the incoming node(s) to handle. If this is the case, the transfers maybe done sequentially by adding the following line to `irondb.conf`, just before the closing `</snowth>` line:

```
<rebalance concurrency="1"/>
```

This will make the overall operation take longer to complete, but should avoid overwhelming the incoming node(s).

This value will only take effect at the start of a rebalance operation, and will be ignored if changed while a rebalance is ongoing. To abandon a rebalance operation, see the last item of either [Adding Nodes](resizing-clusters.md#adding-nodes) or [Removing Nodes](resizing-clusters.md#removing-nodes) below.

## Adding Nodes

An existing IRONdb cluster has two nodes with write factor of 2. A new node is prepared by running the [installation](../getting-started/installation.md) which creates a standalone node with its own topology. We want to combine these three nodes together to create a three-node cluster, maintaining 2 write copies.

We will use the cluster resizing tool, `/opt/circonus/bin/resize_cluster`. Run this with the `-h` option for details on the available options.

* Choose one of the existing cluster nodes and note its IP address and API port. This will be the "bootstrap node" from which the resize tool will fetch the existing cluster's topology. If you do not specify the API port, the default (8112) will be assumed.
* Note the new node's IP address and node UUID, and, if the cluster is sided, whether the node will be added to side "a" or "b".
*   Run the resize tool, specifying the new node with a comma-separated tuple of IP address, node ID, and optionally a side. If adding more than one node, specify the `-a` option multiple times.

    `/opt/circonus/bin/resize_cluster -b <bootstrap_node_ip[:port]> -a <new_ip,new_uuid>`
* A summary of the new topology will be displayed, along with a listing of the existing cluster and the proposed changes. Unless you specified the `-y` (always answer "yes") option, you will be asked to confirm the changes before any actual work begins.
*   Once the changes are confirmed, IRONdb will start rebalancing the data. The new topology hash will be shown once it has been calculated.

    After all nodes complete the rebalance, they will switch their active topology from old to new. Each node will then kick off a delete operation of any metrics that no longer belong on that node.
*   To view progress, retrieve the [rebalance state](../api/api-specs.md) via GET of `/rebalance/state`:

    `curl http://<node>:<api-port>/rebalance/state`
*   To abort the rebalance, [stop the IRONdb service](operations.md#service-management) and remove the rebalance state file:

    `/irondb/localstate/.rebalance_state.json`

    on every node, including on any new nodes that were added. Then start the service again.

## Removing Nodes

Shrinking a cluster is basically the same as adding, above:

* Create a new topology with the nodes that should remain.
* Load the new topology to all nodes, including the ones that are leaving.
* Start rebalance to new topology on all nodes, including the ones that are leaving.

We will use the cluster resizing tool, `/opt/circonus/bin/resize_cluster`. Run this with the `-h` option for details on the available options.

* Choose a node that will be staying in the cluster and note its IP address and API port. This will be the "bootstrap node" from which the resize tool will fetch the existing cluster's topology. If you do not specify the API port, the default (8112) will be assumed.
* Note the node UUID of the node(s) that will be removed.
*   Run the resize tool, specifying the removed nodes by their node UUID. If removing more than one node, specify the `-r` option multiple times.

    `/opt/circonus/bin/resize_cluster -b <bootstrap_node_ip[:port]> -r <removed_uuid>`
* A summary of the new topology will be displayed, along with a listing of the existing cluster and the proposed changes. Unless you specified the `-y` (always answer "yes") option, you will be asked to confirm the changes before any actual work begins.
* Once you have confirmed the changes, IRONdb will start rebalancing the data. The new topology hash will be shown once it has been calculated.
*   To view progress, retrieve the [rebalance state](../api/api-specs.md) via GET of `/rebalance/state`:

    `curl http://<node>:<api-port>/rebalance/state`
*   To abort the rebalance, [stop the IRONdb service](operations.md#service-management) and remove the rebalance state file:

    `/irondb/localstate/.rebalance_state.json`

    on every node, including on any leaving nodes. Then start the service again.
