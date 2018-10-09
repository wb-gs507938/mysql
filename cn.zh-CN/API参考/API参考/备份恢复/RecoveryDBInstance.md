# RecoveryDBInstance {#reference_iqf_v4t_h2b .reference}

恢复数据库。

先创建一个实例，再在新实例上恢复原实例的数据库：

-   若指定数据库名，则新实例只恢复对应的数据库（单库恢复）；
-   若不指定数据库名，则新实例会恢复原实例上的所有数据库，此时功能类似于克隆实例：[CloneDBInstance](cn.zh-CN/API参考/API参考/备份恢复/CloneDBInstance.md#)。

**说明：** 该接口暂时仅适用于SQL Server 2012及以上版本的实例。

## 请求参数 {#section_tgm_1mt_h2b .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是|系统规定参数，取值为：RecoveryDBInstance。|
|DBInstanceId|String|否|原实例ID。-   按备份集恢复（即指定BackupId参数）时，本参数不是必须。
-   按时间点恢复（即指定RestoreTime参数）时，本参数为必须。

|
|TargetDBInstanceId|String|否|目标实例名。|
|DBInstanceClass|String|否|新实例规格。|
|DBInstanceStorage|String|否|新实例存储容量。|
|DBInstanceDescription|String|否|新实例描述。|
|PayType|String|否|新实例付费类型：-   Postpaid：后付费，按量付费；
-   Prepaid：预付费，包年包月。

|
|InstanceNetworkType|String|否|新实例网络类型：-   Classic：经典网络；
-   VPC：专有网络，VPC网络。

默认与主实例网络类型一致。

|
|DbNames|String|是|数据库名：`{"sourceDbName1":"targetDbName1","sourceDbName2":"targetDbName2"}`。|
|BackupId|String|否|备份集ID，可通过查询备份列表接口[DescribeBackups](cn.zh-CN/API参考/API参考/备份恢复/DescribeBackups.md#)获取。指定此参数时，DBInstanceId参数为可选。

BackupId和RestoreTime两者至少传入一个。

|
|RestoreTime|String|否|备份保留周期内的任意时间点，例如2011-06-11T16:00:00Z指定此参数时，DBInstanceId参数为必须。

BackupId和RestoreTime两者至少传入一个。

|
|VPCId|String|否|VPCId。|
|VSwitchId|String|否|VSwitch Id，多个值用英文逗号“,”隔开。|
|PrivateIpAddress|String|否|您可以指定VSwitchId下的VPCId，如果不输入，系统自动分配。|
|usedTime|String|否|包年包月类型：-   若付费类型为Prepaid，则该入参必须传入；
-   指定购买时长，可按需传入1、2、3等数值。

|
|Period|String|否| -   若付费类型为Prepaid，则该入参必须传入；
-   指定预付费实例为包年或者包月类型：
    -   Year：包年；
    -   Month：包月。

 |

## 返回参数 {#section_nrn_z4t_h2b .section}

|参数|类型|描述|
|--|--|--|
|RequestId|String|详见[公共参数](cn.zh-CN/API参考/使用API/公共参数.md#)。|
|DBInstanceId|String|实例名。|
|OrderId|String|订单ID。|

