# Recover data to the master instance through a temporary instance {#concept_en3_pfn_ydb .concept}

**Note:** This article is not applicable to MySQL instances. To recover data for a MySQL instance, see [Recover data from a clone instance to a master instance](intl.en-US/User Guide/Backup and recovery/Recover MySQL data/Recover data from a clone instance to a master instance.md) \(recommended\) or [Recover data directly to the master instance](intl.en-US/User Guide/Backup and recovery/Recover MySQL data/Recover data directly to the master instance.md).

The data recovery function minimizes the damage caused by database misoperations. We recommend that you recover data to the master instance through a temporary instance. That is to say, recover data to a temporary instance, verify the data, and then migrate the data to the master instance. This avoids the impact of data recovery on the master instance.

## Note: {#section_qn5_l2n_ydb .section}

-   Creating a temporary instance does not affect the master instance.

-   The temporary instance inherits the account and password of the backup file.

-   The network type of the temporary instance is classic network.

-   A master instance can have only one temporary instance at a time. Before creating a temporary instance, delete any existing temporary instance of the master instance.

-   The temporary instance is free of charge, but will be released automatically 48 hours after being created.


## Create a temporary instance {#section_vbm_n2n_ydb .section}

1.  Log on to the [RDS console](https://rds.console.aliyun.com/) and select the region where the target instance is located.
2.  Click the ID of the target instance to go to the Basic information page.
3.  Select **Backup and Recovery** in the left-side navigation pane.
4.  Select the **Temporary Instance** tab.
5.  Select a point in time for recovery and click **Create Temporary Instance**.
6.  In the displayed dialog box, click **OK**.
7.  Go back to the **Instances** page.

## Recover data from the temporary instance to the master instance {#section_xm5_phv_l2b .section}

1.  After the temporary instance is created successfully, click the ID of the master instance to go to the Basic information page.
2.  Click **Create Data Migration Task** in the upper right corner to go to the [Data Transmission Service console](http://dts.console.aliyun.com/).
3.  Select **Data migration** in the left-side navigation pane.
4.  Click **Create migration task**.
5.  Set the parameters. 
    -   Task name: A default task name is generated. You can modify it so that you will identify it more easily later.

    -   Source database information:

        -   Instance type: Select **RDS instance**.

        -   Instance region: Select the region where the master instance is located.

        -   RDS instance ID: Select the ID of the temporary instance.

        -   Database account: Same as the account name of the master instance. Make sure that this account has read/write permissions on the data to be migrated.

        -   Database password: Same as the account password of the master instance.

    -   Target database information:

        -   Instance type: Select **RDS instance**.

        -   Instance region: Select the region where the master instance is located.

        -   RDS instance ID: Select the master instance that has the temporary instance.

        -   Database account: Enter the account name of the master instance. Make sure that this account has read/write permissions on the data to be migrated.

        -   Database password: Enter the account password of the master instance.

6.  Click **Authorization whitelist and enter into next step**.
7.  Select the migration types.
8.  In the left pane, select the objects to be migrated and click **\>** to add them to the right. If you want to modify the name of a migrated object in the target database, you can hover the mouse over the database that needs to be modified in the Selected objects pane and click the displayed **Edit** button.
9.  Click **Pre-check and start**.
10. If the pre-check fails, click **!** next to the failed check item to view detailed failure information, and perform troubleshooting accordingly. After the troubleshooting, find the migration task in the **Migration task list** page and start the pre-check again.
11. After the pre-check is passed, click **OK** to start the migration task.

