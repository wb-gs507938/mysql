# AddTagsToResource {#reference_wxm_lkn_12b .reference}

## 描述 {#section_l21_v32_12b .section}

为实例绑定已有的或新创建的标签，限制如下：

-   每个标签（Tag）由标签键（TagKey）和标签值（TagValue）组成，TagKey不能为空，TagValue可以为空。

-   TagKey和TagValue的值不允许以aliyun开头。

-   TagKey和TagValue不区分大小写。

-   TagKey最长为64个字符，TagValue最长为128个字符。

-   每个实例最多绑定10个Tag，且每个实例绑定的TagKey不能重复。若绑定带有重复TagKey的Tag，则最后绑定的Tag将覆盖已绑定的Tag。


## 请求参数 {#section_qzx_w32_12b .section}

|名称|类型|是否必须|描述|
|Action|String|是|系统规定参数，取值为AddTagsToResource。|
|RegionId|String|是|地域，例如RegionId值为cn-hangzhou。|
|DBInstanceId|String|是| -   实例ID，支持传入多个实例Id进行批量操作，最多传入30个；
-   格式示例：instance1,instance2,instance3。

 |
|Tags|Json String|是| -   需要绑定的Tag列表，包括TagKey和TagValue；
-   单次最多支持传入5组值；
-   TagKey不能为空，TagValue可以为空。
-   格式示例：\{“key1”:”value1”,“key2”:””\}。

 |

## 返回参数 {#section_a5x_zlh_12b .section}

|名称|类型|描述|
|--|--|--|
|<公共返回参数\>|无|详见[公共参数](cn.zh-CN/API参考/使用API/公共参数.md#)。|

