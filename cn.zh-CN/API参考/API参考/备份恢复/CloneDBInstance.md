# CloneDBInstance {#reference_pys_54l_12b .reference}

## 描述 {#section_l21_v32_12b .section}

基于现有实例的备份文件或指定时间点克隆出一个带有当时数据的新实例。实例内的白名单设置、SQL审计设置、阈值报警设置、备份设置、参数设置将和当前实例状态保持一致。实例内的数据信息与备份文件当时信息一致。

克隆实例仅支持MySQL引擎，实例内数据库账号信息克隆将遵循如下方式：

-   若在克隆时，主实例为高权限账号状态，则克隆出的实例带有该主实例的高权限账号信息。
-   若克隆时，主实例为普通权限账号状态，则克隆出的实例带有所使用备份文件或时间点当时的账号信息。

创建克隆实例时，主实例需要满足如下条件：

-   实例状态为运行中，且没有被锁定。
-   当前没有迁移任务。
-   已开启数据备份和日志备份。
-   若要按备份集克隆实例，则主实例必须至少有一个已完成备份的备份集。

    **说明：** RDS支持RAM子账号创建克隆实例，请务必保证子账号已添加克隆实例的授权策略，添加授权请参见[云数据库 RDS 授权](https://help.aliyun.com/document_detail/58932.html)。


## 请求参数 {#section_qzx_w32_12b .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是|系统规定参数，取值：CloneDBInstance。|
|DBInstanceId|String|是|实例名。|
|BackupId|String|否| -   备份集ID，可通过查询备份列表接口DescribeBackups获取；
-   BackupId和RestoreTime两者至少传入一个。

 |
|RestoreTime|String|否| -   用户指定备份保留周期内的任意时间点，如2011-06-11T16:00:00Z；
-   BackupId和RestoreTime两者至少传入一个。

 |
|PayType|String|是|付费类型：-   Postpaid：按量付费
-   Prepaid：预付费

|
|Period|String|否| -   若付费类型为Prepaid则该入参必须传入；
-   指定预付费实例为包年或者包月类型；
-   Year：包年
-   Month：包月

 |
|UsedTime|String|否|包年包月类型：-   若付费类型为Prepaid则该入参必须传入；
-   指定购买时长，可按需传入1、2、3等数值。

|
|DBInstanceClass|String|否| -   实例规格，详见[实例规格表](../cn.zh-CN/产品简介/实例规格/实例规格表.md#)
-   可选参数，若不传入，则默认规格和主实例一致。

 |
|DBInstanceStorage|String|否| -   磁盘空间，默认与主实例一致，单位GB，每5GB递增；
-   RDS独占物理机规格可传入范围为\[3000，3000\]；
-   其它规格可传入范围为\[5,2000\]。

 |
|InstanceNetworkType|String|否|网络类型：-   Classic：经典网络。
-   VPC：VPC网络
-   默认与主实例网络类型一致。

|
|VPCId|String|否|VPC ID。|
|VSwitichId|String|否|VSwitich ID。|
|PrivateIpAddress|String|否|您可以指定VSwitchId下的VPCId，如果不输入，系统自动分配。|

## 返回参数 {#section_a5x_zlh_12b .section}

|名称|类型|描述|
|--|--|--|
|<公共返回参数\>|无|详见[公共参数](cn.zh-CN/API参考/使用API/公共参数.md#)。|
|DBInstanceId|无|实例名。|
|OrderId|无|订单ID。|

