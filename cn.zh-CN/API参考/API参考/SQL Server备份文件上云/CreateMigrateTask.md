# CreateMigrateTask {#reference_ab3_f5l_12b .reference}

## 描述 {#section_l21_v32_12b .section}

从OSS上的备份文件还原到RDS，限制条件如下：

-   目前，仅适用于SQL Server实例。
-   源文件必须是源数据库全量备份（FULL）文件。


## 请求参数 {#section_qzx_w32_12b .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是|系统规定参数，取值：CreateMigrateTask。|
|DBInstanceId|String|是|实例ID。|
|DBName|String|是|数据库名称。|
|BackupMode|String|是|任务类型，目前始终取FULL值。取值如下：-   FULL：表示全量备份文件，默认值为FULL。
-   UPDF：表示增量文件，可以是差异备份文件或者日志文件。

|
|IsOnlineDB|String|是|是否将还原后的数据库带上线，以便用户可以访问，可选值为True和False，默认值为True。目前，这个值恒定为True。|
|MigrateTaskId|String|否|迁移任务ID：-   BackupMode=FULL时，该值为空，默认值（兼容2008）。
-   BackupMode=UPDF时，该值为对应FULL任务的ID。

|
|CheckDBMode|String|否|打开数据库后一致性检查方法：-   SyncExecuteDBCheck：同步检查。
-   AsyncExecuteDBCheck：异步检查，默认值，2008r2版本始终为该值。
-   IsOnlineDB=True时，该值有效。

|
|OSSUrls|String|是|备份文件所在OSS的共享URL地址（Encode编码后的URL）。-   当有多个备份文件地址时，每个URL之间使用`|`隔开，目前只能传入一个URL。
-   对于SQL Server 2008 R2版本，本参数为必须。

|
|OssObjectPositions|String|是|OSS的组成部分。对于SQL Server 2012及以上版本，本参数为必须。

取值：ss-ap-southeast-1.aliyuncs.com:rdsmssqlsingapore:/autotest\_2008R2\_TestMigration\_FULL.bak；

-   OSS Endpoint地址：oss-ap-southeast-1.aliyuncs.com；
-   OSS Bucket名字：rdsmssqlsingapore；
-   OSS上的备份文件Key:/autotest\_2008R2\_TestMigration\_FULL.bak；默认为空（兼容2008）。

|

## 返回参数 {#section_a5x_zlh_12b .section}

|名称|类型|描述|
|--|--|--|
|<公共返回参数\>|-|详见[公共参数](intl.zh-CN/API参考/使用API/公共参数.md#) 。|
|RequestId|String|请求ID。|
|DBInstanceId|String|实例ID。|
|DBName|String|数据库名称。|
|TaskId|String|任务ID。|
|MigrateTaskId|String|迁移任务ID。|
|BackupMode|String|任务类型，目前始终取FULL值。取值如下：-   FULL：全量备份文件一次性迁入。
-   UPDF：表示增量文件，可以是差异备份文件或者日志文件，默认值 UPDF。

|

## 请求示例 {#section_gdg_kks_c2b .section}

```
https://rds.aliyuncs.com/?Action=CreateMigrateTask
&BackupMode=FULL
&IsOnlineDB=True
&DBName=testDB
&DBInstanceId=rm-xxxxxxx
&OssObjectPositions=oss-cn-beijing.aliyuncs.com:atp-test-on-ecs:Migration/TestMigration_FULL_20180523225534.bak
&<公共请求参数>
```

## 返回示例 {#section_trc_4ks_c2b .section}

**json格式**

```
{u'DBInstanceId': u'rm-xxxxxxx', u'BackupMode': u'FULL', u'MigrateTaskId': u'106121', u'RequestId': u'67E0DD7F-7219-4F67-AAE7-B27273921303', u'TaskId': u'68244691', u'DBName': u'TestDB'}
```

