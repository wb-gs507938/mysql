# SwitchDBInstanceHA {#reference_t4n_qcf_12b .reference}

## 描述 {#section_l21_v32_12b .section}

RDS主实例是由分布在不同服务器上的主库和备库组成的，该接口用于切换实例的主备库，由新的主库来承担业务流量。

## 请求参数 {#section_qzx_w32_12b .section}

|名称|类型|是否必须|描述|
|Action|String|是|系统规定参数，取值为SwitchDBInstanceHA。|
|DBInstanceId|String|是|实例名。|
|NodeId|String|是|节点的唯一标识，从[DescribeDBInstanceHAConfig](cn.zh-CN/API参考/API参考/实例管理/DescribeDBInstanceHAConfig.md#)接口可查询该值。|
|Force|String|否| -   Yes：强制
-   No：非强制，默认为非强制

 |

## 返回参数 {#section_rpk_z32_12b .section}

|名称|类型|描述|
|--|--|--|
|<公共返回参数\>|-|详见[公共参数](cn.zh-CN/API参考/使用API/公共参数.md#)。|

