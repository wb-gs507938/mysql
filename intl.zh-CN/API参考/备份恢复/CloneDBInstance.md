# CloneDBInstance {#reference_pys_54l_12b .reference}

基于现有实例的备份文件或按指定时间点克隆出一个新实例。

实例需满足以下条件，否则操作将失败：

-   实例类型为RDS for MySQL。
-   实例状态为运行中。
-   实例当前没有正在执行的迁移任务。
-   实例已开启数据备份和日志备份。
-   若要按备份集克隆实例，则主实例必须至少有一个已完成备份的备份集。

**说明：** RDS支持RAM子账号创建克隆实例，请务必保证子账号已添加克隆实例的授权策略，添加授权请参见[云数据库RDS授权](https://www.alibabacloud.com/help/zh/doc-detail/58932.htm)。

实例内数据库账号信息克隆以及其他功能的设置克隆将遵循如下方式：

-   实例内的白名单设置、SQL审计设置、阈值报警设置、备份设置、参数设置将和当前实例状态保持一致。
-   实例内的数据信息与备份文件当时信息一致。
-   若克隆时主实例为高权限账号，则克隆出的实例带有该主实例的高权限账号信息。
-   若克隆时主实例为普通权限账号状态，则克隆出的实例带有所使用备份文件或时间点当时的账号信息。

## 请求参数 {#section_qzx_w32_12b .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是|要执行的操作。取值：

CloneDBInstance

。|
|DBInstanceId|String|是|实例ID。|
|BackupId|String|否| 备份集ID。

 您可以通过DescribeBackups接口获取备份列表。

 BackupId和RestoreTime两者至少传入一个。

 |
|RestoreTime|String|否| 用户指定备份保留周期内的任意时间点，如2011-06-11T16:00:00Z。

 BackupId和RestoreTime两者至少传入一个。

 |
|PayType|String|是| 付费类型：

 -   Postpaid：按量付费；
-   Prepaid：预付费。

 |
|Period|String|否| 指定预付费实例为包年或者包月类型：

 -   Year：包年；
-   Month：包月。

 若付费类型为Prepaid，则该入参必须传入。

 |
|UsedTime|String|否| 指定购买时长，可按需传入1、2、3等数值。

 付费类型为Prepaid时，该入参必须传入。

 |
|DBInstanceClass|String|否| 实例规格，详见[实例规格表](../../../../intl.zh-CN/产品简介/实例规格/实例规格表.md#)

 该参数为可选参数，若不传入，则默认规格和主实例一致。

 |
|DBInstanceStorage|String|否| 实例的磁盘空间。

 默认与主实例一致，单位GB，每5GB递增。

 RDS实例独占物理机规格可传入范围为\[3000，3000\]。

 其它规格可传入范围为\[5,2000\]。

 |
|InstanceNetworkType|String|否| 实例的网络类型：

 -   Classic：经典网络；
-   VPC：VPC网络。

 默认与主实例网络类型一致。

 |
|VPCId|String|否| VPC ID。

 |
|VSwitichId|String|否| VSwitich ID。

 |
|PrivateIpAddress|String|否| 您可以指定VSwitchId下的VPCId，如果不输入，系统自动分配。

 |

## 返回参数 {#section_a5x_zlh_12b .section}

|名称|类型|描述|
|--|--|--|
|<公共返回参数\>|-| 详见[公共参数](intl.zh-CN/API参考/使用API/公共参数.md#)。

 |
|DBInstanceId|String| 实例ID。

 |
|OrderId|String| 订单ID。

 |

