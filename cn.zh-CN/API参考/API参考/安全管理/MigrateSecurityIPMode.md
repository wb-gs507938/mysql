# MigrateSecurityIPMode {#concept_wpm_djj_w2b .concept}

把白名单从通用模式切换为高安全模式。

**说明：** 高安全模式无法切换为通用模式。

-   在通用模式下，白名单中的IP地址不区分经典网络和VPC网络。有安全风险，建议切换为高安全模式。
-   在高安全模式下，白名单中的IP地址分为两类：经典网络的IP地址和VPC的IP地址。

## 请求参数 {#section_qzx_w32_12b .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是|系统规定参数，取值为MigrateSecurityIPMode。|
|DBInstanceId|String|是|实例ID。|

## 返回参数 {#section_a5x_zlh_12b .section}

|名称|类型|描述|
|--|--|--|
|<公共返回参数\>|-|详见[公共参数](cn.zh-CN/API参考/使用API/公共参数.md#)。|
|RequestId|String|请求ID。|
|DBInstanceId|String|实例ID。|
|SecurityIPMode|String|白名单模式。参数值如下：-   **normal**：通用模式
-   **safety**：高安全模式

|

