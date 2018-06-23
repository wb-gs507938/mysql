# Modify the RDS instance access mode {#reference_pyz_mm2_12b .reference}

## Description {#section_l21_v32_12b .section}

Currently, two access modes are available for RDS:

-   Standard access mode
-   High security access mode

## Request parameters {#section_qzx_w32_12b .section}

|Name|Type|Required?|Description|
|----|----|---------|-----------|
|Action|String|Yes|Required parameter. Value: ModifyDBInstanceConnectionMode.|
|DBInstanceId|String|Yes|Instance ID.|
|ConnectionMode|String|Yes| -   Performance: standard access mode.
-   Safe: high security access mode.

 |

## Return parameters {#section_rpk_z32_12b .section}

|Name|Type|Description|
|<Public Return Parameters\>|-|For more information, see [Public parameters](intl.en-US/API Reference/Use APIs/Public parameters.md#).|

