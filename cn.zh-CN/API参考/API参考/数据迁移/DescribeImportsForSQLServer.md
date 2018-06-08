# DescribeImportsForSQLServer {#reference_ujt_12m_12b .reference}

## 描述 {#section_l21_v32_12b .section}

查看SQL Server数据库导入列表，查看导入任务情况，判断导入任务是否完成。

## 请求参数 {#section_qzx_w32_12b .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是|系统规定参数，取值：DescribeImportsForSQLServer。|
|DBInstanceId|String|是|实例名。|
|ImportId|Integer|否|迁移结果ID。|
|StartTime|String|是|查询开始时间，格式如：2011-06-11T15:00Z。|
|EndTime|String|是|查询结束时间，格式如：2011-06-11T16:00Z，且大于查询开始时间。|
|PageSize|Integer|否|每页记录数，取值：30/50/100，默认值：30。|
|PageNumber|Integer|否|页码，大于0且不超过Integer的最大值，默认值：1。|

## 返回参数 {#section_a5x_zlh_12b .section}

|名称|类型|描述|
|--|--|--|
|TotalRecordCount|Integer|总记录数。|
|PageNumber|Integer|页码。|
|PageRecordCount|Integer|本页SQL语句个数。|
|Items| ```
List<SQLServerImport>
```

 |无|

## SQLServerImport参数 {#section_z52_f2m_12b .section}

|名称|类型|描述|
|--|--|--|
|ImportId|Integer|迁移ID。|
|FileName|String|文件名。|
|DBName|String|导入的数据库名。|
|ImportStatus|Integer|导入状态，取值如下：-   Pending：未开始
-   Importing：导入中
-   Success：导入成功
-   Failed：导入失败
-   Cancelled：任务取消
-   Cancelling：迁移取消中

|
|StartTime|String|导入时间。格式：YYYY-MM-DD’T’HH:mm:ssZ，如2011-05-30 T12:11:40Z。|

## 请求示例 {#section_l4g_pj2_12b .section}

```
https://rds.aliyuncs.com/?Action=DescribeImportsForSQLServer
&DBInstanceId=rianeurbfaeuq2u2a1370572118496
&StartTime=2014-06-11T15:00Z
&EndTime=2014-06-11T16:00Z
&<公共请求参数>
```

## 返回示例 {#section_xtg_rj2_12b .section}

**XML格式**

```
<DescribeImportsForSQLServerResponse> 
  <RequestId>08A3B71B-FE08-4B03-974F-CC7EA6DB1828</RequestId>
<TotalRecordCount>1</TotalRecordCount>
<PageNumber>1</PageNumber>
<PageRecordCount>1<PageRecordCount>
<Items>
<SQLServerImport>
<DBName>testdb01</DBName>
<FileName>testdb01_1370572475975.bak</FileName>
<ImportStatus>Success</ImportStatus>
<StartTime>2014-06-11T15:11:40Z</StartTime>
</SQLServerImport>
</Items>
</DescribeImportsForSQLServerResponse>
```

**JSON格式**

```
{
"PageNumber":1,
"TotalRecordCount":1,
"PageRecordCount":1
"Items":
{"SQLServerImport":
[
{
"DBName":"testdb01"
"FileName":"testdb01_1370572475975.bak"
"ImportStatus":"Success"
"StartTime": "Innodb"
}
]
},
"RequestId": "08A3B71B-FE08-4B03-974F-CC7EA6DB1828"
}
```

