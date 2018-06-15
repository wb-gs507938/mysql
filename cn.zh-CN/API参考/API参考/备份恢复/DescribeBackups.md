# DescribeBackups {#reference_ptk_ypl_12b .reference}

## 描述 {#section_xzk_krv_d2b .section}

该接口用于查询实例的备份集。备份集的状态必须是完成备份，才能用于恢复。

```
<?xml version="1.0" encoding="UTF-8" ?>
<Error>
<Code>AccessDenied</Code>
<Message>Request has expired.</Message>
<Expires>2012-12-25T09:47:52.000Z</Expires>
<ServerTime>2012-12-25T09:49:00.000Z</ServerTime>
<RequestId>50D9768CA801C2F102005C70</RequestId>
<HostId>oss-test.aliyun-inc.com</HostId>
</Error>
```

## 输入参数 {#section_hmb_rrv_d2b .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是|系统规定参数，取值：DescribeBackups。|
|DBInstanceId|String|是|实例名。|
|BackupId|Integer|否|备份集ID。|
|BackupStatus|String|否|备份集状态，取值如下：-   Success：完成备份；
-   Failed：备份失败。

|
|BackupMode|String|否|备份类型。取值范围：-   Automated：常规任务；
-   Manual：临时任务。

|
|StartTime|String|是|查询开始时间，格式如：2011-06-11T15:00Z。|
|EndTime|String|是|查询结束时间，格式如：2011-06-11T16:00Z，且大于查询开始时间。|
|PageSize|Integer|否|每页记录数，取值：30/50/100；默认值：30。|
|PageNumber|Integer|否|页码，大于0且不超过Integer的最大值。默认值：1。|

## 返回参数 {#section_xbt_tsv_d2b .section}

|参数|类型|说明|
|--|--|--|
|RequestId|String|详见[公共参数](cn.zh-CN/API参考/使用API/公共参数.md#)|
|TotalRecordCount|Integer|总记录数。|
|PageNumber|Integer|页码。|
|PageRecordCount|Integer|本页备份集个数。|
|Items|List|由Backup组成的数组。|

## Backup参数 {#section_yxw_vsv_d2b .section}

|名称|类型|描述|
|--|--|--|
|BackupId|Integer|备份ID。|
|DBInstanceId|String|实例名。|
|HostInstanceID|String|产生备份集的实例编号，用于区分该备份集产生于主实例或从实例。|
|BackupStatus|String|备份状态：-   Success：完成备份；
-   Failed：备份失败。

|
|BackupStartTime|String|本次备份开始时间，格式为YYYY-MM-DD’T’hh:mm:ssZ。|
|BackupEndTime|String|本次备份结束时间，格式为YYYYMM-DD’T’hh:mm:ssZ。|
|BackupType|String|备份类型：-   FullBackup：全量备份；
-   IncrementalBackup：增量备份。

|
|BackupDBNames|String|数据库名称。|
|BackupDownloadURL|String|OSS备份下载链接。|
|BackupIntranetDownloadURL|String| |
|BackupLocation|String|备份文件存储在OSS中的位置。|
|BackupMethod|String| -   Logical：逻辑备份；
-   Physical：物理备份；
-   默认值为Physical，逻辑备份不支持没有数据库的实例。SQL Server仅支持物理备份。

 |
|BackupMode|String|备份类型，取值如下：-   Automated：常规任务；
-   Manual：临时任务。

|
|BackupScale|String|逻辑备份可选备份范围：-   Database：单库备份；
-   DBInstance：全实例备份。

|
|BackupSize|String|备份占用空间，单位：Byte，NULL表示没有数据，全量。|
|HostInstanceID|String| |
|StoreStatus|String| |

