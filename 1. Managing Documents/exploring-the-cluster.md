# Exploring the cluster

we use the `_cat` API to check info about the cluster. `?v` is used for verbosity (should use this)

## Checking the cluster health

```
GET /_cat/health?v
```

when we get this info, we will get the status of the cluster.

**green** means everything is good, and cluster is fully functional.

**yellow** means all the cluster's data is available, but some replicas are not yet allocated. The cluster is still fully functional in this case, but there is a risk of data loss in case a node fails. 

NOTE: in the default elasticsearch config, there is no replication. Which is why it is most likely yellow.

**red**: some of the cluster's data is not available. Chances are, one or more nodes have gone down. e.g. if a hard drive calls it quits.

## Listing the cluster's nodes

```
GET /_cat/nodes?v
```

we will see the nodes in the cluster:

e.g.:

```
ip        heap.percent ram.percent cpu load_1m load_5m load_15m node.role master name
127.0.0.1           44          99  26    3.18                  mdi       *      wPhbZ1T
```

## Listing the cluster's indices

```
GET /_cat/indices?v
```

Like clusters, the indices have their own green yellow red statuses.

The index status is returned for all the masters and replicas.

## Checking the shard allocation

```
GET /_cat/allocation?v
```

## Checking which nodes contain which shards

```
GET /_cat/shards?v
```

result: we see where each shard section is stored.

NOTE: `prirep` means whether the section is a primary or a replica.

```
 index        shard prirep state      docs   store ip        node
products     1     p      STARTED     117    17kb 127.0.0.1 wPhbZ1T
products     1     r      UNASSIGNED
products     2     p      STARTED     128  17.9kb 127.0.0.1 wPhbZ1T
products     2     r      UNASSIGNED
products     4     p      STARTED     127  24.3kb 127.0.0.1 wPhbZ1T
products     4     r      UNASSIGNED
products     3     p      STARTED     115  22.6kb 127.0.0.1 wPhbZ1T
products     3     r      UNASSIGNED
products     0     p      STARTED     113    23kb 127.0.0.1 wPhbZ1T
products     0     r      UNASSIGNED
```

