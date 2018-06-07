# GrantAccountPrivilege {#reference_x1w_rzg_12b .reference}

## 描述 {#section_l21_v32_12b .section}

该接口用于授权账号访问某个数据库，一个账号可关联一个或多个数据库。如果指定的账号对指定数据库已经具有访问权限，则会直接返回成功。

**说明：** 实例状态要求为运行中。

## 请求参数 {#section_qzx_w32_12b .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是|系统规定参数，取值为GrantAccountPrivilege。|
|DBInstanceId|String|是|实例名。|
|AccountName|String|是|账号名。|
|DBName|String|是|设置与该账号关联的数据库名称。|
|AccountPrivilege|String|是|账号权限：-   ReadOnly：只读
-   ReadWrite：读写

|

## 返回参数 {#section_rpk_z32_12b .section}

|名称|类型|描述|
|--|--|--|
|<公共返回参数\>| |详见[公共参数](cn.zh-CN/API参考/使用API/公共参数.md#)。|

## 请求示例 {#section_l4g_pj2_12b .section}

```
https://rds.aliyuncs.com/?Action=GrantAccountPrivilege
&AccountName=testacc02
&AccountPrivilege=ReadWrite
&DBName=testdb03
&DBInstanceId=riauvjz6zajfiq6ba1370329449201
&<公共请求参数>
```

## 返回示例 {#section_xtg_rj2_12b .section}

**XML格式**

```
<GrantAccountPrivilegeResponse>
         <RequestId>81BC9559-7B22-4B7F-B705-5F56DEECDEA7</RequestId>
</GrantAccountPrivilegeResponse>
```

**JSON格式**

```
{
         "RequestId":"81BC9559-7B22-4B7F-B705-5F56DEECDEA7"
}
```

