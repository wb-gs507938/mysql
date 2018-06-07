# DescribeBackups {#reference_ptk_ypl_12b .reference}

## 描述 {#section_l21_v32_12b .section}

查询实例的备份集。备份集的状态必须是完成备份，才能用于恢复。

RDS提供备份文件文件下载：

-   当DownloadLink为NULL时，表示RDS没有提供下载链接URL。
-   当DownloadLink不为NULL时，用户可以根据此URL，通过wget（请加双引号）、浏览器、编写程序下载备份文件，此URL已设置过期时间LinkExpiredTime，请在过期时间之前使用。若过期，用户在下载时，将会出现如下错误码：

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


## 请求参数 {#section_qzx_w32_12b .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是|系统规定参数，取值：DescribeBackups。|
|DBInstanceId|String|是|实例名。|
|BackupId|Integer|否|备份集ID。|
|BackupStatus|String|否|备份集状态。取值范围：-   Success：完成备份
-   Failed：备份失败

|
|BackupMode|String|否|备份类型。取值范围：-   Automated：常规任务
-   Manual：临时任务

|
|StartTime|String|是|查询开始时间，格式如：2011-06-11T15:00Z。|
|EndTime|String|是|查询结束时间，格式如：2011-06-11T16:00Z，且大于查询开始时间。|
|PageSize|Integer|否|每页记录数，取值：30/50/100；默认值：30。|
|PageNumber|Integer|否|页码，大于0且不超过Integer的最大值。默认值：1。|

## 返回参数 {#section_a5x_zlh_12b .section}

|名称|类型|描述|
|--|--|--|
|<公共返回参数\>| |详见[公共参数](cn.zh-CN/API参考/使用API/公共参数.md#)。|
|TotalRecordCount|Integer|总记录数。|
|PageNumber|Integer|页码。|
|PageRecordCount|Integer|本页备份集个数。|
|Items| ```
List<Backup>
```

 |由Backup组成的数组。|

## Backup参数 {#section_awf_nql_12b .section}

|名称|类型|描述|
|--|--|--|
|BackupId|Integer|备份ID。|
|DBInstanceId|String|实例名。|
|HostInstanceID|String|产生备份集的实例编号，用于区分该备份集产生于主实例或从实例。|
|BackupStatus|String|备份状态：-   Success：完成备份
-   Failed：备份失败

|
|BackupStartTime|String|本次备份开始时间，格式为YYYY-MM-DD’T’hh:mm:ssZ。|
|BackupEndTime|String|本次备份结束时间，格式为YYYYMM-DD’T’hh:mm:ssZ。|
|BackupType|String|备份类型：-   FullBackup：全量备份
-   IncrementalBackup：增量备份

|
|BackupMode|String|备份模式：-   Automated：系统自动备份
-   Manual：手动备份

|
|BackupMethod|String|备份方法：-   Logical：逻辑备份
-   Physical：物理备份

|
|BackupDownloadURL|String|公网下载链接的地址，若当前不可下载，则为空串。|
|BackupIntranetDownloadURL|String|内网下载链接的地址，若当前不可下载，则为空串。|
|BackupSize|Long|备份文件大小，单位：Byte。|
|StoreStatus|String|数据备份存储状态：-   Enabled：可删除
-   Disabled：不可删除

|

