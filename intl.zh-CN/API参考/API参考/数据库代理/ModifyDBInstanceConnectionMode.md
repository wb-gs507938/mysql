# ModifyDBInstanceConnectionMode {#reference_pyz_mm2_12b .reference}

## 描述 {#section_l21_v32_12b .section}

该接口用于变更实例连接模式，目前RDS提供两种访问模式：

-   标准访问模式；
-   高安全访问模式。

## 请求参数 {#section_qzx_w32_12b .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是|系统规定参数，取值为ModifyDBInstanceConnectionMode。|
|DBInstanceId|String|是|实例ID。|
|ConnectionMode|String|是|设置实例的访问模式：-   Standard：标准访问模式；
-   Safe：高安全访问模式。

|

## 返回参数 {#section_rpk_z32_12b .section}

|名称|类型|描述|
|<公共返回参数\>|-|详见[公共参数](intl.zh-CN/API参考/使用API/公共参数.md#)。|

