# DescribeSlowLogs {#reference_i4z_lc3_12b .reference}

## 描述 {#section_l21_v32_12b .section}

用户可以查询某日期范围内、某个用户实例下、某个DB的慢查询汇总情况，支持分页查询。对于SQL Server和MySQL两种实例类型，慢查询返回的SQLSlowLog参数值是不一样的，详情请见下面的SQLSlowLog参数表。

## 请求参数 {#section_qzx_w32_12b .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是|系统规定参数，取值：DescribeSlowLogs。|
|DBInstanceId|String|是|实例名。|
|StartTime|String|是|查询开始日期，格式：YYYY-MM-DDZ，如2011-05-30Z。|
|EndTime|String|是|查询结束日期，不能小于查询开始日期，格式：YYYY-MM-DDZ，如2011-05-30Z。|
|DBName|String|否|DB名称。|
|SortKey|String|否|排序依据，取值如下：-   TotalExecutionCounts：总执行次数最多；
-   TotalQueryTimes：总执行时间最多
-   TotalLogicalReads：总逻辑读最多；
-   TotalPhysicalReads：总物理读最多。此参数对SQL Server实例有效，SQL Server类型必传此参数。

|
|PageSize|Integer|否|每页记录数，取值：30/50/100；默认值：30。|
|PageNumber|Integer|否|页码，大于0且不超过Integer的最大值；默认值：1。|

## 返回参数 {#section_a5x_zlh_12b .section}

|名称|类型|描述|
|--|--|--|
|<公共返回参数\>| |详见[公共参数](cn.zh-CN/API参考/使用API/公共参数.md#)。|
|Engine|String|数据库类型。|
|StartTime|String|查询开始日期，格式：YYYY-MM-DDZ，如2011-05-30Z。|
|EndTime|String|查询结束日期，格式：YYYY-MM-DDZ，如2011-05-30Z。|
|TotalRecordCount|Integer|总记录数。|
|PageNumber|Integer|页码。|
|PageRecordCount|Integer|本页SQL语句个数。|
|Items| ```
List<SQLSlowLog>
```

 | |

## SQLSlowLog参数 {#section_vgj_vc3_12b .section}

|名称|类型|描述|
|--|--|--|
|DBName|String|DB名称。|
|SQLText|String|查询语句。|
|MySQLTotalExecutionCounts|Long|执行总次数。|
|MySQLTotalExecutionTimes|Long|执行总时长，单位：秒。|
|MaxExecutionTime|Long|执行最大时长，单位：秒。|
|TotalLockTimes|Long|锁定总时长，单位：秒。|
|MaxLockTime|Long|锁定最大时长，单位：秒。|
|ParseTotalRowCounts|Long|解析总行数。|
|ParseMaxRowCount|Long|解析最大行数。|
|ReturnTotalRowCounts|Long|返回总行数。|
|ReturnMaxRowCount|Long|返回最大行数。|
|CreateTime|String|数据生成日期，格式：”yyyy-MM-ddZ”，如2011-05-30Z。|

## SQLSlowLog参数 {#section_xkq_xc3_12b .section}

|称|类型|描述|
|--|--|--|
|SQLText|String|查询语句。|
|SQLServerTotalExecutionCounts|Long|总执行次数。|
|SQLServerTotalExecutionTimes|Long|总执行时间，单位：毫秒。|
|TotalLogicalReadcounts|Long|总逻辑读。|
|TotalPhysicalReadcounts|Long|总物理读。|
|ReportTime|String|数据报表生成日期；格式：”yyyy-MM-ddZ”，如2011-05-30Z。|

## 请求示例 {#section_l4g_pj2_12b .section}

```
https://rds.aliyuncs.com/?Action=DescribeSlowLogs
&DBInstanceId=riauvjz6zajfiq6ba1370329449201
&StartTime=2011-06-11Z
&EndTime=2011-12-11Z
&SortKey= TotalExecutionCounts
&<公共请求参数>
```

## 返回示例 {#section_xtg_rj2_12b .section}

**XML格式**

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

**JSON格式**

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

