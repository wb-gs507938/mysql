# Query the SQL audit file list {#reference_j2q_fg3_12b .reference}

## Description {#section_l21_v32_12b .section}

Query the SQL audit file list.

## Request parameters {#section_qzx_w32_12b .section}

|Name|Type|Required|Description|
|----|----|--------|-----------|
|Action|String|Yes|Required parameter. Value: DescribeSQLLogFiles.|
|DBInstanceId|String|Yes|Instance ID.|

## Return parameters {#section_a5x_zlh_12b .section}

|Name|Type|Description|
|----|----|-----------|
|<Public Return Parameters\>| |For more information, see [Public parameters](intl.en-US/API Reference/Use APIs/Public parameters.md#).|
|TotalRecordCount|Integer|Total number of records.|
|PageNumber|Integer|Page number.|
|PageRecordCount|Integer|Number of records displayed on the current page.|
|Items| ```
List<LogFile>
```

 |Array consisting of audit files.|

## LogFile parameters { .section}

|Name|Type|Description|
|----|----|-----------|
|FileID|Integer|ID of a file.|
|DBInstanceId|String|Instance ID.|
|LogStatus|String|Success: archiving completed: Failed: archiving failed; Generating: archiving underway.|
|LogStartTime|String|SQL start time.|
|LogEndTime|String|SQL end time.|
|LogDownloadURL|String|Download URL. This parameter is set to a null string if download cannot be performed for the moment.|
|LogSize|Long|Log file size, in the unit of bytes.|

##   {#section_l4g_pj2_12b .section}

##   {#section_xtg_rj2_12b .section}

