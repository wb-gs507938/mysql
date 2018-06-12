# View slow log details {#reference_rfc_fd3_12b .reference}

## Description {#section_l21_v32_12b .section}

Query slow log details for an instance in a certain time range. MySQL, PostgreSQL, and PPAS instances are supported.

## Request parameters {#section_qzx_w32_12b .section}

|Name|Type|Required|Description|
|----|----|--------|-----------|
|Action|String|Yes|Required parameter. Value: DescribeSlowLogRecords|
|DBInstanceId|String|Yes|Instance ID.|
|StartTime|String|Yes|Query start date. Format: YYYY-MM-DD’T’HH:mmZ, for example, 2011-06-11 T15:00Z.|
|EndTime|String|Yes.|Query end date, which cannot be earlier than the query start date. Format: YYYY-MM-DD’T’HH:mmZ, for example, 2011-06-11 T16:00Z.|
|DBName|String|No|Name of a database.|
|PageSize|Integer|No|Number of records on every page. Values: 30, 50, and 100; default value: 30.|
|PageNumber|Integer|No|Page number, which must be greater than 0, but must not exceed the maximum Integer value. Default value: 1.|

## Response parameters {#section_a5x_zlh_12b .section}

|Name|Type|Description|
|----|----|-----------|
|<Common response parameters\>| |Fore more information, see [Public parameters](intl.en-US/API Reference/Use APIs/Public parameters.md#).|
|Engine|String|Database type.|
|TotalRecordCount|Integer|Total number of records.|
|PageNumber|Integer|Page number.|
|PageRecordCount|Integer|Number of SQL statements displayed on the current page.|
|Items| ```
List<SQLSlowRecord>
```

 | |

## SQLSlowLog parameters {#section_vgj_vc3_12b .section}

|Name|Type|Description|
|----|----|-----------|
|HostAddress|String|Host address used for database connection.|
|DBName|String|Name of a database.|
|SQLText|String|Query statement.|
|QueryTimes|Long|Execution duration, in the unit of seconds.|
|LockTimes|Long|Lock duration, in the unit of seconds.|
|ParseRowCounts|Long|Number of parsed rows.|
|ReturnRowCounts|Long|Number of returned rows.|
|ExecutionStartTime|String|Execution start time. Format: YYYY-MM-DD’T’HH:mm:ss Z, for example, 2011-06-11 T15:00:08Z.|

## Request example {#section_l4g_pj2_12b .section}

```
https://rds.aliyuncs.com/?Action=DescribeSlowLogRecords
&DBInstanceId=riauvjz6zajfiq6ba1370329449201
&StartTime=2011-06-11T15:00Z
&EndTime=2011-06-11T16:00Z
&<Common request parameters>
```

## Response example {#section_xtg_rj2_12b .section}

**XML format**

```
<DescribeSlowLogRecordsResponse> 
  <RequestId>542BB8D6-4268-45CC-A557-B03EFD7AB30A</RequestId>
  <DBInstanceID>riauvjz6zajfiq6ba1370329449201</DBInstanceID> 
  <Engine>MySQL</Engine>
  <TotalRecordCount>1</TotalRecordCount>
  <PageNumber>1</PageNumber>
  <PageRecordCount>1</PageRecordCount>
  <Items>
    <SQLSlowRecord>
    <HostAddress>192.168.0.123</HostAddress>
    <DBName>test</DBName>
    <SQLText>update test.zxb set id=0 limit 1</SQLText>
    <QueryTimes>123</QueryTimes>
    <LockTimes>12</LockTimes>
    <ParseRowCounts>125</ParseRowCounts>
    <ReturnRowCounts>1</ReturnRowCounts>
    <ExecutionStartTime>2011-06-11T15:00:08Z</ExecutionStartTime>
    </SQLSlowRecord>
  </Items>
</DescribeSlowLogRecordsResponse>
```

**JSON format**

```
{
"RequestId":"542BB8D6-4268-45CC-A557-B03EFD7AB30A"
"Engine":"MySQL",
"PageNumber":1,
"PageRecordCount":1,
"TotalRecordCount":1
"Items":
{"SQLSlowRecord":
[
{
HostAddress:”192.168.0.123”
DBName:”test”
SQLText:” update test.zxb set id=0 limit 1”
QueryTimes:”123”
LockTimes”12”
ParseRowCounts:”125”
ReturnRowCounts:”1”
ExecutionStartTime:”2011-06-11T15:00:08Z”
}
]
}
}
```

