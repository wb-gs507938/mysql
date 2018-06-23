# View the slow log list {#reference_i4z_lc3_12b .reference}

## Description {#section_l21_v32_12b .section}

Query a summary of slow queries for a database under a user instance in a certain time range, and this operation supports querying by page. Slow queries return different SQLSlowLog parameter values for the SQL Server and MySQL instances. For details, see the SQLSlowLog parameter table below.

## Request parameters {#section_qzx_w32_12b .section}

|Name|Type|Required?|Description|
|----|----|---------|-----------|
|Action|String|Yes|Required parameter. Value: DescribeSlowLogs.|
|DBInstanceId|String|Yes|Instance ID.|
|StartTime|String|Yes|Query start date. Format: YYYY-MM-DDZ, for example, 2011-05-30Z.|
|EndTime|String|Yes|Query end date, which cannot be earlier than the query start date. Format: YYYY-MM-DDZ, for example, 2011-05-30Z.|
|DBName|String|No|Name of a database.|
|SortKey|String|No|Sorting basis. Values are as follows:-   TotalExecutionCounts: sorting in the descending order of execution times;
-   TotalQueryTimes: sorting in the descending order of the total execution duration;
-   TotalLogicalReads: sorting in the descending order of the total number of logical reads;
-   TotalPhysicalReads: sorting in the descending order of the total number of physical reads. This parameter is effective for SQL Server instances and must be used for SQL Server instances.

|
|PageSize|Integer|No|Number of records on every page. Values: 30, 50, and 100; default value: 30.|
|PageNumber|Integer|No|Page number, which must be greater than 0, but must not exceed the maximum Integer value. Default value: 1.|

## Return parameters {#section_a5x_zlh_12b .section}

|Name|Type|Description|
|----|----|-----------|
|<Public Return Parameters\>| |For details, see [Public parameters](intl.en-US/API Reference/Use APIs/Public parameters.md#).|
|Engine|String|Database type.|
|StartTime|String|Query start date. Format: YYYY-MM-DDZ, for example, 2011-05-30Z.|
|EndTime|String|Query end date. Format: YYYY-MM-DDZ, for example, 2011-05-30Z.|
|TotalRecordCount|Integer|Total number of records.|
|PageNumber|Integer|Page number.|
|PageRecordCount|Integer|Number of SQL statements displayed on the current page.|
|Items|`List<SQLSlowLog>`| |

## SQLSlowLog parameters for MySQL {#section_vgj_vc3_12b .section}

|Name|Type|Description|
|----|----|-----------|
|DBName|String|Name of a database.|
|SQLText|String|Query statement.|
|MySQLTotalExecutionCounts|Long|Total number of execution times.|
|MySQLTotalExecutionTimes|Long|Total execution duration, in the unit of seconds.|
|MaxExecutionTime|Long|Maximum execution duration, in the unit of seconds.|
|TotalLockTimes|Long|Total lock duration, in the unit of seconds.|
|MaxLockTime|Long|Maximum lock duration, in the unit of seconds.|
|ParseTotalRowCounts|Long|Total number of parsed rows.|
|ParseMaxRowCount|Long|Maximum number of parsed rows.|
|ReturnTotalRowCounts|Long|Total number of returned rows.|
|ReturnMaxRowCount|Long|Maximum number of returned rows.|
|CreateTime|String|Data generation date. Format: “yyyy-MM-ddZ”, for example, 2011-05-30Z.|

## SQLSlowLog for SQL Server {#section_xkq_xc3_12b .section}

|Name|Type|Description|
|----|----|-----------|
|SQLText|String|Query statement.|
|SQLServerTotalExecutionCounts|Long|Total number of execution times.|
|SQLServerTotalExecutionTimes|Long|Total execution duration, in the unit of milliseconds.|
|TotalLogicalReadcounts|Long|Total number of logical reads.|
|TotalPhysicalReadcounts|Long|Total number of physical reads.|
|ReportTime|String|Data report generation date. Format: “yyyy-MM-ddZ”, for example, 2011-05-30Z.|

## Request example {#section_l4g_pj2_12b .section}

```
https://rds.aliyuncs.com/?Action=DescribeSlowLogs
&DBInstanceId=riauvjz6zajfiq6ba1370329449201
&StartTime=2011-06-11Z
&EndTime=2011-12-11Z
&SortKey= TotalExecutionCounts
&<Public Request Parameters>
```

## Response example {#section_xtg_rj2_12b .section}

**XML format:**

```
<DescribeSlowLogsResponse> 
  <RequestId>A5409D02-D661-4BF3-8F3D-0A814D0574E7</RequestId>
  <DBInstanceID>riauvjz6zajfiq6ba1370329449201</DBInstanceID> 
  <Engine>SQLServer</Engine>
  <StartTime>2011-06-11Z</StartTime> 
  <EndTime>2011-12-11Z</EndTime> 
  <TotalRecordCount>1</TotalRecordCount>
  <PageNumber>1</PageNumber>
  <PageRecordCount>1</PageRecordCount>
  <Items>
    <SQLSlowLog>
    <SQLText>update test.zxb set id=0 limit 1</SQLText>
    <SQLServerTotalExecutionCounts>178</SQLServerTotalExecutionCounts>
    <SQLServerTotalExecutionTimes>189</SQLServerTotalExecutionTimes>
    <TotalLogicalReadcounts>89</TotalLogicalReadcounts>
    <TotalPhysicalReadcounts>90</TotalPhysicalReadcounts>
    <ReportTime>2013-11-12Z</ReportTime>
   </SQLSlowLog>
  </Items>
</DescribeSlowLogsResponse>
```

**JSON format:**

```
{
    "RequestId":"A5409D02-D661-4BF3-8F3D-0A814D0574E7"
"StartTime":"2011-06-11Z ",
"EndTime":"2011-12-11Z ",
"Engine":"SQLServer",
"PageNumber":1,
"PageRecordCount":1,
"TotalRecordCount"：1,
"Items":
{"SQLSlowLog":
[
{ "SQLText":”update test.zxb set id=0 limit 1”
"SQLServerTotalExecutionCounts":178
"SQLServerTotalExecutionTimes":189
"TotalLogicalReadcounts":89
"TotalPhysicalReadcounts":90
"ReportTime":"2013-11-12Z "
}
]
}
}
```

