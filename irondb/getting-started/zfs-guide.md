---
description: >-
  In the following guide we will demonstrate a typical IRONdb installation on
  Linux, using ZFS.
---

# ZFS Guide

This guide assumes a server with the following storage configuration:

* One or more OS drives with ext4 on LVM, md, etc., depending on installer choices and/or operator preference.
* 12 data drives attached via a SAS or SATA HBA (non-RAID) that will be used exclusively for ZFS.

## ZFS Terminology[​](https://docs.circonus.com/irondb/getting-started/zfs-guide#zfs-terminology) <a href="#zfs-terminology" id="zfs-terminology"></a>

If you are new to ZFS, there are some basic concepts that you should become familiar with to best utilize your server hardware with ZFS.

References:

* [OpenZFS Administration](http://open-zfs.org/wiki/System_Administration)
* [ZFS on Linux RHEL setup](https://github.com/zfsonlinux/zfs/wiki/RHEL-and-CentOS)
* [ZFS: The Last Word in Filesystems](https://wiki.chipp.ch/twiki/pub/CmsTier3/NFSServerZFSBackupANDdCache/zfs_last_presentation.pdf) Old but still largely relevant presentation introducing ZFS, from Sun Microsystems

### Pools[​](https://docs.circonus.com/irondb/getting-started/zfs-guide#pools) <a href="#pools" id="pools"></a>

Pools are the basis of ZFS storage. They are constructed out of "virtual devices" (vdevs), which can be individual disks or groupings of disks that provide some form of redundancy for writes to the group.

Review the `zpool` man page for details.

### Datasets[​](https://docs.circonus.com/irondb/getting-started/zfs-guide#datasets) <a href="#datasets" id="datasets"></a>

Datasets are logical groupings of objects within a pool. They are accessed in one of two ways: as a POSIX-compliant filesystem, or as a block device. In this guide we will only be dealing with the filesystem type.

Filesystem datasets are mounted in the standard UNIX hierarchy just as traditional filesystems are. The difference is that the "device" part of the mount is a hierarchical name, starting with the pool name, rather than a device name such as `/dev/sdc1`. The specific mountpoint of a given filesystem is determined by its `mountpoint` property. See the `zfs` man page for more information on ZFS dataset properties.

**Please note that IRONdb setup configures all necessary datatset properties. No pre-configuration is required.**

On Linux, ZFS filesystems are mounted at boot by the `zfs-mount` service. They are not kept in the traditional `/etc/fstab` file.

## Obtaining ZFS Packages[​](https://docs.circonus.com/irondb/getting-started/zfs-guide#obtaining-zfs-packages) <a href="#obtaining-zfs-packages" id="obtaining-zfs-packages"></a>

### RHEL and CentOS[​](https://docs.circonus.com/irondb/getting-started/zfs-guide#rhel-and-centos) <a href="#rhel-and-centos" id="rhel-and-centos"></a>

Follow the [RHEL & CentOS](https://github.com/zfsonlinux/zfs/wiki/RHEL-and-CentOS) getting-started guide. The kABI-tracking kmod version is the easiest to manage, as there is nothing to compile, and it is designed to work with the stock EL7 kernels.

### Ubuntu[​](https://docs.circonus.com/irondb/getting-started/zfs-guide#ubuntu) <a href="#ubuntu" id="ubuntu"></a>

Packages for ZFS are available from the standard Ubuntu repository.

```
apt-get install zfs
```

## Creating a ZFS Pool[​](https://docs.circonus.com/irondb/getting-started/zfs-guide#creating-a-zfs-pool) <a href="#creating-a-zfs-pool" id="creating-a-zfs-pool"></a>

IRONdb setup expects a zpool to exist, but will take care of creating all necessary filesystems and directories.

For best performance with IRONdb, consider using mirror groups. These provide the highest number of write IOPS, but at a cost of 50% of available raw storage. Balancing the capacity of individual nodes with the number of nodes in your IRONdb cluster is something that Apica Support can help you with.

In our example system we have 12 drives available for our IRONdb pool. We will configure six 2-way mirror groups, across which writes will be striped. This is similar to a RAID-10 setup. We will call our pool "data". To simplify the example command we are using the traditional `sdX` names, but it's recommended that you use [different identifiers](https://github.com/zfsonlinux/zfs/wiki/FAQ#selecting-dev-names-when-creating-a-pool) for your devices that are less susceptible to change and make it easier to maintain.

```
zpool create data \
    mirror sdc sdd \
    mirror sde sdf \
    mirror sdg sdh \
    mirror sdi sdj \
    mirror sdk sdl \
    mirror sdm sdn
```

Using the `zpool status` command we can see our new pool:

```
  pool: data
 state: ONLINE
  scan: none requested
config:

    NAME        STATE     READ WRITE CKSUM
    data        ONLINE       0     0     0
      mirror-0  ONLINE       0     0     0
        sdc     ONLINE       0     0     0
        sdd     ONLINE       0     0     0
      mirror-1  ONLINE       0     0     0
        sde     ONLINE       0     0     0
        sdf     ONLINE       0     0     0
      mirror-2  ONLINE       0     0     0
        sdg     ONLINE       0     0     0
        sdh     ONLINE       0     0     0
      mirror-3  ONLINE       0     0     0
        sdi     ONLINE       0     0     0
        sdj     ONLINE       0     0     0
      mirror-4  ONLINE       0     0     0
        sdk     ONLINE       0     0     0
        sdl     ONLINE       0     0     0
      mirror-5  ONLINE       0     0     0
        sdm     ONLINE       0     0     0
        sdn     ONLINE       0     0     0

errors: No known data errors
```

At this point you may wish to reboot the system to ensure that the pool is present at startup.

## Proceed to IRONdb Setup[​](https://docs.circonus.com/irondb/getting-started/zfs-guide#proceed-to-irondb-setup) <a href="#proceed-to-irondb-setup" id="proceed-to-irondb-setup"></a>

> This step is only required if using the standalone IRONdb product. If you are referring to this appendix as an on-premise Apica Inside user, there is no further manual setup required at this point. All IRONdb setup from this point is handled by the Apica Inside installer.

Now that you have created a ZFS pool you may begin the IRONdb [installation](installation.md). If you have multiple pools configured and you want to use a specific pool for IRONdb, you can use the `-z` option to the setup script.

```
/opt/apica/bin/setup-irondb (other options) -z data
```

The setup script takes care of creating the `/irondb` mountpoint and all other necessary filesystems, as well as setting the required properties on those filesystems. No other administrative action at the ZFS level should be required at this point.
