# DescribeErrorLogs {#reference_bsc_qd3_12b .reference}

## 描述 {#section_l21_v32_12b .section}

查看实例某段时间内的错误日志。

## 请求参数 {#section_qzx_w32_12b .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是|系统规定参数，取值：DescribeErrorLogs。|
|DBInstanceId|String|是|实例名。|
|StartTime|String|是|查询开始时间，格式：YYYY-MM-DD’T’HH:mmZ，如2011-05-30T12:10Z。|
|EndTime|String|是|查询结束时间，必须大于查询开始时间 格式：YYYY-MM-DD’T’HH:mmZ，如2011-05-30T20:10Z。|
|PageSize|Integer|否|每页记录数，取值：30/50/100；默认值：30。|
|PageNumber|Integer|否|页码，大于0且不超过Integer的最大值；默认值：1。|

## 返回参数 {#section_a5x_zlh_12b .section}

|名称|类型|描述|
|--|--|--|
|<公共返回参数\>| |详见[公共参数](cn.zh-CN/API参考/使用API/公共参数.md#)。|
|TotalRecordCount|Integer|总记录数。|
|PageNumber|Integer|页码。|
|PageRecordCount|Integer|本页错误日志个数。|
|Items| ```
List<ErrorLogs>
```

 | |

## ErrorLogs参数 {#section_vgj_vc3_12b .section}

|名称|类型|描述|
|--|--|--|
|ErrorInfo|String|错误日志信息。|
|CreateTime|String|生成时间，格式：YYYY-MM-DD’T’HH:mm:ssZ，如2011-05-30 T12:11:4Z。|

## 请求示例 {#section_l4g_pj2_12b .section}

```
https://rds.aliyuncs.com/?Action=DescribeErrorLogs
&DBInstanceId=riauvjz6zajfiq6ba1370329449201
&StartTime=2011-06-11T15:00Z
&EndTime=2011-06-11T20:00Z
&<公共请求参数>
```

## 返回示例 {#section_xtg_rj2_12b .section}

**XML格式**

```
<DescribeErrorLogsResponse> 
  <RequestId>98504E07-BB0E-40FC-B152-E4882615812C</RequestId>
  <TotalRecordCount>1</TotalRecordCount>
  <PageNumber>1</PageNumber>
  <PageRecordCount>1<PageRecordCount>
  <Items>
    <ErrorLog>
    <ErrorInfo>spid52 DBCC TRACEON 3499, server process ID (SPID) 52. This is an informational message only; no user action is required</ErrorInfo>
    <CreateTime>2013-06-04T15:00:00</CreateTime>
    </ErrorLog>
 </Items>
</DescribeErrorLogsResponse>
```

**JSON格式**

```
{
"RequestId":"98504E07-BB0E-40FC-B152-E4882615812C"
"PageNumber":1,
"TotalRecordCount":1,
"PageRecordCount":1
"Items":
{"ErrorLog":
[
{
ErrorInfo:”spid52 DBCC TRACEON 3499, server process ID (SPID) 52. This is an informational message only; no user action is required”
CreateTime:”2013-06-04T15:00:00”
}
]
}
}
```

