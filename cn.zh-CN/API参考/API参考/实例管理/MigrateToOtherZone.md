# MigrateToOtherZone {#reference_t5m_dd2_12b .reference}

## 描述 {#section_l21_v32_12b .section}

该接口用于将实例迁移至其他可用区。例如，实例1目前位于华东 1 \(杭州\) 的cn-hangzhou-a的可用区，调用此接口可以将该实例迁移至杭州的cn-hangzhou-b。

**说明：** 

跨可用区迁移必须迁移至相同物理位置内的，如华东 1 \(杭州\) 可用区内的实例不支持迁移至华北 1 \(青岛\) 的可用区。

## 请求参数 {#section_qzx_w32_12b .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是|系统规定参数，取值为MigrateToOtherZone。|
|DBInstanceId|String|是|实例名。|
|ZoneId|String|是|通过函数DescribeRegions查看可用的可用区。|

## 返回参数 {#section_rpk_z32_12b .section}

|名称|类型|描述|
|--|--|--|
|<公共返回参数\>|-|详见[公共参数](cn.zh-CN/API参考/使用API/公共参数.md#)。|

## 请求示例 {#section_l4g_pj2_12b .section}

```
https://rds.aliyuncs.com/?Action=MigrateToOtherZone
&DBInstanceId=rdsaiiabnaiiabn
&ZoneId=cn-hangzhou-b
&<公共请求参数>
```

## 返回示例 {#section_xtg_rj2_12b .section}

**XML格式**

```
<MigrateToOtherZoneResponse>
         <RequestId>65BDA532-28AF-4122-AA39-B382721EEE64</RequestId>
</MigrateToOtherZoneResponse>
```

**JSON格式**

```
{
    "RequestId": " 65BDA532-28AF-4122-AA39-B382721EEE64"
}
```

