# CalculateDBInstanceWeight {#reference_n4p_cjf_12b .reference}

## 描述 {#section_l21_v32_12b .section}

该接口用于查询在系统权重分配方式下，每个只读实例被分配的读请求权重值。

**说明：** 

-   仅适用于RDS for MySQL实例。
-   主实例必须在没有被锁定的情况下才能进行查询，否则操作将失败。

## 请求参数 {#section_qzx_w32_12b .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是|系统规定参数，取值为CalculateDBInstanceWeight。|
|DBInstanceId|String|是|主实例ID。|

## 返回参数 {#section_rpk_z32_12b .section}

|参数|类型|说明|
|--|--|--|
|<公共返回参数\>|-|详见[公共参数](intl.zh-CN/API参考/使用API/公共参数.md#)。|
|DBInstanceWeights|List|系统实时计算的只读实例权重信息。|

## DBInstanceWeight {#section_avj_3jf_12b .section}

|名称|类型|描述|
|--|--|--|
|DBInstanceId|String|只读实例ID。|
|DBInstanceType|String|实例类型：-   Master：主实例
-   Readonly：只读实例

|
|Weight|String|只读实例所分配的权重。|

