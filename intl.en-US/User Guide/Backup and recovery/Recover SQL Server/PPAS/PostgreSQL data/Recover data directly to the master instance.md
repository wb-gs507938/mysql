# Recover data directly to an instance {#concept_ed1_fgn_ydb .concept}

You can recover data directly to an instance, and the specified backup data overwrites the data of the instance, and the data generated after creation of the specified backup data is lost. We recommend that you create a temporary instance for data recovery and migration to guarantee higher security.

**Note:** 

-   This method is only applicable to the database of SQL Server 2008 R2.

## Procedure {#section_ilr_kgn_ydb .section}

1.  Log on to the [RDS console](https://rds.console.aliyun.com/).
2.  Select the region where the target instance is located.
3.  Click the ID of the target instance to enter the Basic Information page.
4.  Select **Backup and Recovery** in the left-side menu.
5.  Select the **Backup List** tab.
6.  Select the time range for recovery and click **Query**.
7.  Select the target backup file and click **Coverage Restoration**, as shown in the following figure.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7963/6111_en-US.png)

8.  Click **Confirm** in the dialog box to recover data to the master instance.

