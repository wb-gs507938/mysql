# DescribeBinlogFiles {#reference_dyp_zd3_12b .reference}

## 描述 {#section_l21_v32_12b .section}

查询实例的BINLOG文件（仅MySQL数据库实例），支持分页。RDS提供Binlog文件下载。

-   当DownloadLink为NULL时，表示RDS没有提供下载链接URL。
-   当DownloadLink不为NULL时，用户可以根据此URL，通过wget（请加双引号）、浏览器、编写程序下载备份文件，此URL已设置过期时间LinkExpiredTime，请在过期时间之前使用。若过期，用户在下载时，将会出现如下错误码：

    ```
    <?xml version="1.0" encoding="UTF-8" ?>
    <Error>
    <Code>AccessDenied</Code>
    <Message>Request has expired.</Message>
    <Expires>2012-12-25T09:47:52.000Z</Expires>
    <ServerTime>2012-12-25T09:49:00.000Z</ServerTime>
    <RequestId>50D9768CA801C2F102005C70</RequestId>
    <HostId>oss-test.aliyun-inc.com</HostId>
    </Error>
    ```


## 请求参数 {#section_qzx_w32_12b .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是|系统规定参数，取值：DescribeBinlogFiles。|
|DBInstanceId|String|是|实例名。|
|StartTime|String|是|查询开始时间，格式：yyyy-MM-dd’T’HH:mm:ssZ。|
|EndTime|String|是|查询结束时间，格式：yyyy-MM-dd’T’HH:mm:ssZ，且大于查询开始时间。|
|PageSize|Integer|否|每页记录数，取值：30/50/100/；默认值：30。|
|PageNumber|Integer|否|页码，大于0且不超过Integer的最大值；默认值：1。|

## 返回参数 {#section_a5x_zlh_12b .section}

|名称|类型|描述|
|--|--|--|
|<公共返回参数\>| |详见[公共参数](intl.zh-CN/API参考/使用API/公共参数.md#)。|
|TotalRecordCount|Integer|Binlog文件总数。|
|PageNumber|Integer|页码。|
|PageRecordCount|Integer|本页BINLOG文件个数。|
|Items|`List<BinLogFile>`| |

## BinLogFile参数 {#section_vgj_vc3_12b .section}

|名称|类型|描述|
|--|--|--|
|FileSize|Long|BINLOG文件大小，单位：Byte。|
|LogBeginTime|String|BINLOG文件记录的开始时间。|
|LogEndTime|String|BINLOG文件记录的结束时间。|
|DownloadLink|String|支持HTTP协议的下载链接URL，NULL表示没有下载链接。|
|HostInstanceID|String|Binlog所在实例编号，用户区分该binlog日志产生于主实例或从实例。|
|LinkExpiredTime|String|URL过期时间，格式如：2011-06-11T15:00:00Z。|

## 请求示例 {#section_l4g_pj2_12b .section}

```
https://rds.aliyuncs.com/?Action=DescribeBinlogFiles
&DBInstanceId=riauvjz6zajfiq6ba1370329449201
&StartTime=2011-06-11T15:00:00Z
&EndTime=2013-06-05T15:00:00Z
&<公共请求参数>
```

## 返回示例 {#section_xtg_rj2_12b .section}

**XML格式**

```
<DescribeBinlogFilesResponse> 
  <RequestId>66816822-CEC1-4C8D-AB26-2530A7D4DCA5</RequestId>
  <TotalRecordCount>1</TotalRecordCount>
  <PageNumber>1</PageNumber>
  <PageRecordCount>1<PageRecordCount>
  <Items>
    <BinLogFile>
    <FileSize>123</FileSize>
    <LogBeginTime>2013-06-01T15:00:00Z</LogBeginTime>
     <LogEndTime>2013-06-02T18:00:00Z</LogEndTime>
     <DownloadLink>http://rdslog-   real.oss.aliyuncs.com/custins47742/hostins46770/mysql-bin.000120.zip?spm=0.0.0.0.eMQKjs&OSSAccessKeyId=c9gzsqpauj3duw5whwdv40hb&Expires=1384916927&Signature=07TMgM3G2Jw4sOO6yN8nWDgBJPA%3D</DownloadLink>
    <LinkExpiredTime>2013-06-09T18:00:00Z</LinkExpiredTime>
   </BinLogFile>
  </Items>
</DescribeBinlogFilesResponse>
```

**JSON格式**

```
{
    "RequestId":"66816822-CEC1-4C8D-AB26-2530A7D4DCA5"
"PageNumber":1,
"TotalRecordCount":1,
"PageRecordCount":1
"Items":
{"BinLogFile":
[
{
FileSize:”123”
LogBeginTime:”2013-06-01T15:00:00Z”
LogEndTime:”2013-06-02T18:00:00Z”
DownloadLink:”http://rdslog-real.oss.aliyuncs.com/custins47742/hostins46770/mysql-bin.000120.zip?spm=0.0.0.0.eMQKjs&OSSAccessKeyId=c9gzsqpauj3duw5whwdv40hb&Expires=1384916927&Signature=07TMgM3G2Jw4sOO6yN8nWDgBJPA%3D”
LinkExpiredTime”2013-06-09T18:00:00Z”
}
]
}
}
```

