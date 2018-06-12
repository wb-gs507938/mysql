# Create backup {#reference_ryg_rg3_12b .reference}

## Description {#section_l21_v32_12b .section}

Create backups. Up to 10 backups can be created for an instance in a single day. The following conditions must be met, otherwise backup creation will fail:

-   The instance is active.
-   The last backup has been completed.

## Request parameters {#section_qzx_w32_12b .section}

|Name|Type|Required?|Description|
|----|----|---------|-----------|
|Action|String|Yes|Required parameter. Value: CreateBackup.|
|DBInstanceId|String|Yes|Instance ID.|
|BackupMethod|String|No| -   Logical: logical backup.
-   Physical: physical backup.
-   The default value is Physical. Logical backup does not support instances without databases.
-   SQL Server only supports physical backup.

 |
|BackupStrategy|String|No|Range of logical backup.-   db: single-database backup.
-   instance: instance backup.
-   This parameter is valid only when BackupMethod is Logical.

|
|DBName|String|No|Name of the database for single-database logical backup. This parameter is valid only when BackupMethod is Logical and BackupStrategy is db.|
|BackupType|String|No| -   Auto: determines whether it is a full backup or an incremental backup through automatic calculation.
-   FullBackup: indicates a full backup. The default value is Auto.

 |

## Return parameters {#section_a5x_zlh_12b .section}

|Name|Type|Description|
|----|----|-----------|
|<Public Return Parameters\>| |For more information, see [Public parameters](intl.en-US/API Reference/Use APIs/Public parameters.md#).|

## Request example {#section_l4g_pj2_12b .section}

```
https://rds.aliyuncs.com/?Action= CreateBackup
&DBInstanceId=riauvjz6zajfiq6ba1370329449201
&<Public Request Parameters>
```

## Response example {#section_xtg_rj2_12b .section}

**XML format:**

```
<CreateBackupResponse>
       <RequestId>DA147739-AEAD-4417-9089-65E9B1D8240D</RequestId>
</CreateBackupResponse>
```

**JSON format:**

```

       "RequestId":"DA147739-AEAD-4417-9089-65E9B1D8240D"

```

