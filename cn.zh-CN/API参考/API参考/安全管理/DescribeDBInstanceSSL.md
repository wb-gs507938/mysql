# DescribeDBInstanceSSL {#reference_b4t_3ch_12b .reference}

## 描述 {#section_l21_v32_12b .section}

该接口只支持MySQL 5.5、MySQL 5.6和SQL Server 2008 R2。

## 请求参数 {#section_qzx_w32_12b .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是|系统规定参数，取值为DescribeDBInstanceSSL|
|DBInstanceId|String|是|实例名。|

## 返回参数 {#section_rpk_z32_12b .section}

|名称|类型|描述|
|--|--|--|
|<公共返回参数\>|-|详见[公共参数](cn.zh-CN/API参考/使用API/公共参数.md#)。|
|ConnectionString|String|受SSL保护的连接地址。|
|SSLExpireTime|String|SSL过期的时间，格式为YYYY-MM-DD’T’hh:mm:ssZ。|
|RequireUpdate|String| -   Yes：建议用户立即更新
-   No：不建议用户立即更新

 |
|RequireUpdateReason|String|建议更新的原因。|

