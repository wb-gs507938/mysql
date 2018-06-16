# Delete an account {#concept_zpq_mdp_ydb .concept}

You can delete an account either using SQL statements or on the RDS console, depending on the type of your instance.

## Delete an account on the RDS console {#section_y2t_22p_ydb .section}

Currently, the RDS console allows you to delete accounts for SQL Server 2008 R2 and MySQL 5.5/5.6 instances.

**Note:** If master accounts are created for MySQL 5.5 and 5.6 instances, all other common accounts can be deleted only using SQL statements.

1.  Log on to the [RDS console](https://rds.console.aliyun.com/).
2.  Select the region where the target instance is located.
3.  Click the ID of the instance to visit the Basic Information page.
4.  In the left-side navigation pane, select **Accounts** to go to the Accounts page.
5.  Find the account you want to delete and click **Delete** in its corresponding Action column.
6.  In the displayed dialog box, click **OK**.

## Delete an account using SQL statements {#section_rtq_j2p_ydb .section}

Currently, you can use SQL statements to delete accounts for MySQL 5.7, PostgreSQL, SQL Server 2012, and PPAS instances.

**Note:** The initial or master accounts cannot be deleted.

1.  Log on to the RDS instance. For more information, see [How to connect to ApsaraDB?](https://www.alibabacloud.com/help/zh/doc-detail/41843.htm)
2.  Run the following command to delete the account. `DROP USER 'username'@'localhost';`

