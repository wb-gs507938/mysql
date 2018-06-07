# AllocateInstancePublicConnection {#reference_iph_pyh_12b .reference}

## 描述 {#section_l21_v32_12b .section}

该接口用于申请实例的外网连接串。

## 请求参数 {#section_qzx_w32_12b .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是|系统规定参数，取值为AllocateInstancePublicConnection。|
|DBInstanceId|String|是|实例名。|
|ConnectionStringPrefix|String|是|外网连接串的前缀。可以在RDS控制台的基本信息栏找到，即外网地址。|
|Port|String|是|外网端口。|

## 返回参数 {#section_a5x_zlh_12b .section}

|参数|类型|说明|
|--|--|--|
|<公共返回参数\>|-|详见[公共参数](cn.zh-CN/API参考/使用API/公共参数.md#)。|

## 请求示例 {#section_l4g_pj2_12b .section}

```
https://rds.aliyuncs.com/?Action=AllocateInstancePublicConnection
&DBInstanceId=rdsaiiabnaiiabn
&<公共请求参数>
```

## 返回示例 {#section_xtg_rj2_12b .section}

**XML格式**

```
<PurgeDBInstanceLogResponse>
         <RequestId>65BDA532-28AF-4122-AA39-B382721EEE64</RequestId>
</PurgeDBInstanceLogResponse>
```

**JSON格式**

```
{
    "RequestId": " 65BDA532-28AF-4122-AA39-B382721EEE64"
}
```

