# RevokeAccountPrivilege {#reference_ssc_g1h_12b .reference}

## 描述 {#section_l21_v32_12b .section}

该接口用于删除账号对数据库的访问权限。实例必须满足以下条件，否则操作将失败：

-   实例状态为运行中。
-   数据库状态为运行中。

**说明：** 具体收回的权限包括 SELECT，INSERT，UPDATE，DELETE，CREATE，DROP，REFERENCES，INDEX，ALTER，CREATE TEMPORARY TABLES，LOCK TABLES，EXECUTE，CREATE VIEW，SHOW VIEW，CREATE ROUTINE ，ALTER ROUTINE，EVENT，TRIGGER。

## 请求参数 {#section_qzx_w32_12b .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是|系统规定参数，取值为RevokeAccountPrivilege。|
|DBInstanceId|String|是|实例ID。|
|AccountName|String|是|账号名。|
|DBName|String|是|数据库名。|

## 返回参数 {#section_rpk_z32_12b .section}

|名称|类型|描述|
|--|--|--|
|<公共返回参数\>| |详见[公共参数](cn.zh-CN/API参考/使用API/公共参数.md#)。|

## 请求示例 {#section_l4g_pj2_12b .section}

```
https://rds.aliyuncs.com/?Action=RevokeAccountPrivilege
        &AccountName=testacc02
        &DBName=testdb03
        &DBInstanceId=riauvjz6zajfiq6ba1370329449201
        &<公共请求参数>
```

## 返回示例 {#section_xtg_rj2_12b .section}

**XML格式**

```
<RevokeAccountPrivilegeResponse>
        <RequestId>E22099CA-A61E-4992-A0B7-CE82DC175626</RequestId>
        </RevokeAccountPrivilegeResponse>
```

**JSON格式**

```
{
        "RequestId":"E22099CA-A61E-4992-A0B7-CE82DC175626"
        }
```

