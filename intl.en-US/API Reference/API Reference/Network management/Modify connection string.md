# Modify connection string {#reference_hbm_h13_12b .reference}

## Description {#section_l21_v32_12b .section}

This interface is used to modify connection string names and ports. Currently, RDS provides intranet and Internet connection strings and allows both types to coexist in a specific access mode.

## Request parameters {#section_qzx_w32_12b .section}

|Name|Type|Required or Not|Description|
|----|----|---------------|-----------|
|Action|String|Yes|Required parameter. Value: ModifyDBInstanceConnectionString.|
|DBInstanceId|String|Yes|Instance ID.|
|CurrentConnectionString|String|Yes|Current connection string of an instance.|
|ConnectionStringPrefix|String|No|Target connection string.|
|Port|String|No|Target port.|

## Return parameters {#section_a5x_zlh_12b .section}

|Name|Type|Description|
|<Public Return Parameters\>|-|For more information, see [Public parameters](intl.en-US/API Reference/Use APIs/Public parameters.md#).|

##   {#section_l4g_pj2_12b .section}

##   {#section_xtg_rj2_12b .section}

