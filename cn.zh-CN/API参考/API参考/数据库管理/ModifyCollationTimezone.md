# ModifyCollationTimezone {#concept_uff_hks_cfb .concept}

修改系统库的字符集排序规则和时区。系统库包括master、msdb、tempdb和model。

## 请求参数 {#section_qzx_w32_12b .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是|要执行的操作，取值：ModifyCollationTimezone

。|
|DBInstanceId|String|是|实例ID。|
|Collation|String|否|要修改成的系统字符集排序规则，为空表示不修改。系统字符集排序规则与时区必须修改其中至少一个。

|
|Timezone|String|否|要修改成的系统时区，为空表示不修改。系统字符集排序规则与时区必须修改其中至少一个。

|

## 返回参数 {#section_a5x_zlh_12b .section}

|名称|类型|描述|
|--|--|--|
|<公共返回参数\>| |详见[公共参数](cn.zh-CN/API参考/使用API/公共参数.md#)。|
|DBInstanceId|String|实例ID。|
|ModifyResult|String|修改结果：-   Success
-   Failed

|
|ResultMemo|String|修改结果的描述（若有），如错误信息。|

