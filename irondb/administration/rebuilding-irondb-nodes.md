# Rebuilding IRONdb Nodes

If an IRONdb node or its data is damaged or lost, its data may be rebuilt from replicas elsewhere in the cluster. This process is known as "reconstituting" a node.

## Prerequisites

Reconstitution requires that at least one replica of every metric stream stored on the reconstituting node be available. A reconstitute operation cannot complete if more than `W-1` nodes are unavailable, including the node being reconstituted (`W` is the number of `write_copies` configured for the current topology.)

For example, given a cluster of 10 nodes (`N=10`) with 3 write copies (`W=3`), a node may be reconstituted if at least `N-(W-1)`, or 8, other nodes are available and healthy.

As this can be a long-running procedure, a terminal multiplexer such as `tmux` or `screen` is recommended to avoid interruption.

## Reconstitute Procedure

1. Log into the IRONdb node you wish to reconstitute as `root` or a privileged user. Make sure the IRONdb package is [up to date](../getting-started/installation.md#updating).
   * **Note:** If the entire old node was replaced (e.g., due to a hardware failure), or the ZFS pool has been recreated (due to hardware failure or administrative action), then you should repeat [initial installation](../getting-started/installation.md#installation-steps) and then [disable the service](operations.md#service-management). The installer will not interfere with an existing `irondb.conf` file but will ensure that all necessary ZFS datasets and node-id subdirectories have been created.
2. Make note of this node's topology UUID, found in the [imported topology](../getting-started/installation.md#import-topology). You may need to reference this configuration on another node if the node to be reconstituted is a fresh install. The node UUID will be referred to below as `<node_id>`.
3. If the IRONdb service is running, [stop it](operations.md#service-management).
4.  Make sure there is no lock file located at `/irondb/logs/snowth.lock`. If there is, remove it with the following command:

    ```
    rm -f /irondb/logs/snowth.lock
    ```
5. **If you repeated initial installation on this node, you may skip to the next step.** Otherwise, follow this procedure to clean out any incomplete or damaged data.
   1.  Run the following command to find the base ZFS dataset. This will create a shell variable, `BASE_DATASET`, that will be used in subsequent commands.

       ```
       BASE_DATASET=$(zfs list -H -o name /irondb)
       ```
   2.  Destroy the existing data using the following commands:

       ```
       zfs destroy -r $BASE_DATASET/data
       zfs destroy -r $BASE_DATASET/text
       zfs destroy -r $BASE_DATASET/hist
       zfs destroy -r $BASE_DATASET/hist_ingest
       zfs destroy -r $BASE_DATASET/hist_rollup
       zfs destroy -r $BASE_DATASET/localstate
       zfs destroy -r $BASE_DATASET/raw_db
       zfs destroy -r $BASE_DATASET/surrogate_db
       zfs destroy -r $BASE_DATASET/metadata
       zfs destroy -r $BASE_DATASET/metric_name_db
       zfs destroy -r $BASE_DATASET/nntbs
       ```
   3.  Wait for the data to be completely destroyed. To do this, periodically run the following command and wait until the value for all pools reads "0".

       ```
       zpool get freeing
       ```
   4.  Recreate the dataset structure by running the following commands:

       ```
       zfs create $BASE_DATASET/data
       zfs create $BASE_DATASET/hist
       zfs create $BASE_DATASET/hist_ingest
       zfs create $BASE_DATASET/hist_rollup
       zfs create $BASE_DATASET/text
       zfs create $BASE_DATASET/localstate
       zfs create $BASE_DATASET/metadata
       zfs create -o logbias=throughput $BASE_DATASET/raw_db
       zfs create -o logbias=throughput $BASE_DATASET/surrogate_db
       zfs create $BASE_DATASET/metric_name_db
       zfs create $BASE_DATASET/nntbs
       ```
   5.  Run the following commands to make the node-id subdirectories:

       ```
       mkdir /irondb/hist/<node_id>
       mkdir /irondb/hist_ingest/<node_id>
       mkdir /ironeb/hist_rollup/<node_id>
       mkdir /irondb/text/<node_id>
       mkdir /irondb/data/<node_id>
       mkdir /irondb/raw_db/<node_id>
       mkdir /irondb/surrogate_db/<node_id>
       mkdir /irondb/metadata/<node_id>
       mkdir /irondb/metric_name_db/<node_id>
       mkdir /irondb/nntbs/<node_id>
       ```
   6.  Make sure that all the directories are owned by the `nobody` user by running the following:

       ```
       chown -R nobody:nobody /irondb/
       ```
6.  Run IRONdb in reconstitute mode using the following command:

    ```
    /opt/circonus/bin/irondb-start -B
    ```
7.  Wait until the reconstitute operation has fetched 100% of its data from cluster peers. You can access the current percentage done as an auto-refreshing UI via:

    ```
    <node ip address>:<node port>/#reconstituteview
    ```

    or as raw JSON at:

    ```
    <node ip address>:<node port>/stats.json
    ```

    ...and looking at the "reconstitute" stats.

    **Note**: There may not be messages appearing on the console while this runs. This is normal. Do not stop the reconstitute. Completion percentages may pause for long periods of time during reconstitution.

    Current progress will be saved - if the process stops for any reason, everything should resume approximately where it was. A reconstitute may be resumed with the same command:

    ```
    /opt/circonus/bin/irondb-start -B
    ```

    Once the reconstituting node has retrieved all of its data, you will see the following on the console:

    ```
    Reconstitute Finished!
    ```
8. [Start the IRONdb service](operations.md#service-management).
