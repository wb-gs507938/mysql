# View the data encryption status of an instance {#reference_pdf_sch_12b .reference}

## Description {#section_l21_v32_12b .section}

This interface only supports MySQL 5.5, MySQL 5.6, and SQL Server 2008 R2.

## Request parameters {#section_qzx_w32_12b .section}

|Name|Type|Required?|Description|
|----|----|---------|-----------|
|Action|String|Yes|Required parameter. Value: DescribeDBInstanceTDE.|
|DBInstanceId|String|Yes|Instance ID.|

## Return parameters {#section_rpk_z32_12b .section}

|Name|Type|Description|
|----|----|-----------|
|<Public Return Parameters\>| |For more information, see [Public parameters](intl.en-US/API Reference/Use APIs/Public parameters.md#).|
|TDEStatus|String|TDE status of an instance. Value options:-   Enabled: TDE enabled.
-   Disabled: TDE disabled.

|
|Databases|List<DataBase\>|Data composed of the databases.|

## DataBase {#section_qzt_ych_12b .section}

|Name|Type|Description|
|----|----|-----------|
|DBName|String|Database name|
|TDEStatus|String|TDE status of a database. Value options:-   Enabled: TDE enabled.
-   Disabled: TDE disabled.

|

##   {#section_l4g_pj2_12b .section}

##   {#section_xtg_rj2_12b .section}

