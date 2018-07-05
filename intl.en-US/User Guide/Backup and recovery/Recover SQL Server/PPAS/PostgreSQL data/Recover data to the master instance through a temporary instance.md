# Recover data to the master instance through a temporary instance {#concept_en3_pfn_ydb .concept}

中国站

The data recovery function can minimize the damage caused by database misoperations. We recommend that you recover data to the master instance through a temporary instance.

Creating a temporary instance does not affect the current production instance but offers a temporary instance for data access. We recommend that you recover data to a temporary instance and verify the data before migrating the data to the master instance. This avoids the impact of data recovery on services.

## Note: {#section_qn5_l2n_ydb .section}

-   The temporary instance inherits the account and password of the backup file.

-   The network type of temporary instance is classic network.

-   The temporary instance uses its instance name as the password. Only one temporary instance can be generated at the same time. Before you create a temporary instance, delete any existing temporary instance.

-   The temporary instance is valid for 48 hours.


## Procedure {#section_vbm_n2n_ydb .section}

1.  Log on to the [RDS console](https://rds.console.aliyun.com/) and select the region where the target instance is located.
2.  Click the ID of the target instance to go to the Basic information page.
3.  Select **Backup And Recovery** in the left-side navigation pane to go to the Backup and recovery page,
4.  and then select the **Temporary instance** tab.
5.  Select the recovery time point, and click **Create temporary instance**.
6.  Click **OK** in the dialog box to create a temporary instance.
7.  After the temporary instance is created, go to the Instance list page.
8.  Click the ID of the target instance to go to the Basic information page.
9.  Click **Create a data migration task** in the upper right corner to go to [Data Transmission console](http://dts.console.aliyun.com/).
10. Select **Data migration** in the left-side navigation pane to go to the Migration task list page.
11. Click **Create migration task** to enter the Create migration task page.
12. Enter the task name, source database and target database information, and click Authorize whitelist and enter into next step. 

    ![](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/pic/26207/cn_zh/1496825100821/%E8%BF%81%E7%A7%BB%E6%95%B0%E6%8D%AE.png)

    Parameters description:

    -   Task name: custom task name or default value.

    -   Source database information:

        -   Instance type: Specifies the instance type of a database. Select RDS Instance.

        -   Instance region: The region where the master instance is located.

        -   RDS instance ID: Click the drop-down list and select the temporary instance ID.

        -   Database account: It is consistent with the account name of the master instance. Make sure that this account has the read/write privilege to all the data to be migrated.

        -   Database password: It is consistent with the password of the master instance account.

        -   Connection mode: You can select a non-encrypted or encrypted connection. If you select SSL secure connection, SSL needs to be enabled for instances in the source database first. For details, see [Set SSL encryption](https://help.aliyun.com/document_detail/32474.html).

    -   Target database information:

        -   Instance type: RDS Instance by default.

        -   Instance region: The region where the master instance is located.

        -   RDS instance ID: ID of the target RDS instance. Click the drop-down list and select the master instance mapped to the temporary instance.

        -   Database account: The master instance account name. Make sure that this account has the read/write privilege to all the data to be migrated.

        -   Database password: The password of the master instance account.

        -   Connection mode: You can select a non-encrypted or encrypted connection. If you select SSL secure connection, SSL needs to be enabled for instances in the source database first. For details, see [Set SSL encryption](https://help.aliyun.com/document_detail/32474.html).

13. Click **Authorization whitelist and enter into next step** to enter the Migration Type and List page.
14. Select the migration type, choose the migration object from the Migration objects column, and click ****\>**** to add the migration object to the Selected column. If you want to modify the name of the migrated object in the target database, you can mouse over the database that needs to be modified in the Selected column. Then, the **Edit** button is displayed, as shown in the following figure.

    ![](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/pic/26207/cn_zh/1496827601510/%E9%80%89%E6%8B%A9%E8%BF%81%E7%A7%BB%E5%AF%B9%E8%B1%A1.png)

15. And then click **Pre-check** and start.

    **Note:** 

    -   Before the migration task is started, pre-check must be performed. The migration taskk can be started only after the pre-check is passed. For specific pre-check content, see [Introduction to pre-check](https://help.aliyun.com/document_detail/52099.html).

    -   The following uses the failed pre-check as an example: If the pre-check is passed, go to step 18.

16. If the system displays the pre-check failure result, click **!** next to the check item with **Check Result as Failed** to check the detailed failure information, and perform troubleshooting accordingly. After troubleshooting, select the current migration task on the **Migration task list** page and click Start.

    ![](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/pic/26207/cn_zh/1496828913256/rds_newuser_image_024.png)

17. After troubleshooting, on the migration task list page, select the newly created Migration task on the Migration task list page, click **Start**, as shown in the following figure.

    ![](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/pic/26207/cn_zh/1496829072181/rds_newuser_image_025.png)

18. After pre-check is passed, click **OK** to automatically run the migration task.
19. 中国站

