# Query SQL audit logs {#reference_n4g_1f3_12b .reference}

## Description {#section_l21_v32_12b .section}

Query the SQL audit logs generated for an instance.

## Request parameters {#section_qzx_w32_12b .section}

|Name|Type|Required?|Description|
|----|----|---------|-----------|
|Action|String|Yes|Required parameter. Value: DescribeSQLLogRecords.|
|DBInstanceId|String|Yes|Instance ID.|
|Database|String|No|Default value: All.|
|User|String|No|Default value: All.|
|Form|String|No|File: trigger of audit log file generation. If this parameter is set to File, only public parameters are returned, and you must call DescribeSQLLogFilesinterface to obtain the final download file address; if this parameter is set to Stream, data streams are returned. Default value: Stream.|
|QueryKeywords|String|No|Keywords used for query, which are separated by spaces. Up to 10 keywords can be entered.|
|StartTime|String|Yes|Query start time. Format: yyyy-MM-dd’T’HH:mm:ssZ.|
|EndTime|String|Yes|Query end time, which must be later than the query start time. Format:yyyy-MM-dd’T’HH:mm:ssZ.|
|PageSize|Integer|No|Number of records on every page. Values: 30, 50, and 100; default value: 30.|
|PageNumber|Integer|No|Page number, which must be greater than 0, but must not exceed the maximum Integer value. Default value: 1.|

## Return parameters {#section_a5x_zlh_12b .section}

|Name|Type|Description|
|----|----|-----------|
|<Public Return Parameters\>| |For more information, see [Public parameters](intl.en-US/API Reference/Use APIs/Public parameters.md#).|
|TotalRecordCount|Integer|Total number of records.|
|PageNumber|Integer|Page number.|
|PageRecordCount|Integer|Number of SQL logs displayed on the current page.|
|Items| ```
List<SQLRecord>
```

 |None.|

## SQLRecord parameters { .section}

|Name|Type|Description|
|----|----|-----------|
|DBName|String|Name of a database.|
|AccountName|String|Name of an account.|
|HostAddress|String|Client IP address.|
|SQLText|String|SQL statement.|
|TotalExecutionTimes|Long|Time consumed, in the unit of microseconds.|
|ReturnRowCounts|Long|Number of returned records.|
|ThreadID|String|Thread ID.|
|ExecuteTime|String|Execution time. Format: yyyy-MM-dd’T’HH:mm:ss Z, for example, 2011-05-30 T12:11:20Z.|

## Request example {#section_l4g_pj2_12b .section}

```
https://rds.aliyuncs.com/?Action=DescribeSQLLogRecords
&DBInstanceId=riauvjz6zajfiq6ba1370329449201
&StartTime=2011-06-11T15:00:00Z
&EndTime=2013-06-05T15:00:00Z
&<Public Request Parameters>
```

## Response example {#section_xtg_rj2_12b .section}

**XML format**

```
<DescribeSQLLogRecordsResponse> 
  <RequestId>08A3B71B-FE08-4B03-974F-CC7EA6DB1828</RequestId>
  <TotalRecordCount>1</TotalRecordCount>
  <PageNumber>1</PageNumber>
  <PageRecordCount >1<PageRecordCount>
  <Items>
    <SQLRecord>
    <DBName>test</DBName>
    <AccountName>accounttest</AccountName>
    <HostAddress>192.168.0.121</HostAddress>
    <SQLText>update test.zxb set id=0 limit 1</SQLText>
    <TotalExecutionTimes >12</TotalExecutionTimes>
    <ReturnRowCounts>34</ReturnRowCounts>
    <ExecuteTime>2011-06-11T15:00:23Z</ExecuteTime>
    </SQLRecord>
</Items>
</DescribeSQLLogRecordsResponse>
```

**JSON format**

```
{
"PageNumber":1,
"TotalRecordCounts":1,
"ItemsCounts":1
"SQLItems":
{"SQLItem":
[
{
"DBName":”test”
"AccountName":”accounttest”
"HostAddress":” 192.168.0.121”
"SQLText":”update test.zxb set id=0 limit 1”
"TotalExecutionTimes":12
"ReturnRowCounts":34
"ExecuteTime":”2011-06-11T15:00:23Z”
}
]
},
"RequestId": "08A3B71B-FE08-4B03-974F-CC7EA6DB1828"
}
```

