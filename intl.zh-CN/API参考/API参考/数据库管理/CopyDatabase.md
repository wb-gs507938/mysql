# CopyDatabase {#reference_ipv_xfg_12b .reference}

## 描述 {#section_l21_v32_12b .section}

该接口用于在RDS for SQL Server 2008 R2实例内复制数据库。

## 请求参数 {#section_qzx_w32_12b .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是|系统规定参数，取值为CopyDatabase。|
|DBInstanceId|String|是|实例ID。|
|SrcDBName|String|是|要复制的源数据库的名称，实例中必须存在该数据库。|
|DstDBName|String|是|新建的目标数据库的名称，且名称唯一：-   以字母开头；
-   由小写字母，数字、下划线或中划线组成；
-   长度不能超过64个字符。
-   关于其它非法字符，请参见[禁用关键字表](intl.zh-CN/API参考/API参考/附表/禁用关键字表.md#)

|
|ReserveAccount|String|是|是否保留源库的账号：-   如果保留会直接复制到目标库；
-   如果不保留则目标库中不不存该用户账号。

可选值为0和1，默认值为1 。|
|DBDescription|String|否|数据库描述，不超过256个字符。|

## 返回参数 {#section_rpk_z32_12b .section}

|名称|类型|描述|
|--|--|--|
|<公共返回参数\>|String|详见[公共参数](intl.zh-CN/API参考/使用API/公共参数.md#)。|
|RequestId|String|Request ID。|
|DBName|String|数据库名称。|
|DBStatus|String|数据库状态，取值如下：-   Creating：创建中；
-   Running：使用中；
-   Deleting：删除中。

|
|TaskId|String|任务ID。|

