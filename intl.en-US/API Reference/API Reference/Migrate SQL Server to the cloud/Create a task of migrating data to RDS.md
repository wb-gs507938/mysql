# Create a task of migrating data to RDS {#reference_ab3_f5l_12b .reference}

## Description {#section_l21_v32_12b .section}

This API restores the backup files in an OSS instance to an RDS instance. It has the following constraints:

-   This API is applicable only to SQL Server 2008 R2 instances.

-   The source file must be the full backup file of the source database.


## Request parameters {#section_qzx_w32_12b .section}

|Parameter|Type|Required|Description|
|---------|----|--------|-----------|
|Action|String|Yes|API of the action, system required parameter. Set this parameter to CreateMigrateTask.|
|DBInstanceId|String|Yes|Instance ID.|
|DBName|String|Yes|Database name.|
|BackupMode|String|Yes|Task type. Currently, this parameter can only be set to FULL. Optional values:-   FULL: One-time full backup file migration.
-   DIFF: One-time incremental backup file migration.
-   LOG: Repeated incremental backup file migration.

|
|IsOnlineDB|String|Yes|Whether to bring the restored database online for user access. Optional values: True and False. The default value is True. Currently, this parameter is invariably set to True.|
|OSSUrls|String|Yes|Sharing URL of the backup file in the OSS instance. The URL must be encoded. If multiple URLs are available for a backup file, separate them with `|`. Currently, only one URL is allowed.|

## Response parameters {#section_a5x_zlh_12b .section}

|Parameter|Type|Description|
|---------|----|-----------|
|<Public response parameters\>|-|For more information, see [Public parameters](intl.en-US/API Reference/Use APIs/Public parameters.md#).|
|RequestId|String|Request ID.|
|DBInstanceId|String|Instance ID.|
|DBName|String|Database name.|
|TaskId|String|Task ID.|
|MigrateTaskId|String|ID of the migration task.|
|BackupMode|String|Task type. Currently, this parameter can only be set to FULL. Optional values:-   FULL: One-time full backup file migration.
-   DIFF: One-time incremental backup file migration.
-   LOG: Multiple migrations of incremental backup files.

|

##   {#section_l4g_pj2_12b .section}

##   {#section_xtg_rj2_12b .section}

