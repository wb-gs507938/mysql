# DescribeDBInstanceHAConfig {#reference_wgq_rw2_12b .reference}

## 描述 {#section_l21_v32_12b .section}

该接口用于查询实例高可用信息和数据复制状态。

## 请求参数 {#section_qzx_w32_12b .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是|系统规定参数，取值为DescribeDBInstanceHAConfig。|
|DBInstanceId|String|是|实例名。|

## 返回参数 {#section_rpk_z32_12b .section}

|名称|类型|描述|
|--|--|--|
|<公共返回参数\>| |详见[公共参数](cn.zh-CN/API参考/使用API/公共参数.md#)。|
|DBInstanceId|String|实例名称。|
|SyncMode|String|-   Sync：强同步
-   Semi-sync：半同步
-   Async：异步
-   ：
-   ：

对于 SQL Server 2012/2016 双机高可用版，值为 Sync 或 Async。|
|HAMode|String| -   RPO：数据持久性优先
-   RTO：实例可用性优先

 |
|HostInstanceInfos|List<NodeInfo\>|主备节点信息。|

## NodeInfo {#section_c3m_3w2_12b .section}

|名称|类型|描述|
|--|--|--|
|NodeId|String|主备节点的唯一标识。|
|NodeType|String| -   Master：主节点
-   Slave：备节点

 |
|RegionId|String|数据中心。|
|ZoneId|String|可用区。|
|SyncStatus|String| -   NotAvailable：
-   Syncing：同步中，切换可能会发生数据丢失
-   Synchronized：完成同步
-   NotSupport：引擎类型或者版本不支持

 |
|LogSyncTime|String|备库收到的日志时间点。|
|DataSyncTime|String|备库当前的数据时间点。|

