# ModifyDBInstanceConnectionString {#reference_hbm_h13_12b .reference}

## 描述 {#section_l21_v32_12b .section}

该接口用于修改连接串的名字和端口。目前RDS提供内外网两种连接串，同时也支持特定访问模式下的连接串并存。

## 请求参数 {#section_qzx_w32_12b .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是|系统规定参数，取值位ModifyDBInstanceConnectionString。|
|DBInstanceId|String|是|实例名。|
|CurrentConnectionString|String|是|实例当前的某个连接串。|
|ConnectionStringPrefix|String|否|目标连接串。|
|Port|String|否|目标端口。|

## 返回参数 {#section_a5x_zlh_12b .section}

|名称|类型|描述|
|<公共返回参数\>|-|详见[公共参数](cn.zh-CN/API参考/使用API/公共参数.md#)。|

