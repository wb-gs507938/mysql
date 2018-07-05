# Recover data directly to the master instance {#task_yy1_g21_ydb .task}

1.  You can recover data directly to the master instance, and the specified backup data overwrites the data of the master instance, but the data generated after creation of the specified backup data is lost. We recommend that you create a temporary instance for data recovery and migration to guarantee higher security.

    **Note:** 

    -   This article is applicable only to MySQL instances. To recover data directly to a SQL server instance, see [Recover data directly to the master instance](intl.en-US/User Guide/Backup and recovery/Recover SQL Server/PPAS/PostgreSQL data/Recover data directly to the master instance.md)
    -   If a read-only instance exists, the specified backup data cannot directly overwrite the original data of the master instance. You can only recover the data through a clone instance. For more information, see [Recovering from a temporary instance to a primary instance recovering from a clone instance to a primary instance](intl.en-US/User Guide/Backup and recovery/Recover MySQL data/Recovering from a clone or temporary instance to a primary instance.md).
2.   Log on to the [RDSconsole](https://rds.console.aliyun.com/) . 
3.   Select the region where the target instance is located. 
4.   Click the ID of the target instance to go to the Basic Information page. 
5.   Select **Backup and Recovery** in the left-side menu. 
6.   Select the **Backup List** tab. 
7.   Select the time range and click **Query**. 
8.   Find the target backup and click **Restore** in the Action column. 
9.   In the displayed dialog box, select **Coverage Restoration** and click **OK**. 
10.  Click **OK** again. 

