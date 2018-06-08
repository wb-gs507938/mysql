# RemoveTagsFromResource {#reference_brs_rln_12b .reference}

## 描述 {#section_l21_v32_12b .section}

为实例解绑已绑定的标签。限制条件如下：

-   单次最多支持解绑10个标签。

-   若一个标签所绑定的实例全都解绑，则该标签自动删除。

-   在解绑标签时仅传入标签键（TagKey），未传入标签值（TagValue），则解绑符合TagKey条件的标签。


## 请求参数 {#section_qzx_w32_12b .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是|系统规定参数，取值为RemoveTagsFromResource。|
|RegionId|String|是|地域，例如RegionId值为cn-hangzhou。|
|DBInstanceId|String|是|实例ID。|
|Tags|Json String|是| -   需要解绑的Tag，包括TagKey和TagValue；
-   TagKey不能为空，TagValue可以为空。
-   格式示例：\{“key1”:”value1”\}。

 |

## 返回参数 {#section_a5x_zlh_12b .section}

|参数|类型|说明|
|--|--|--|
|<公共返回参数\>|-|详见[公共参数](cn.zh-CN/API参考/使用API/公共参数.md#)。|

