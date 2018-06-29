# RecoveryDBInstance {#reference_iqf_v4t_h2b .reference}

## 描述 {#section_b2s_g3t_h2b .section}

该接口用于单库恢复。

## 请求参数 {#section_tgm_1mt_h2b .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是|系统规定参数，取值为：RecoveryDBInstance。|
|DBInstanceId|String|是|实例名。|
|DBInstanceClass|String|否|实例规格。|
|DBInstanceStorage|String|否|存储容量。|
|DBInstanceDescription|String|否|实例描述。|
|DBInstanceStorage|String|否|存储容量。|
|PayType|String|否|付费类型：Postpaid：后付费，按量付费；Prepaid：预付费，包年包月。|
|InstanceNetworkType|String|否|网络类型：Classic：经典网络；VPC：专有网络，VPC网络默认与主实例网络类型一致。|
|DbNames|String|是|数据库名称。|
|BackupId|String|否|备份集ID，可通过查询备份列表接口[DescribeBackups](cn.zh-CN/API参考/API参考/备份恢复/DescribeBackups.md#)获取；BackupId和RestoreTime两者至少传入一个。|
|RestoreTime|String|否|用户指定备份保留周期内的任意时间点，例如2011-06-11T16:00:00Z；BackupId和RestoreTime两者至少传入一个。|
|VPCId|String|否|VPCId。|
|VSwitchId|String|否|VSwitchId。|
|PrivateIpAddress|String|否|您可以指定VSwitchId下的VPCId，如果不输入，系统自动分配。|
|usedTime|String|是|包年包月类型：-   若付费类型为Prepaid，则该入参必须传入；
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

