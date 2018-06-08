# CreateMigrateTask {#reference_ab3_f5l_12b .reference}

## 描述 {#section_l21_v32_12b .section}

从OSS上的备份文件还原到RDS，限制条件如下：

-   目前，仅支持SQL Server 2008 R2版本的实例。

-   源文件必须是源数据库全量备份（FULL）文件。


## 请求参数 {#section_qzx_w32_12b .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是|系统规定参数，取值：CreateMigrateTask。|
|DBInstanceId|String|是|实例ID。|
|DBName|String|是|数据库名称。|
|BackupMode|String|是|任务类型，目前始终取FULL值。取值如下：-   FULL：全量备份文件一次性迁入
-   DIFF：增量备份文件一次性迁入
-   LOG：增量备份文件多次迁入

|
|IsOnlineDB|String|是|是否将还原后的数据库带上线，以便用户可以访问，可选值为True和False，默认值为True。目前，这个值恒定为True。|
|OSSUrls|String|是|备份文件所在OSS的共享URL地址（Encode编码后的URL）。当有多个备份文件地址时，每个URL之间使用`|`隔开，目前只能传入一个URL。|

## 返回参数 {#section_a5x_zlh_12b .section}

|名称|类型|描述|
|--|--|--|
|<公共返回参数\>|-|详见[公共参数](cn.zh-CN/API参考/使用API/公共参数.md#) 。|
|RequestId|String|请求ID。|
|DBInstanceId|String|实例ID。|
|DBName|String|数据库名称。|
|TaskId|String|任务ID。|
|MigrateTaskId|String|迁移任务ID。|
|BackupMode|String|任务类型，目前始终取FULL值。取值如下：-   FULL：全量备份文件一次性迁入
-   DIFF：增量备份文件一次性迁入
-   LOG：增量备份文件多次迁入

|

