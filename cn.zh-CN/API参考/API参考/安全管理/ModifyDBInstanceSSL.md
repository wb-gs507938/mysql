# ModifyDBInstanceSSL {#reference_krn_wkh_12b .reference}

## 描述 {#section_l21_v32_12b .section}

该接口只支持MySQL 5.5、MySQL 5.6和SQL Server 2008 R2。

## 请求参数 {#section_qzx_w32_12b .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是|系统规定参数，取值为ModifyDBInstanceSSL。|
|DBInstanceId|String|是|实例名。|
|ConnectionString|String|是|每个实例只能有一个连接地址受SSL保护。为目标连接地址创建或更新SSL证书。|

## 返回参数 {#section_qdm_tf3_12b .section}

|名称|类型|描述|
|--|--|--|
|<公共返回参数\>| |详见[公共参数](cn.zh-CN/API参考/使用API/公共参数.md#)。|
|SSLExpireTime|String|SSL过期的时间，格式为YYYY-MM-DD’T’hh:mm:ssZ。|

