# DescribeTags {#reference_jhb_hln_12b .reference}

## 描述 {#section_l21_v32_12b .section}

查询账号下绑定RDS实例的标签信息。限制条件如下：

-   如果传入指定实例ID，则查询该实例下所有标签，其他过滤条件失效。

-   若查询标签时仅传入标签键（TagKey），未传入标签值（TagValue），则返回所有符合标签键条件的结果。若同时传入标签键和标签值，则返回两个条件都符合的结果。


## 请求参数 {#section_qzx_w32_12b .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是|系统规定参数，取值为DescribeTags。|
|RegionId|String|是|地域，例如RegionId值为cn-hangzhou。|
|DBInstanceId|String|否|实例ID，传入这个参数，其他过滤条件失效。|
|Tags|Json String|否| -   需要查询的Tag列表，包括TagKey和TagValue；
-   TagKey不能为空，TagValue可以为空。
-   格式示例：\{“key1”:”value1”\}。

 |

## 返回参数 {#section_a5x_zlh_12b .section}

|名称|类型|描述|
|--|--|--|
|<公共返回参数\>|无|详见[公共参数](cn.zh-CN/API参考/使用API/公共参数.md#)。|
|Items|List<TagInfos\>|由Tag信息组成的数组。|

## TagInfos {#section_krd_nln_12b .section}

|名称|类型|描述|
|--|--|--|
|TagKey|String|标签键。|
|TagValue|String|标签值。|
|DBInstanceIds|List<DBInstanceId\>|该标签所绑定的实例ID。|

## DBInstanceIds {#section_oms_4ln_12b .section}

|名称|类型|描述|
|--|--|--|
|DBInstanceId|String|实例ID。|

