# ModifyDBInstanceDelayReplicationTime {#reference_j4c_yrq_p2b .reference}

## 描述 {#section_pyg_v54_p2b .section}

修改只读实例延迟时间。

## 请求参数 {#section_qhs_w54_p2b .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是|系统规定参数，取值：ModifyDBInstanceDelayedReplicationTime。|
|DBInstanceId|String|是|只读实例ID。|
|ReadSQLReplicationTime|Integer|是|只读实例延时复制时间，单位为：秒。默认值：0。|

## 返回参数 {#section_mx3_1x4_p2b .section}

|参数|类型|说明|
|--|--|--|
|RequestId|String|详见[公共参数](intl.zh-CN/API参考/使用API/公共参数.md#)。|
|DBInstanceId|String|实例ID。|
|DelayedReplicationTime|String|延迟时间。|
|TaskId|String|任务ID。|

