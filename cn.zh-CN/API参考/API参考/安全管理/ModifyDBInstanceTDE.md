# ModifyDBInstanceTDE {#reference_urs_klh_12b .reference}

## 描述 {#section_l21_v32_12b .section}

该接口只支持MySQL 5.6和SQL Server 2008 R2：

-   加密密钥由密钥管理服务（KMS）产生和管理，RDS不提供加密所需的密钥和证书。开通TDE后，用户如果要恢复数据到本地，需要先通过RDS解密数据。

-   开通TDE前需要先开通KMS。如果您未开通KMS，可在开通TDE过程中根据引导开通KMS。

-   对于SQL Server 2008R2，只支持DB级别的TDE开启和关闭，开启DB级别的TDE时也会修改实例级别的TDE状态。

-   对于MySQL 5.6，只支持实例级别的TDE开启，不接受DBName传值。

-   TDE开通后无法关闭，且会增加CPU使用率。


## 请求参数 {#section_qzx_w32_12b .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是|系统规定参数，取值为ModifyDBInstanceTDE。|
|DBInstanceId|String|是|实例名。|
|TDEStatus|String|是| -   Enabled：TDE开启
-   Disabled：TDE关闭

 |
|DBName|String|否|数据库名，可以一次输入多个，以英文半角“,”分隔，最多传入50个。|

## 返回参数 {#section_a5x_zlh_12b .section}

|名称|类型|描述|
|--|--|--|
|<公共返回参数\>| |详见[公共参数](intl.zh-CN/API参考/使用API/公共参数.md#)。|

