# CreateMigrateTask {#reference_ab3_f5l_12b .reference}

通过将OSS上的备份文件还原到RDS实例，实现数据上云。

## 请求参数 {#section_qzx_w32_12b .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是| 系统规定参数，取值：

 CreateMigrateTask

 |
|DBInstanceId|String|是|实例ID。|
|DBName|String|是|数据库名称。|
|BackupMode|String|是| 迁移上云任务类型，取值为：

-   FULL：表示通过全量备份文件去执行还原操作。
-   UPDF：表示通过增量文件或者日志文件去还原增量部分的数据。

 默认值为FULL。

 |
|IsOnlineDB|String|是| 是否将还原后的数据库带上线，便于用户访问，取值为：

 -   True：将数据库带上线。
-   False：不将数据库带上线。

 默认值为True。

**说明：** 对于 SQL Server 2008 R2 版本实例，该值恒定为True。

 |
|OSSUrls|String|否| 备份文件所在OSS共享URL地址（Encode编码后的URL）。

 有多个地址时，先使用“|”隔开，再编码后传入参数。

 默认值为空。

**说明：** 该参数对于 SQL Server 2008 R2 版本实例是必传参数。

 |
|OssObjectPositions|String|否| OSS的组成部分。取值由3段组成：oss-ap-southeast-1.aliyuncs.com:rdsmssqlsingapore:/autotest\_2008R2\_TestMigration\_FULL.bak

-   OSS Endpoint地址：oss-ap-southeast-1.aliyuncs.com
-   OSS Bucket名字：rdsmssqlsingapore
-   OSS上的备份文件Key：/autotest\_2008R2\_TestMigration\_FULL.bak

 **说明：** 

-   该参数对于 SQL Server 2008 R2 版本实例是可选参数。
-   该参数对于 SQL Server 2008 R2 以上版本实例是必传参数。

 |
|MigrateTaskId|String|否|迁移任务ID：-   BackupMode=FULL时，该值为空。（兼容RDS for SQLServer 2008 R2）。
-   BackupMode=UPDF时，该值为对应FULL任务的ID。

默认值为FULL。

**说明：** 

-   IsOnlineDB=True时，BackupMode必须取值为FULL。
-   IsOnlineDB=False时，BackupMode必须为UPDF。

|
|CheckDBMode|String|否|打开数据库后一致性检查方法，取值为：-   SyncExecuteDBCheck：同步执行DB检查。
-   AsyncExecuteDBCheck：异步执行DB检查。

默认值为AsyncExecuteDBCheck（兼容 SQL Server 2008 R2）。

**说明：** 当IsOnlineDB=True时，该值有效。

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
|BackupMode|String| 迁移上云任务类型，取值为：

-   FULL：表示通过全量备份文件去执行还原操作。
-   UPDF：表示通过增量文件或者日志文件去还原增量部分的数据。

 默认值为FULL。

 |

## 错误码 {#section_gqh_tqj_sfb .section}

以下为本接口特有的错误码。更多错误码，请访问 [API 错误中心](https://error-center.aliyun.com/status/product/Rds)。

|错误代码|描述|HTTP状态码|
|----|--|-------|
|InvalidFile|The operation does not support this kind of file.|400|
|InvalidInstanceState|Current DB instance state does not support this operation.|403|
|IncorrectDBInstanceType|The DB instance state does not support this operation.|400|
|InvalidInstanceType|The DB instance type does not support this operation.|400|
|InvalidInstanceLockMode|The DB instance lock mode does not support this operation.|400|
|InvalidDBName|The instance does not have the specified DB name.|400|
|InvalidDBType|Current DB type does not support this operation.|400|
|InvalidDBState|Current DB state does not support this operation.|400|
|ExceedUploadTime|UploadTimesQuotaExceeded: Exceeding the daily upload times of this DB.|400|
|InvalidOSSURL|The Specified OSS URL is not valid.|400|
|ExceedDiskSize|The file size exceeding the disk size.|400|

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

**JSON格式**

```
{"DBInstanceId": "rm-xxxxxxx", "BackupMode": "FULL", "MigrateTaskId": "106121", "RequestId": "67E0DD7F-7219-4F67-AAE7-B27273921303", "TaskId": "68244691", "DBName": "TestDB"}
```

