# DescribeSQLLogFiles {#reference_j2q_fg3_12b .reference}

## 描述 {#section_l21_v32_12b .section}

查询SQL审计文件列表。

## 请求参数 {#section_qzx_w32_12b .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是|系统规定参数，取值：DescribeSQLLogFiles。|
|DBInstanceId|String|是|实例名。|

## 返回参数 {#section_a5x_zlh_12b .section}

|名称|类型|描述|
|--|--|--|
|<公共返回参数\>| |详见[公共参数](cn.zh-CN/API参考/使用API/公共参数.md#)。|
|TotalRecordCount|Interger|总记录数。|
|PageNumber|Interger|页码。|
|PageRecordCount|Interger|本页记录数。|
|Items| ```
List<LogFile>
```

 |由审计文件组成的数组。|

## LogFile参数 { .section}

|名称|类型|描述|
|--|--|--|
|FileID|Interger|文件ID。|
|DBInstanceId|String|实例名。|
|LogStatus|String|Success：归档完成；Failed：归档失败；Generating归档中。|
|LogStartTime|String|SQL起始时间。|
|LogEndTime|String|SQL结束时间。|
|LogDownloadURL|String|下载链接的地址。若当前不可下载，则为空串。|
|LogSize|Long|日志文件大小，单位：Byte。|

