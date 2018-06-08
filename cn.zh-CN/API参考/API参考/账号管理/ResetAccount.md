# ResetAccount {#reference_wxt_hbh_12b .reference}

## 描述 {#section_l21_v32_12b .section}

该接口用于重置实例的初始账号。

**说明：** 该接口不适用于没有高权限账号的MySQL 5.5/5.6实例以及SQL Server 2008 R2实例。

## 请求参数 {#section_qzx_w32_12b .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是|系统规定参数，取值为ResetAccount。|
|DBInstanceId|String|是|实例名。|
|AccountName|String|是|账号名。|
|AccountPassword|String|是|账号密码。|

## 返回参数 {#section_rpk_z32_12b .section}

|名称|类型|描述|
|--|--|--|
|<公共返回参数\>| |详见[公共参数](cn.zh-CN/API参考/使用API/公共参数.md#)。|

