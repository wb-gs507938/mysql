# Copy a database for SQL Server 2008 R2 {#reference_ipv_xfg_12b .reference}

## Description {#section_l21_v32_12b .section}

The CopyDatabase API copies a SQL Server 2008 R2 database.

## Request parameters {#section_qzx_w32_12b .section}

|Name|Type|Required|Description|
|----|----|--------|-----------|
|Action|String|Yes|Required parameter. Value: CopyDatabase.|
|DBInstanceId|String|Yes|Instance ID. This API supports only SQL Server 2008 R2 databases.|
|SrcDBName|String|Yes|Name of the source database. The name must exist in the instance and comply with the following rules:-   Start with a letter;
-   Contian only lowercase letters, digits, underscores \(\_\), and hyphens \(-\);
-   Cannot exceed 64 characters;
-   For other invalid characters, see [Forbidden keywords table](intl.en-US/API Reference/API Reference/Schedules/Forbidden keywords table.md#)

|
|DstDBName|String|Yes|Name of the target database. The name must be unique and comply with the following rules:-   Start with a letter;
-   Contian only lowercase letters, digits, underscores \(\_\), and hyphens \(-\);
-   Cannot exceed 64 characters;
-   For other invalid characters, see [Forbidden keywords table](intl.en-US/API Reference/API Reference/Schedules/Forbidden keywords table.md#)

|
|ReserveAccount|String|Yes|Whether to reserve the account of the source database.-   If the account is reserved, it is copied to the target database.
-   Otherwise, the target database does not reserve the user account.

The optional values are 0 and 1, and the default value is 1.|
|DBDescription|String|No|Database description. The length is up to 256 characters.|

## Response parameters {#section_rpk_z32_12b .section}

|Name|Type|Description|
|----|----|-----------|
|<Common response parameters\>|String|For more information, see [Public parameters](intl.en-US/API Reference/Use APIs/Public parameters.md#).|
|RequestId|String|Request ID.|
|DBName|String|Database name.|
|DBStatus|String|Database status. The optional values are as follows:-   Creating
-   Running
-   Deleting

|
|TaskId|String|Task ID.|

##   {#section_l4g_pj2_12b .section}

##   {#section_xtg_rj2_12b .section}

