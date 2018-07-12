# Recover data from a clone instance to a master instance {#concept_tmr_3b1_ydb .concept}

The data recovery function minimizes the damage caused by database misoperations. We recommend that you recover data to the master instance through a clone instance.

Currently, the following RDS instances support clone instances.

-   MySQL 5.5, 5.6, 5.7 master instances \(except MySQL 5.7 Basic Edition\)

-   SQL Server 2016 High-Availability Edition \(including Standard and Enterprise Editions\)

-   SQL Server 2012 High-Availability Edition \(including Standard and Enterprise Editions\)


To recover data for other RDS instances, see [Recover data from a temporary instance to a master instance](intl.en-US/User Guide/Backup and recovery/Recover SQL Server/PPAS/PostgreSQL data/Recover data to the master instance through a temporary instance.md#).

## Procedure {#section_jtd_v11_ydb .section}

1.  Log on to the [RDS console](https://rdsnew.console.aliyun.com).
2.  Select the region where the target instance is located.
3.  Click the ID of the target instance to go to the **Basic Information** page.
4.  Recover data to a clone instance. For more information, see [Create a clone instance](intl.en-US/User Guide/Backup and recovery/这一篇国际站没有.md#).
5.  After the clone instance is created, go back to the **Basic Information** page of the master instance.
6.  Click **Create Data Migration Task** at the top of the page.
7.  Select **Data migration** in the left-side navigation pane.
8.  Click **Create migration task** at the upper right corner.
9.  Enter the task name, source database information, and target database information.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7959/3948_en-US.png)

    Parameter descriptions:

    -   By default, DTS automatically generates a name for each task. You can edit the name to indicate the specific services for easy identification of the task.

    -   Source database information:

        -   Instance type: Specifies the instance type of a database. Select **RDS Instance**.

        -   Instance region: The region where the master instance is located.

        -   RDS instance ID: Click the drop-down list and select the clone instance ID.

        -   Database account: It is consistent with the account name of the master instance. Make sure that this account has the read/write privilege to all the data to be migrated.

        -   Database password: It is consistent with the password of the master instance account.

    -   Target database information

        -   Instance type: **RDS Instance** by default.

        -   Instance region: The region where the master instance is located.

        -   RDS instance ID: Click the drop-down list and select the master instance.

        -   Database account: The master instance account name. Make sure that this account has the read/write privilege to all the data to be migrated.

        -   Database password: The password of the master instance account.

10. Click **Authorize whitelist and enter into next step**.
11. Select the migration type, choose objects from the **Migration objects** column, and click **\>** to add the objects to the **Selected** column.

    To modify the migration object name in the target database, you can click **Edit** on the right side of the **Selected** list to modify the name.

12. Click **Pre-check and start**.
13. If the system displays the pre-check failure result, click **!** next to the check item with **Check Result**as **Failed** to check the detailed failure information, and perform troubleshooting accordingly.
14. After troubleshooting, select the current migration task on the **Migration task list** page and click **Start**.
15. After pre-check is passed, click **OK** to automatically run the migration task.

