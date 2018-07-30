# RestartDBInstance {#reference_glw_r32_12b .reference}

## 描述 {#section_l21_v32_12b .section}

该接口用于重启实例，重启一般在10S钟内完成。如果有大量的事务需要提交或回滚，可能会延长1分钟左右。重启实例必须满足以下条件，否则将操作失败：

-   实例使用中
-   实例没有进行中的备份

## 请求参数 {#section_qzx_w32_12b .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是|系统规定参数，取值：RestartDBInstance。|
|DBInstanceId|String|是|实例ID。|
|ClientToken|String|否|用于保证幂等性。|
|UpgradeKernelVersion|String|否|设置实例是否自动升级小版本，默认为否。|

## 返回参数 {#section_rpk_z32_12b .section}

|名称|类型|描述|
|--|--|--|
|<公共返回参数\>|-|详见[公共参数](intl.zh-CN/API参考/使用API/公共参数.md#)。|

## 请求示例 {#section_l4g_pj2_12b .section}

```
https://rds.aliyuncs.com/?Action=RestartDBInstance
&DBInstanceId=rdsaiiabnaiiabn
&<公共请求参数>
```

## 返回示例 {#section_xtg_rj2_12b .section}

**XML格式**

```
<RestartDBInstanceResponse>
         <RequestId>65BDA532-28AF-4122-AA39-B382721EEE64</RequestId>
</RestartDBInstanceResponse>
```

**JSON格式**

```
{
    "RequestId": " 65BDA532-28AF-4122-AA39-B382721EEE64"
}
```

