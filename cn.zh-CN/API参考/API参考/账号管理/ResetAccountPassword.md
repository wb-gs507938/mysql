# ResetAccountPassword {#reference_ydw_z1h_12b .reference}

## 描述 {#section_l21_v32_12b .section}

该接口用于重置账号密码。必须满足以下条件，否则将操作失败：

-   当前实例状态：运行中。
-   没有被锁定。

## 请求参数 {#section_qzx_w32_12b .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是|系统规定参数，取值为ResetAccountPassword。|
|DBInstanceId|String|是|实例名。|
|AccountName|String|是|账号名。|
|AccountPassword|String|是|新密码，由字母、数字或下划线组成，长度为6~32位。|

## 返回参数 {#section_rpk_z32_12b .section}

|名称|类型|描述|
|--|--|--|
|<公共返回参数\>| |详见[公共参数](cn.zh-CN/API参考/使用API/公共参数.md#)。|

## 请求示例 {#section_l4g_pj2_12b .section}

```
https://rds.aliyuncs.com/?Action=ResetAccountPassword
&AccountName=testacc02
&AccountPassword=newpw1234
&DBInstanceId=riauvjz6zajfiq6ba1370329449201
&<公共请求参数>
```

## 返回示例 {#section_xtg_rj2_12b .section}

**XML格式**

```
<ResetAccountPasswordResponse>
         <RequestId>D4D4BE8A-DD46-440A-BFCD-EE31DA81C9DD</RequestId>
</ResetAccountPasswordResponse>
```

**JSON格式**

```
{
         "RequestId":"D4D4BE8A-DD46-440A-BFCD-EE31DA81C9DD"
}
```

