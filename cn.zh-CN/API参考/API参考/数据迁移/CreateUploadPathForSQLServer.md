# CreateUploadPathForSQLServer {#reference_t52_1bm_12b .reference}

## 描述 {#section_l21_v32_12b .section}

**说明：** 该接口只适用于SQL Server类型的实例。

创建文件服务器的账号、密码以及上传文件的路径信息。用户根据此信息，可上传数据文件，待上传完成，调用导入数据接口，进行外部数据迁移操作。限制条件如下：

-   实例的状态：使用中。

-   数据库的状态：使用中。

-   一个数据库一天只能创建20个文件名，按24小时为一天计算，如上一次创建时间点为2012-03-15 18:30:12，则下次创建时间点大于2012-03-16 18:30:12。


## 请求参数 {#section_qzx_w32_12b .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是|系统规定参数，取值：CreateUploadPathForSQLServer。|
|DBInstanceId|String|是|实例名。|
|DBName|String|是|数据库名。|

## 返回参数 {#section_a5x_zlh_12b .section}

|名称|类型|描述|
|--|--|--|
|<公共返回参数\>| |详见[公共参数](cn.zh-CN/API参考/使用API/公共参数.md#)。|
|InternetFtpServer|String|外网文件服务器。|
|InternetPort|Integer|外网文件服务器端口。|
|IntranetFtpServer|String|内网服务器地址。|
|IntranetPort|Integer|内网服务器端口。|
|UserName|String|文件服务器账号。|
|Password|String|文件服务器账号密码。|
|FileName|String|文件名，带扩展名。|

## 请求示例 {#section_l4g_pj2_12b .section}

```
https://rds.aliyuncs.com/?Action= CreateUploadPathForSQLServer
&DBInstanceId=rianeurbfaeuq2u2a1370572118496
&DBName=testdb01
&<公共请求参数>
```

## 返回示例 {#section_xtg_rj2_12b .section}

**XML格式**

```
<CreateUploadPathForSQLServerResponse>
       <RequestId>66816822-CEC1-4C8D-AB26-2530A7D4DCA5</RequestId>
       <InternetFtpServer>10.230.239.1</InternetFtpServer>
       <InternetPort>3021</InternetPort>
       <IntranetFtpServer></IntranetFtpServer>
       <IntranetPort></IntranetPort>
       <UserName>MKEakJbyG</UserName>
       <Password>aT2Y_XN1GGnOLzm</Password>
       <FileName>testdb01_1370572475975.bak</FileName>
</CreateUploadPathForSQLServerResponse>
```

**JSON格式**

```
{
       "RequestId":"66816822-CEC1-4C8D-AB26-2530A7D4DCA5"
       "InternetFtpServer ":"10.230.239.1"
       "InternetPort":3021
       "IntranetFtpServer":""
       "IntranetPort":
       "UserName":"MKEakJbyG"
       "Password":"aT2Y_XN1GGnOLzm"
       "FileName":"testdb01_1370572475975.bak"
}
```

