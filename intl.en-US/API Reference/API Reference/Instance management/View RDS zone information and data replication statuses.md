# View RDS zone information and data replication statuses {#reference_wgq_rw2_12b .reference}

## Description {#section_l21_v32_12b .section}

This interface is used to show instance zone information and data replication statuses.

## Request parameters {#section_qzx_w32_12b .section}

|Name|Type|Required|Description|
|----|----|--------|-----------|
|Action|String|Yes|Required parameter. Value: DescribeDBInstanceHAConfig.|
|DBInstanceId|String|Yes|Instance ID.|

## Return parameters {#section_rpk_z32_12b .section}

|Name|Type|Description|
|----|----|-----------|
|<Public Return Parameters\>| |For more information, see [Public parameters](intl.en-US/API Reference/Use APIs/Public parameters.md#).|
|DBInstanceId|String|Instance ID.|
|SyncMode|String|-   Sync: Synchronous.
-   Semi-sync: Semi-synchronous.
-   Async: Asynchronous.
-   :
-   :

For SQL Server 2012/2016 dual-machine high-availability version, the value is Sync or Async.|
|HAMode|String| -   RPO: Data persistence is preferred.
-   RTO: Instance availability is preferred.

 |
|HostInstanceInfos|List<NodeInfo\>|Master/slave node information.|

## NodeInfo {#section_c3m_3w2_12b .section}

|Name|Type|Description|
|----|----|-----------|
|NodeId|String|Unique ID of the master/slave node.|
|NodeType|String| -   Master: master node.
-   Slave: slave node.

 |
|RegionId|String|Data center.|
|ZoneId|String|Zone.|
|SyncStatus|String| -   NotAvailable:
-   Syncing: synchronization in process, with a probability of data loss during a switchover.
-   Synchronized: synchronization completed.
-   NotSupport: unsupported engine type or version.

 |
|LogSyncTime|String|The time when the standby database receives logs.|
|DataSyncTime|String|The time when the standby database receives the data.|

