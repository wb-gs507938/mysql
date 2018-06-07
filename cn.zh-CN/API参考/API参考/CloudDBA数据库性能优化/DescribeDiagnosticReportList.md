# DescribeDiagnosticReportList {#reference_gw3_dgf_12b .reference}

## 描述 {#section_l21_v32_12b .section}

获取诊断报告列表，返回带有诊断报告的数据采集时间、生成时间和下载地址，诊断报告可保留15天。

## 请求参数 {#section_qzx_w32_12b .section}

|参数|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeDiagnosticReportList|系统规定参数。取值：DescribeDiagnosticReportList|
|DBInstanceId|String|是|rm-bp1842vmucoa5w874|实例的名称。|
|AccessKeyId|String|否|LTAIKw8gqPc3FvOw|阿里云颁发给用户的访问服务所用的密钥ID。|

## 返回参数 {#section_rpk_z32_12b .section}

|参数|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|1AD222E9-E606-4A42-BF6D-8A4442913CEF|请求ID。|
|ReportList| | |报告列表。|
|  └DiagnosticTime|String|2018-01-17T12:46:09Z|诊断报告的生成时间。|
|  └Score|Integer|100|诊断分数（当前不显示）。|
|  └StartTime|String|2012-06-11T15:00Z|监控数据的起始时间，格式示例为`2012-06-11T15:00Z`。|
|  └EndTime|String|2012-06-11T15:00Z|监控数据的结束时间，格式示例为`2012-06-11T15:00Z`。|
|  └DownloadURL|String| ```
http://rdsreport-hzi-v2.oss-cn-hangzhou-i.aliyuncs.com/custins5095533/apsaradba_report_1516193170098.pdf?OSSAccessKeyId=LTAITfQ7krsrEwRn&Expires=1516244278&Signature=hWQMLng%2ByhNjas2q59w1zKBvvzc%3D
```

 |公网的下载地址。若当前不可下载，则为空串。|

## 请求示例 {#section_l4g_pj2_12b .section}

```
https://rds.aliyuncs.com/?Action=DescribeDiagnosticReportList
DBInstanceId=rm-bp1842vmucoa5w874
AccessKeyId=LTAIKw8gqPc3FvOw 
&<公共请求参数>
```

## 返回示例 {#section_xtg_rj2_12b .section}

**正常返回格式：JSON格式**

```
{
    "reportList":[{
        "diagnosticTime":"2018-01-17T12:46:09Z",
        "downloadURL":"http://rdsreport-hzi-v2.oss-cn-hangzhou-i.aliyuncs.com/custins5095533/apsaradba_report_1516193170098.pdf?OSSAccessKeyId=LTAITfQ7krsrEwRn&Expires=1516244278&Signature=hWQMLng%2ByhNjas2q59w1zKBvvzc%3D",
        "endTime":"2018-01-10T15:31:00Z",
        "score":100,
        "startTime":"2018-01-10T15:30:00Z"
    }],
    "requestId":"B7E9A79C-DE1B-4398-845F-D654FC0958BD"
}
```

**异常返回格式：JSON格式**

```
{
    "Code":"UnsupportedOperation",
    "HostId":"rds.aliyuncs.com",
    "Message":"The specified action is not supported.",
    "RequestId":"7463B73D-35CC-4D19-A010-6B8D65D242EF"
}
```

