# DescribeSQLLogRecords {#reference_n4g_1f3_12b .reference}

## 描述 {#section_l21_v32_12b .section}

查询实例的SQL审计日志。

## 请求参数 {#section_qzx_w32_12b .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是|系统规定参数，取值：DescribeSQLLogRecords。|
|DBInstanceId|String|是|实例名。|
|Database|String|否|默认为所有。|
|User|String|否|默认为所有。|
|Form|String|否|File，触发审计日志文件的生成，若传入这个值，则只返回公共参数，需再调用[DescribeSQLLogFiles](cn.zh-CN/API参考/API参考/日志管理/DescribeSQLLogFiles.md#)接口获取文件的最终下载地址；Stream，返回数据流。默认为Stream。|
|QueryKeywords|String|否|关键字查询，多个关键字以空格分隔，不超过10个关键字。|
|StartTime|String|是|查询开始时间，格式如：yyyy-MM-dd’T’HH:mm:ssZ。|
|EndTime|String|是|查询结束时间，格式如：yyyy-MM-dd’T’HH:mm:ssZ，且大于查询开始时间。|
|PageSize|Integer|否|每页记录数，取值：30/50/100；默认值：30。|
|PageNumber|Integer|否|页码，大于0且不超过Integer的最大值；默认值：1。|

## 返回参数 {#section_a5x_zlh_12b .section}

|名称|类型|描述|
|--|--|--|
|<公共返回参数\>| |详见[公共参数](cn.zh-CN/API参考/使用API/公共参数.md#)。|
|TotalRecordCount|Integer|总记录数。|
|PageNumber|Integer|页码。|
|PageRecordCount|Integer|本页SQL日志明细个数。|
|Items| ```
List<SQLRecord>
```

 |无|

## SQLRecord参数 { .section}

|名称|类型|描述|
|--|--|--|
|DBName|String|数据库。|
|AccountName|String|账号名。|
|HostAddress|String|客户端IP地址。|
|SQLText|String|SQL语句。|
|TotalExecutionTimes|Long|消耗时间，单位：微秒。|
|ReturnRowCounts|Long|返回记录数。|
|ThreadID|String|线程ID。|
|ExecuteTime|String|执行时间;格式：yyyy-MM-dd’T’HH:mm:ssZ，如2011-05-30 T12:11:20Z。|

## 请求示例 {#section_l4g_pj2_12b .section}

```
https://rds.aliyuncs.com/?Action=DescribeSQLLogRecords
&DBInstanceId=riauvjz6zajfiq6ba1370329449201
&StartTime=2011-06-11T15:00:00Z
&EndTime=2013-06-05T15:00:00Z
&<公共请求参数>
```

## 返回示例 {#section_xtg_rj2_12b .section}

**XML格式**

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

**JSON格式**

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

