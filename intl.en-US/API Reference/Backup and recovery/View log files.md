# View log files {#concept_ytn_cjp_bfb .concept}

This API is used to query log files of RDS instances and download links of the files.

**Note:** It applies only to RDS for SQL Server instances.

## Request parameters {#section_bvb_kwj_n2b .section}

|Name|Type|Required or not|Description|
|----|----|---------------|-----------|
|Action|String|Yes|Required parameter. Value: DescribeLogBackupFiles|
|DBInstanceId|String|Yes|Instance ID|
|StartTime|String|Yes|Start time of the query. Format: yyyy-mm-dd’T’hh:mm:ssZExample: 2018-10-31T08:40Z

|
|EndTime|String|Yes|End time of the query. Format: yyyy-mm-dd’T’hh:mm:ssZExample: 2018-10-31T08:40Z

It must be later than the start time of the query.

|
|PageSize|Integer|No|Maximum number of log files displayed on each page. -   30
-   50
-   100

Default value: 30|
|PageNumber|Integer|No|Page number. It must be greater than 0 and cannot exceed the largest value of the Integer data type.Default value: 1

|

## Return parameters {#section_ugq_nwj_n2b .section}

|Name|Type|Required|
|----|----|--------|
|<Common Return Parameters\>|String|For more information, see [Public parameters](intl.en-US/API Reference/Use APIs/Public parameters.md#).|
|TotalRecordCount|Integer|Total number of log files|
|PageNumber|Integer|Page number|
|PageRecordCount|Integer|Number of log files displayed on a page|
|Items|List<LogBackupFiles\>|Log file list|

**LogBackupFiles parameters**

|Name|Type|Required|
|----|----|--------|
|FileSize|Long|Log file size. Unit: byte|
|LogBeginTime|String|Start time of a log file|
|LogEndTime|String|End time of a log file|
|DownloadLink|String|HTTP download linkNULL indicates that no download link is provided.

|
|LinkExpiredTime|String|Link expiration time. Example: 2011-06-11T15:00:00ZIf you attempt to download a log file after its download link has expired, an error message similar to the following is displayed:

```
<? xml version="1.0" encoding="UTF-8" ? >
<Error>
<Code>AccessDenied</Code>
<Message>Request has expired. </Message>
<Expires>2012-12-25T09:47:52.000Z</Expires>
<ServerTime>2012-12-25T09:49:00.000Z</ServerTime>
<RequestId>50D9768CA801C2F102005C70</RequestId>
<HostId>oss-test.aliyun-inc.com</HostId>
</Error>
```

|

