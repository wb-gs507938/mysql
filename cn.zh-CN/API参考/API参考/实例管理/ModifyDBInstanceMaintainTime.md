# ModifyDBInstanceMaintainTime {#reference_f5b_pbf_12b .reference}

## 描述 {#section_ops_ghv_12b .section}

该接口用于修改实例可例行维护的时间，一般设置为业务的低峰时间段。阿里云会在您设置的可维护时间段内进行实例维护，保证对业务的影响降到最低。

## 请求参数 {#section_mpn_hhv_12b .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是|系统规定参数，取值为ModifyDBInstanceMaintainTime。|
|DBInstanceId|String|是|实例名。|
|MaintainTime|String|是|实例的维护时间，取值范围如下：-   22:00Z-02:00Z :22点至凌晨2点
-   02:00Z-06:00Z:凌晨2点至6点
-   06:00-10:00：6点至10点
-   10:00Z14:00Z：10点至14点
-   14:00Z-18:00Z：14点至18点
-   18:00Z-22:00Z：18点至22点

|

## 返回参数 {#section_pbd_qhv_12b .section}

|名称|类型|描述|
|--|--|--|
|<公共返回参数\>|-|详见[公共参数](cn.zh-CN/API参考/使用API/公共参数.md#)。|

## 请求示例 {#section_qwj_rhv_12b .section}

```
https://rds.aliyuncs.com/?Action=ModifyDBInstanceMaintainTime
&DBInstanceId=rdsaiiabnaiiabn
&MaintainTime=22:00Z-02:00Z
&<公共请求参数>
```

## 返回示例 {#section_umq_shv_12b .section}

**XML格式**

```
<ModifyDBInstanceMaintainTimeResponse>
         <RequestId>65BDA532-28AF-4122-AA39-B382721EEE64</RequestId>
</ModifyDBInstanceMaintainTimeResponse>
```

**JSON格式**

```
{
    "RequestId": " 65BDA532-28AF-4122-AA39-B382721EEE64"
  }
```

