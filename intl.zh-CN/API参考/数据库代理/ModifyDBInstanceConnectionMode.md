# ModifyDBInstanceConnectionMode {#reference_pyz_mm2_12b .reference}

## 描述 {#section_l21_v32_12b .section}

该接口用于开启或关闭数据库代理功能。

**说明：** 仅适用于RDS for MySQL实例。

## 请求参数 {#section_qzx_w32_12b .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是|系统规定参数，取值为ModifyDBInstanceConnectionMode。|
|DBInstanceId|String|是|实例ID。|
|ConnectionMode|String|是|设置数据库代理功能的状态：-   Performance：关闭数据库代理功能；
-   Safe：开启数据库代理功能。

|

## 返回参数 {#section_rpk_z32_12b .section}

|名称|类型|描述|
|--|--|--|
|<公共返回参数\>|-|详见[公共参数](intl.zh-CN/API参考/使用API/公共参数.md#)。|

