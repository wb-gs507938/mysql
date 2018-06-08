# ModifyDBInstanceNetworkType {#reference_p24_w13_12b .reference}

## 描述 {#section_l21_v32_12b .section}

该接口用于将实例的网络类型从VPC切换成经典网络，或从经典网络切换成VPC。

**说明：** 对于网络类型为经典网络的实例，只有ConnectionMode为**Safty**时才能将网络类型切换成VPC。

## 请求参数 {#section_qzx_w32_12b .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是|系统规定参数，取值为ModifyDBInstanceNetworkType。|
|DBInstanceId|String|是|实例名。|
|InstanceNetworkType|String|是| -   VPC：返回VPC实例
-   Classic：返回Classic实例

 |
|VPCId|String|否|VPC ID。|
|VSwitchId|String|否|VSwitch ID；若传入VPCId的值，则该参数必传。|
|PrivateIpAddress|String|否|您可以指定VSwitchId下的VPC IP。如果不输入，系统通过VPCId和VSwitchId自动分配。|
|ReadWriteSplittingPrivateIpAddres|String|否| -   若当前实例存在内网读写分离地址，则读写分离地址的网络类型也会一同变更。
-   当切换为VPC网络时，您可以指定在VSwitchId下当前实例的读写分离链路的VPC IP。
-   如果不输入，系统通过VPCId和VSwitchId自动分配。

 |

## 返回参数 {#section_a5x_zlh_12b .section}

|名称|类型|描述|
|--|--|--|
|<公共返回参数\>|-|详见[公共参数](cn.zh-CN/API参考/使用API/公共参数.md#)。|

