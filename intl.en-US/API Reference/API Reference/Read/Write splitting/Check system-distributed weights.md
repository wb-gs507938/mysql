# Check system-distributed weights {#reference_n4p_cjf_12b .reference}

## Description {#section_l21_v32_12b .section}

This API checks the read weight distributed to each instance when weights are distributed by the system.

This API can only be performed on unlocked instances. Otherwise, the operation fails.

## Request parameters {#section_qzx_w32_12b .section}

|Name|Type|Required|Description|
|----|----|--------|-----------|
|Action|String|Yes|Name of the API. Set this parameter to CalculateDBInstanceWeight.|
|DBInstanceId|String|Yes|Name of the master instance.|

## Return parameters {#section_rpk_z32_12b .section}

|Name|Type|Description|
|----|----|-----------|
|<Public response parameters\>|-|For more information, see [Public parameters](intl.en-US/API Reference/Use APIs/Public parameters.md#).|
|DBInstanceWeights|List|Instance weight that is calculated by the system in real time.|

## DBInstanceWeight {#section_avj_3jf_12b .section}

|Name|Type|Description|
|----|----|-----------|
|DBInstanceId|String|Instance ID.|
|DBInstanceType|String|Instance type. Optional values:-   Master: Refers to a master instance.
-   Readonly: Refers to a read-only instance.

|
|Weight|String|The weight that should be distributed to the instance.|

##   {#section_l4g_pj2_12b .section}

##   {#section_xtg_rj2_12b .section}

