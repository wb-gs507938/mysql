# DeleteBackup {#reference_bwt_vtl_12b .reference}

删除实例的备份集

只删除实例自身的备份集，不会删除所关联实例（只读、灾备、克隆等）的备份集。

实例必须满足以下条件，否则将操作失败：

-   实例状态为运行中。
-   实例引擎为RDS for MySQL、RDS for PostgreSQL或RDS for PPAS。

## 请求参数 {#section_qzx_w32_12b .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是| 要执行的操作，取值：

 DeleteBackup

 |
|DBInstanceId|String|是|实例ID。|
|BackupId|String|是| 备份集ID。

 可通过[DescribeBackups](intl.zh-CN/API参考/备份恢复/DescribeBackups.md#)获取。支持传入多组值，以英文逗号（,）隔开，单次最多传入100个。只支持删除[DescribeBackups](intl.zh-CN/API参考/备份恢复/DescribeBackups.md#)中存储状态为Enable的备份集。

 |

## 返回参数 {#section_a5x_zlh_12b .section}

|参数|类型|说明|
|--|--|--|
|<公共返回参数\>|-|详见[公共参数](intl.zh-CN/API参考/使用API/公共参数.md#)。|

