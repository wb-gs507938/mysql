# Check the file details about the task of migrating data to RDS {#reference_dj4_pwl_12b .reference}

## Description {#section_l21_v32_12b .section}

This API queries details about cloud data migration tasks, including details about specific migrated files. It has the following constraints:

-   This API is applicable only to SQL Server 2008 R2 instances.

-   The source file must be the full backup file of the source database.


## Request parameters {#section_qzx_w32_12b .section}

|Parameter|Type|Required|Description|
|---------|----|--------|-----------|
|Action|String|Yes|Name of the API. Value: DescribeOssDownloads.|
|DBInstanceId|String|Yes|Instance ID.|
|MigrateTaskId|String|Yes|ID of the migration task.|

## Response parameters {#section_a5x_zlh_12b .section}

|Parameter|Type|Description|
|---------|----|-----------|
|DBInstanceId|String|Instance ID.|
|MigrateTaskId|String|ID of the migration task.|
|Items|List|Import records.|

## Parameters for Items {#section_rjp_cwl_12b .section}

|Parameter|Type|Description:|
|---------|----|------------|
|FileName|String|Name of the backup file stored in an OSS instance.|
|CreateTime|String|Creation time of the backup file in the download list.|
|BackupMode|String|Data migration task type. Currently, only the value FULL can be returned. Optional values:-   FULL: One-time full backup file migration.
-   DIFF: One-time incremental backup file migration.
-   LOG: Multiple migrations of incremental backup files.

|
|FileSize|String|Size of the backup file, in MB.|
|Status|String|File status. Optional values:-   NoStart: Download not started.
-   Downloading: Download in progress.
-   Finished: Download completed.
-   DownloadFailed: Download failed.
-   VerifyFailed: MD5 verification failed.
-   Deleted: Already deleted.
-   DeleteFailed: Deletion failed.
-   CheckSuccess: Check successful.
-   CheckFailed: Check failed.
-   Restoring: Restore in progress.
-   Restored: Restore successful.
-   RestoreFailed: Restore failed.

|
|IsAvailable|String|Availability status. Optional values:-   False: Unavailable.
-   True: Available.

|
|Description|String|File description.|

##   {#section_l4g_pj2_12b .section}

##   {#section_xtg_rj2_12b .section}

