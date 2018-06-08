# ModifyReadWriteSplittingConnection {#reference_i1k_pjf_12b .reference}

## 描述 {#section_l21_v32_12b .section}

可修改读写分离链路的最大延迟时间和各个实例的读权重。

实例状态必须满足如下所有条件，否则将会操作失败：

-   实例状态为运行中。

-   实例没有迁移任务。

-   实例没有被锁定。


## 请求参数 {#section_qzx_w32_12b .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是|系统规定参数，取值为ModifyReadWriteSplittingConnection。|
|DBInstanceId|String|是|现有主实例名。|
|MaxDelayTime|Int|否| -   延迟阈值，单位为秒。
-   当只读实例延迟时间超过该阈值时，读取流量不发往该实例。
-   不传本参数则保持原值。

 |
|DistributionType|String|否|读权重分配模式：-   Standard：指按规格自动分配权重
-   Custom：指自定义分配权重
-   至少传入MaxDelayTime或DistributionType中的一个。

|
|Weight|Json/ String|否| -   读流量权重分配，即传入主实例和只读实例的读请求权重。
-   以100递增，最大值为10000。
-   按如下格式传入：

\{“Instanceid“:”Weight”,”Instanceid”:”Weight”\}

-   当DistributionType为Custom时，必须传入该参数。
-   当DisrtibutionType为Standard时，传入该参数无效。

 |

## 返回参数 {#section_rpk_z32_12b .section}

|参数|类型|说明|
|--|--|--|
|<公共返回参数\>|-|详见[公共参数](cn.zh-CN/API参考/使用API/公共参数.md#)。|

