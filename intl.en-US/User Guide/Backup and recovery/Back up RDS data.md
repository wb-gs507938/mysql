# Back up RDS data {#concept_l1m_xgn_ydb .concept}

You can configure a backup policy to adjust the cycles of RDS data backup and log backup and as a result, RDS enables the auto-backup feature. You can also manually back up RDS data.

Instance backup files occupy backup space. Charges are incurred if the used space exceeds the free quota. You must design a backup cycle appropriately to cater the service requirements based on the available backup space. For information on the free quota, see [View the free quota of the backup space](intl.en-US/User Guide/Backup and recovery/View the free quota of the backup space.md#). To view the charging standard for backup space usage, see [Pricing](https://www.alibabacloud.com/product/apsaradb-for-rds#pricing).

## Backup policies {#section_oyj_3k4_ydb .section}

ApsaraDB supports data backup and log backup. To recover data by time, you must enable the log backup function. The following table lists the backup policies applicable to different database types:

|Database type|Data backup|Log backup|
|-------------|-----------|----------|
|MySQL| -   MySQL 5.5/5.6/5.7 \(including High-Availability Edition and Finance Edition\):
    -   Automatic backup supports full physical backup.
    -   Manual backup supports full physical backup, full logical backup, and single-database logical backup.
-   MySQL 5.7 Basic Edition:
    -   Supports only snapshot-based backup, not logical backup.
    -   Backup files are retained for at most 7 days for free.

 | -   After being generated, binlogs \(500 MB per log\) are compressed and uploaded immediately. Local files are deleted within 24 hours.
-   Binlog files occupy instance disk capacity. Using the Binlog Upload function, you can upload Binlog files to the OSS. This does not affect the data recovery function and stops the Binlog files from occupying instance disk space.

 |
|SQL Server| -   Supports full physical backup and incremental physical backup.
-   Automatic backup uses the cycle: Full Backup-Incremental Backup-Incremental Backup. For example, if a full backup is performed on Monday, incremental backups are performed on Tuesday and Wednesday, and another full backup is performed on Thursday,with incremental backups on Friday and Saturday, and so on. If a full backup is manually performed at any time in the backup cycle, the next two backups are incremental backups.
-   The SQL Server always compresses transaction logs during the backup process. On the Backup and Recovery page of the target instance’s management console, you can click **Compress Transaction Log** to manually compress the transaction log.

 |Included in data backup; individual transaction logs are not provided for download.|
|PostgreSQL|Supports full physical backup.|After being generated, write-ahead logs \(WALs\) \(16 MB per log\) are compressed and uploaded immediately. Local files are deleted within 24 hours.|
|PPAS|Supports full physical backup.|After being generated, WALs \(16 MB per log\) are compressed and uploaded immediately. Local files are deleted within 24 hours.|

## Automatic backup \(Backup policy setting\) {#section_f33_lk4_ydb .section}

After you configure a backup policy, RDS automatically backs up databases based on the policy.

**Note:** The following uses MySQL 5.7 \(High-Availability Edition\) as an example.

1.  Log on to the [RDS console](https://rds.console.aliyun.com/) .
2.  Click the ID of the instance to visit the Basic Information page.
3.  Select **Backup and Recovery** in the left-side navigation pane.
4.  On the Backup and Recovery page, select **Backup Settings** and click **Edit**.
5.  In the Backup Cycle dialog box, set backup parameters and click **OK**. The parameters are explained as follows:

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7964/4105_en-US.png)

    |Parameters|Description|
    |----------|-----------|
    |Data Retention Period \(days\)|     -   Specifies the time period for which backup files are retained. The default value is 7 days. The value range is 7 to 730 days.
    -   MySQL 5.7 Basic Edition backup files are retained for free for at most 7 days.
 |
    |Backup Cycle Frequency|     -   You can set it to one or multiple days in a week.
    -   SQL Server, PostgreSQL, and PPAS instances are backed up daily by default and this cannot be modified.
 |
    |Next Backup|This value can be set to any time; units: hours.|
    |Log Backup|**Enable** or **Disable**|
    |Log Retention Period \(days\)|     -   Specifies the number of days when the log backup files are retained. The default value is 7 days.
    -   The value range is 7-730 days and it must be less than or equal to the value of the retention days.
 |


## Manual backup {#section_yvd_yk4_ydb .section}

**Note:** The following procedure describes how to configure the single-database logical backup for MySQL 5.7 Basic Edition.

1.  Log on to the [RDS console](https://rds.console.aliyun.com/).
2.  Select the region where the target instance is located.
3.  Click the ID of the instance to visit the Basic Information page.
4.  Click **Back up Instance** at the upper right corner.
5.  Set **Backup Mode** and **Backup Policy**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7964/4105_en-US.png)

    **Note:** 

    -   The backup mode and policy vary with the database type. For more information, see [Backup policies](#section_oyj_3k4_ydb)

    -   If you choose single-database backup, click **\>** to select a database to be backed up. If you do not have a database, create one by referring to [Create a database](intl.en-US/User Guide/Database management/Create a database.md#).

6.  Click **OK**.

