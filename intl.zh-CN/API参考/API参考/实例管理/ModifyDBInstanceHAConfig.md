# ModifyDBInstanceHAConfig {#reference_gx3_2cf_12b .reference}

## 描述 {#section_l21_v32_12b .section}

该接口修改实例的数据复制模式和高可用切换策略。

## 请求参数 {#section_qzx_w32_12b .section}

|名称|类型|是否必须|描述|
|Action|String|是|系统规定参数，取值为ModifyDBInstanceHAConfig。|
|DBInstanceId|String|是|实例名。|
|SyncMode|String|是|-   Sync：强同步；
-   Semi-sync：半同步；
-   Async：异步。

对于 SQL Server 2012/2016 双机高可用版，值为 Sync 或 Async。|
|HAMode|String|是| -   RPO：数据持久性优先；
-   RTO：实例可用性优先。

 |

## 返回参数 {#section_rpk_z32_12b .section}

|名称|类型|描述|
|--|--|--|
|<公共返回参数\>|-|详见[公共参数](intl.zh-CN/API参考/使用API/公共参数.md#)。|

