# Migrate data to RDS for SQL Server 2012/2016 {#concept_msg_hpw_ydb .concept}

This document describes how to migrate full backup data to RDS for SQL Server 2012/2016.

Applicable versions

-   Basic series \(single-node\): RDS for SQL Server 2016/2012 Web or Enterprise Edition
-   High-availability series \(dual-node\): RDS for SQL Server 2016/2012 Standard or Enterprise Edition

For instructions on how to migrate data to RDS for SQL Server 2008 R2 Enterprise Edition \(high-availability series\), see [Migrate data to RDS for SQL Server 2008 R2](intl.en-US/User Guide/Data migration/Migrate SQL Server to cloud/Migrate data to RDS for SQL Server 2008 R2.md#).

## Restrictions {#section_pzt_zsj_zdb .section}

**Backup file version**

Backup data of new SQL Server versions cannot be migrated to old SQL Server versions. For example, you cannot migrate data from SQL Server 2016 to SQL Server 2012.

**Backup file type**

Differential and log backup files are not supported.

**Backup file suffix**

The backup file suffix must be bak, diff, trn, or log. If your backup file is not generated using the script provided in this document, use one of the following suffix:

-   bak: indicates a full backup file.
-   diff: indicates a differential backup file.
-   trn or log: indicates a transaction log backup file.

**Backup file name**

The name of the full backup file cannot contain certain special characters, such as @ or |. Otherwise, the migration will fail.

## Precautions {#section_ybw_1tj_zdb .section}

**AliyunRDSImportRole**

After you authorize the RDS official service account to access OSS, the system creates the role AliyunRDSImportRole in the RAM system. Do not modify or delete the role. Otherwise, the backup upload cannot succeed, and you need to perform the authorization on the wizard again.

**Delete backup file from OSS**

Before the backup restoration is complete, do not delete the backup file from OSS.

## Prerequisites {#section_ibz_btj_zdb .section}

**Instance capacity**

Ensure that the RDS for SQL Server instance has sufficient storage space. Expand the space if needed.

**A database with the same name is not allowed in the target instance.**

You do not need to create a target database in advance. This is different from the requirement stated in [Migrate data to RDS for SQL Server 2008 R2](intl.en-US/User Guide/Data migration/Migrate SQL Server to cloud/Migrate data to RDS for SQL Server 2008 R2.md#).

If the target RDS instance already has a database whose name is the same as that of a database to be migrated, back up and delete the database in the target RDS instance before creating a migration task.

**Create a superuser account on target instance.**

It is recommended that you create a superuser account for the target instance on the console in advance. If the target instance does not have a superuser account, the migration can succeed but you cannot access the database unless you take measures by referring to **Common Errors** at the end of this document.

For information about how to create a superuser account, see [Create accounts and databases \(SQL Server 2012 or 2016\)](https://www.alibabacloud.com/help/doc-detail/43164.htm).

**Prepare an OSS bucket**

Create an OSS bucket that is in the same region as the target instance if you do not have one.

1.  Log on to [OSS console](https://oss.console.aliyun.com/).
2.  Click the **+** sign on the left pane.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7998/154392152633677_en-US.png)

3.  Set the bucket name, region, storage class, and ACL permission, and click **OK**. \(Ensure that the bucket is in the same region as the target RDS for SQL Server instance so that the bucket can be selected in subsequent steps.\)

**Run DBCC CHECKDB**

Run DBCC CHECKDB\(‘xxx’\) on the local database and ensure that the result is as follows, with no allocation errors or consistency errors.

```

CHECKDB found 0 allocation errors and 0 consistency errors in database 'xxx'.
DBCC execution completed. If DBCC printed error messages, contact your system administrator.
```

If DBCC CHECKDB shows any errors, fix them before migration.

## Procedure {#section_f25_nfk_zdb .section}

Only three steps are required to migrate a local database to an RDS for SQL Server 2012/2016 instance:

1.  Back up the local database.
2.  Upload the backup file to OSS.
3.  Create a migration task.

## Back up the local database {#section_idn_mfk_zdb .section}

Before performing a full backup of the local database, stop writing data into the database. Data written into the database during the backup will not be backed up.

You can perform a full backup by using your own method or following these steps:

1.  Download the [backup script](https://rdshelpattachments.oss-cn-beijing.aliyuncs.com/Migration/RDSBackupSpecifiedDatabasesToLocal.sql) and open it with SSMS.
2.  Modify the following parameters as needed:

    |Configuration item|Description|
    |------------------|-----------|
    |@backup\_databases\_list|Databases to be backed up. Separate multiple databases with semicolons \(;\) or commas \(,\).|
    |@backup\_type|Backup type. Values are as follows:    -   FULL: full backup
    -   DIFF: differential backup
    -   LOG: log backup
|
    |@backup\_folder:|Local folder that stores the backup file. It will be automatically created if it does not exist.|
    |@is\_run|Whether to perform a backup. Values are as follows:    -   1: Perform a backup.
    -   0: Only perform a check.
|

3.  Run the backup script.

## Upload the backup file to OSS {#section_g33_vfk_zdb .section}

Use any of the following methods to upload the backup file to your OSS bucket:

**Method 1: Use ossbrowser**

It is recommended that you use the ossbrowser tool to upload the backup file to OSS. For more information, see [ossbrowser](https://www.alibabacloud.com/help/doc-detail/61872.htm).

**Method 2: Use the OSS console**

If the backup file is smaller than 5 GB, you can use the OSS console to upload it. For more information, see [Upload an object](https://www.alibabacloud.com/help/doc-detail/31886.htm).

**Method 3: Use an OSS API**

If you require automatic migration, use an OSS API to perform an upload that can be paused and resumed. For more information, see [Multipart upload](https://www.alibabacloud.com/help/doc-detail/31850.htm).

## Create a migration task {#section_tmd_xfk_zdb .section}

1.  Log on to the [RDS console](https://rdsnew.console.aliyun.com/).
2.  Select the region where the target instance is located.
3.  Click the target instance ID to enter the Basic Information page.
4.  On the left-side navigation pane, click **Backup and Recovery**.
5.  Click **OSS Backup Data Upload** at the upper right corner.
6.  If you are using the function for the first time, authorize the RDS official service account to access OSS:
    1.  In the **import data** step of the **Import Guide**, click **Authorize**.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7998/15439215266114_en-US.png)

    2.  Click **Confirm Authorization Policy**.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7998/154392152633679_en-US.png)

7.  Set the following parameters and click **OK** to generate an OSS backup file upload task.

    |Configuration item|Description|
    |------------------|-----------|
    |Database Name|Target database name in the target instance|
    |OSS Bucket|OSS bucket that stores the backup file|
    |OSS Subfolder Name|Name of the subfolder where the backup is located.|
    |OSS File|Click the magnifier icon on the right. You can perform a fuzzy search with the backup file prefix. The file names, sizes, and update time are displayed. Select the backup file you need.|
    |Cloud Migration Plan|     -   **Immediate Access \(Full Backup\)**: If you have only the full backup file, select **Immediate Access**.
    -   **Access Pending \(Incremental Backup\)**: If you have a full backup file and a differential or log backup file, select this option.
 |
    |Consistency Check Mode|     -   **Synchronous DBCC**: Perform DBCC check only after the database is opened. This reduces service downtime because DBCC check takes a long time if the database is large. If you are sensitive to service downtime and do not care about the DBCC check result, select this option.
    -   **Asynchronous DBC**C: If you want to use DBCC check to find out consistency errors of your source database, select this option. Note that this option lengthens the time it takes to open the database.
 |

    You can click **Refresh** to view the latest status of the migration task. If the migration fails, view the task description and rectify faults by referring to **Common errors** at the end of this document.


## View migration records {#section_j5n_bgk_zdb .section}

View migration records as follows:

On the **Backup and Recovery** page, click **Backup Data Upload History**. Migration records of the past week are displayed by default. You can change the query time range as needed.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7998/154392152633681_en-US.png)

## Common errors {#section_cgb_fgk_zdb .section}

Each migration record has a task description, which helps you identify the failure cause. Common errors are as follows:

**Database with the same name already exists**

-   Error message: The database \(xxx\) is already exist on RDS, please backup and drop it, then try again.
-   Error cause: An existing database with the same name is not allowed in the target instance. This prevents you from mistakenly overwriting a database.
-   Solution: If a database with the same name already exists in the target instance, perform a full backup of the database on the console and delete the database before the migration.

**Differential backup files**

-   Error message: Backup set \(xxx.bak\) is a Database Differential backup, we only accept a FULL Backup.
-   Error cause: The migration supports only full backup files rather than differential backup files.

**Transaction log backup files**

-   Error message: Backup set \(xxx.trn\) is a Transaction Log backup, we only accept a FULL Backup.
-   Error cause: Full migration supports only full backup files rather than log backup files.

**Backup file verification fails**

-   Error message: Failed to verify xxx.bak, backup file was corrupted or newer edition than RDS.
-   Error cause: The verification fails because the backup file is damaged or the local SQL Server version is later than the target RDS SQL Server version. For example, the verification fails if the migration is from SQL Server 2016 to SQL Server 2012.
-   Solution: If the backup file is damaged, perform a full backup again to generate a new backup file. If the local SQL Server version is later than the target RDS SQL Server version, change the target RDS SQL Server version.

**DBCC CHECKDB errors**

-   Error message: DBCC checkdb failed
-   Error cause: DBCC CheckDB failure indicates that the local database has errors.
-   Solution:
    1.  Run the following command to fix the local database \(this may cause data loss\):

        ```
        DBCC CHECKDB (DBName, REPAIR_ALLOW_DATA_LOSS) WITH NO_INFOMSGS, ALL_ERRORMSGS
        ```

    2.  Perform a full backup for the database again.
    3.  Upload the new database file to OSS.
    4.  Perform the migration again on the RDS console.

**OSS download link expires**

This error only happens to the RDS for SQL 2008 R2 High-availability Edition instances.

-   Error message: Failed to download backup file since OSS URL was expired.
-   Error cause: The OSS download link has expired, so the backup file download fails.
-   Solutions:
    -   Solution 1: Set the download link validity period to a larger value \(at most 18 hours\).

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7998/154392152733682_en-US.png)

    -   Solution 2: Set the ACL permission of the OSS database backup file to **Public Read**.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7998/154392152733684_en-US.png)

        **Note:** The backup file with the Public Read ACL permission can always be downloaded without an expiration date. To prevent security risks, set the ACL permission to **Private** after migrating the file.


**Insufficient space 1**

-   Error message: Not Enough Disk Space for restoring, space left \(xxx MB\) < needed \(xxx MB\)
-   Error cause: The remaining space on the instance is insufficient for migration.
-   Solution: Expand the storage space of the instance.

**Insufficient space 2**

-   Error message: Not Enough Disk Space, space left xxx MB < bak file xxx MB
-   Error cause: The remaining space on the instance is smaller than the backup file size.
-   Solution: Expand the storage space of the instance.

**No superuser account**

-   Error message: Your RDS doesn’t have any init account yet, please create one and grant permissions on RDS console to this migrated database \(XXX\).
-   Error cause: If the RDS instance has no superuser account, the migration still succeeds, but the migration task does not know which user to authorize.
-   Solution:
    1.  Create a superuser account. For details, see [Create accounts and databases \(SQL Server 2012 or 2016\)](https://www.alibabacloud.com/help/doc-detail/43164.htm).
    2.  Reset the password of the superuser account. For more information, see [Reset the instance password](intl.en-US/User Guide/Account management/Reset the instance password.md#).
    3.  Use the superuser account to access the database on the cloud.

