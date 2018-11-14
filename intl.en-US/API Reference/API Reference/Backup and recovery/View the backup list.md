# View the backup list {#reference_ptk_ypl_12b .reference}

## Description {#section_l21_v32_12b .section}

This API is used to query a set of instance backups. The set of backups must be in the success state to restore an instance.

RDS provides backup files for download.

-   When **DownloadLink** is NULL, RDS does not provide a download URL.
-   When **DownloadLink** is not NULL, you can use this URL to download the backup file through wget \(add double quotes\), a browser, or programming. The expiration time for this URL is specified by **LinkExpiredTime**. Use it before the expiration time. If it has expired, you can see the following error code during the download:

    ```
    <? xml version="1.0" encoding="UTF-8" ? >
    <Error>
    <Code>AccessDenied</Code>
    <Message>Request has expired.</Message>
    <Expires>2012-12-25T09:47:52.000Z</Expires>
    <ServerTime>2012-12-25T09:49:00.000Z</ServerTime>
    <RequestId>50D9768CA801C2F102005C70</RequestId>
    <HostId>oss-test.aliyun-inc.com</HostId>
    </Error>
    ```


## Request parameters {#section_qzx_w32_12b .section}

|Name|Type|Required|Description|
|----|----|--------|-----------|
|Action|String|Yes|Required parameter. Value: DescribeBackups.|
|DBInstanceId|String|Yes|Instance ID|
|BackupId|Integer|No|ID of the backup set|
|BackupStatus|String|No|Backup set status. Value range:-   Success: The backup is finished.
-   Failed: The backup fails.

|
|BackupMode|String|No|Backup mode. Value range:-   Automated: common task
-   Manual: temporary task

|
|StartTime|String|No|Query start time, for example, 2011-06-11T15:00Z.|
|EndTime|String|No|Query end time, which must be later than the query start time, for example, 2011-06-11T16:00Z.|
|PageSize|Integer|No|Number of records on every page. Values: 30, 50, and 100. Default value: 30.|
|PageNumber|Integer|No|Page number, which must be greater than 0 but must not exceed the maximum integer value. Default value: 1.|

## Return parameters {#section_a5x_zlh_12b .section}

|Name|Type|Description|
|----|----|-----------|
|<Public Return Parameters\>| |For more information, see [Public parameters](intl.en-US/API Reference/Use APIs/Public parameters.md#).|
|TotalRecordCount|Integer|Total number of records|
|PageNumber|Integer|Page number|
|PageRecordCount|Integer|Number of backup sets displayed on the current page|
|Items| ```
List<Backup>
```

 |Arrays composed of backups|

## Backup parameters {#section_awf_nql_12b .section}

|Name|Type|Description|
|----|----|-----------|
|BackupId|Integer|ID of the backup|
|DBInstanceId|String|Name of an instance|
|HostInstanceID|String|ID of the instance that generates the backup set. This parameter is used to indicate whether the master or slave instance generates a backup set.|
|BackupStatus|String|Backup status. Value range:-   Success: The backup is finished.
-   Failed: The backup fails.

|
|BackupStartTime|String|Start time of this backup. Format: YYYY-MM-DD’ T’ hh:mm:ssZ.|
|BackupEndTime|String|End time of this backup. Format: YYYYMM-DD’ T’ hh:mm:ssZ.|
|BackupType|String|Backup type. Value range:-   FullBackup
-   IncrementalBackup

|
|BackupMode|String|Backup mode. Value range:-   Automated
-   Manual

|
|BackupMethod|String|Backup method. Value range:-   Logical
-   Physical

|
|BackupDownloadURL|String|Download URL. The string is empty if the current backup cannot be downloaded.|
|BackupIntranetDownloadURL|String|Download URL. The string is empty if the current backup cannot be downloaded.|
|BackupSize|Long|Data file size. Unit: byte.|
|StoreStatus|String|Data backup storage status. Value range:-   Enabled
-   Disabled

|

