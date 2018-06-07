# ModifySecurityIps {#reference_qfq_dmh_12b .reference}

## 描述 {#section_l21_v32_12b .section}

该接口用于修改允许访问实例的IP名单。接口调用必须满足以下条件，否则将失败：

-   实例状态为运行中。
-   实例没有被锁定。

## 请求参数 {#section_qzx_w32_12b .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是|系统规定参数，取值为ModifySecurityIps。|
|DBInstanceId|String|是|实例名。|
|SecurityIps|String|否|IP白名单分组下的IP列表，最多1000个以逗号隔开，格式如下：-   0.0.0.0/0，10.23.12.24（IP）；
-   10.23.12.24/24（CIDR模式，无类域间路由，/24表示了地址中前缀的长度，范围\[1,32\]）。

|
|DBInstanceIPArrayName|String|否|IP白名单分组的名字，如果不传默认操作“Default”分组。备注：1个实例最多支持50个白名单分组。|
|DBInstanceIPArrayAttribute|String|否|默认为空。用于区分不同的属性值，控制台不显示带有“hidden”标签的分组。|
|ModifyMode|String|否|修改方式，取值如下：-   Cover：默认值，覆盖原白名单。
-   Append：追加白名单
-   Delete：删除该白名单

|

## 返回参数 {#section_a5x_zlh_12b .section}

|名称|类型|描述|
|--|--|--|
|RequestId|String|详见[公共参数](cn.zh-CN/API参考/使用API/公共参数.md#)。|
|TaskId|String|任务ID。|

## 请求示例 {#section_l4g_pj2_12b .section}

```
https://rds.aliyuncs.com/?Action=ModifySecurityIps
&DBInstanceId=rdsaiiabnaiiabn
&SecurityIps=192.168.1.2
&<公共请求参数>
```

## 返回示例 {#section_xtg_rj2_12b .section}

**XML格式**

```
<ModifySecurityIpsResponse>
         <RequestId>65BDA532-28AF-4122-AA39-B382721EEE64</RequestId>
</ModifySecurityIpsResponse>
```

**JSON格式**

```
{
    "RequestId": " 65BDA532-28AF-4122-AA39-B382721EEE64"
}
```

