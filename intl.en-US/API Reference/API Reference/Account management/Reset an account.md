# Reset an account {#reference_wxt_hbh_12b .reference}

## Description {#section_l21_v32_12b .section}

Reset the initial account or master account of an instance.

**Note:** This API is not applicable to MySQL 5.5/5.6 instance that has no master account or SQL Server 2008 R2 instance.

## Request parameters {#section_qzx_w32_12b .section}

|Name|Type|Required|Description|
|----|----|--------|-----------|
|Action|String|Yes|Required parameter. Value: ResetAccount.|
|DBInstanceId|String|Yes|Instance ID.|
|AccountName|String|Yes|Name of an account.|
|AccountPassword|String|Yes|Account password.|

## Return parameters {#section_rpk_z32_12b .section}

|Name|Type|Description|
|----|----|-----------|
|<Public Return Parameters\>| |For more information, see [Public parameters](intl.en-US/API Reference/Use APIs/Public parameters.md#).|

##   {#section_l4g_pj2_12b .section}

##   {#section_xtg_rj2_12b .section}

