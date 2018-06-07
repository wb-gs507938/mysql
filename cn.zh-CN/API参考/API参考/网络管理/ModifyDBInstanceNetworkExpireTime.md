# ModifyDBInstanceNetworkExpireTime {#reference_iy5_n13_12b .reference}

## 描述 {#section_l21_v32_12b .section}

当实例在混访模式下（同时包含VPC和经典网络两种网络类型的实例），该接口用于修改经典网络使用期限。

## 请求参数 {#section_qzx_w32_12b .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是|系统规定参数，取值为ModifyDBInstanceNetworkExpireTime。|
|DBInstanceId|String|是|实例ID。|
|ConnectionString|String|是|要延期的经典网络连接串，经典网络字符串有两种：-   当前实例的经典网络字符串
-   读写分离的经典网络字符串

|
|ClassicExpiredDays|Integer|是|经典网络字符串保留天数\[1-120\]。|

## 返回参数 {#section_a5x_zlh_12b .section}

|名称|类型|描述|
|<公共返回参数\>|-|详见[公共参数](cn.zh-CN/API参考/使用API/公共参数.md#)。|

