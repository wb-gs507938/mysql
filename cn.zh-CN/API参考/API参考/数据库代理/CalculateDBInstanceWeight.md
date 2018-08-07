# CalculateDBInstanceWeight {#reference_n4p_cjf_12b .reference}

## 描述 {#section_l21_v32_12b .section}

该接口用于查询在系统权重分配方式下，每个实例会被分配的读请求权重值。

实例必须在没有被锁定的情况下才能进行查询，否则操作将会失败。

## 请求参数 {#section_qzx_w32_12b .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是|系统规定参数，取值为CalculateDBInstanceWeight。|
|DBInstanceId|String|是|主实例名。|

## 返回参数 {#section_rpk_z32_12b .section}

|参数|类型|说明|
|--|--|--|
|<公共返回参数\>|-|详见[公共参数](intl.zh-CN/API参考/使用API/公共参数.md#)。|
|DBInstanceWeights|List|系统实时计算的实例权重信息。|

## DBInstanceWeight {#section_avj_3jf_12b .section}

|名称|类型|描述|
|--|--|--|
|DBInstanceId|String|实例ID。|
|DBInstanceType|String|实例类型：-   Master：r指主实例
-   Readonly：只读实例

|
|Weight|String|实例所应分配权重。|

