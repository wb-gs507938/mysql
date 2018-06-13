# Modify the basic information of read/write splitting {#reference_i1k_pjf_12b .reference}

## Description {#section_l21_v32_12b .section}

This API changes the maximum delay of the read/write splitting link or the weight for each instance.

The following conditions must be met, or operation fails:

-   The target instance is running.

-   No migration task is ongoing.

-   The target instance is not locked.


## Request parameters {#section_qzx_w32_12b .section}

|Name|Type|Required|Description|
|----|----|--------|-----------|
|Action|String|Yes|Required parameter. Set this parameter to ModifyReadWriteSplittingConnection.|
|DBInstanceId|String|Yes|Name of a master instance.|
|MaxDelayTime|Int|No| -   Delay threshold, in seconds.
-   Read requests are not routed to the read-only instances with a delay greater than the threshold.
-   If this parameter is not set, the original value is kept.

 |
|DistributionType|String|No|Read weight distribution mode. Values are as follows:-   Standard indicates automatic weight distribution based on specifications.
-   Custom indicates custom weight distribution.
-   Either MaxDelayTime or DistributionType must be set.

|
|Weight|JSON/String|No| -   Read weight distribution. Enter the read weights for the master instance and its read-only instances.
-   Read weights increase at a step of 100 up to 10,000.
-   Enter weights in the following format:

\{“Instanceid“:”Weight”,”Instanceid”:”Weight”\}

-   This parameter must be set when DistributionType is set to Custom.
-   This parameter is invalid when DistributionType is set to Standard.

 |

## Return parameters {#section_rpk_z32_12b .section}

|Name|Type|Description|
|----|----|-----------|
|<Public response parameters\>|-|For more information, see [Public parameters](intl.en-US/API Reference/Use APIs/Public parameters.md#).|

##   {#section_l4g_pj2_12b .section}

##   {#section_xtg_rj2_12b .section}

