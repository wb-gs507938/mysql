# Create master account {#concept_bys_1j5_vdb .concept}

## Background information {#section_ivs_z35_vdb .section}

RDS supports the classic mode and the master mode. For instances of MySQL 5.7 High-availability Edition, MySQL 5.6, and MySQL 5.5, you can create a master account to upgrade the account management mode from classic to master. The following figure shows how to switch from the classic mode to the master mode, and their differences in creating and managing databases and accounts.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7821/2588_en-US.png)

Compared with the classic mode, the master mode enables more permissions to meet the personalized and sophisticated permission management needs. You can also use SQL to directly manage databases and accounts. Therefore, we recommend that you use the master mode.

This document describes how to upgrade the account management mode, namely to create a master account, of MySQL 5.7 High-availability Edition, MySQL 5.6, and MySQL 5.5. For details about the usage, supported engines, functions, and permissions of accounts in the classic mode and master mode, see [Create an account](../../../../intl.en-US/User Guide/Account management/Create an account.md#).

## Attention { .section}

-   After a master account is created for a master instance, it is synchronized to the read-only instances and disaster tolerance instances.

-   In the master mode:

    -   You can manage databases and common accounts only by using [Commonly used SQL commands for MySQL](../../../../intl.en-US/User Guide/Appendix/Commonly used SQL commands for MySQL.md#), rather than using the RDS console or APIs.

    -   However, you can reset the permissions and password of the master account on the RDS console or through API, without affecting other accounts in the instance.

-   The following changes occur after an instance switches to the master account mode: After the master account is created, the Databases page and **Create Account** on the Accounts page disappear. However, this change only affects the single instance and has nothing to do with other instances.

-   For MySQL 5.5/5.6 instances:

    -   You can only upgrade from the classic mode to the master mode and does not support rollback.

    -   You cannot directly access the mysql.user and mysql.db tables, but you can view the existing account and permissions through mysql.user\_view and mysql.db\_view.

    -   You cannot use the master account to modify passwords of other common accounts. To modify passwords of other common accounts, you must delete the master account and create a new account.

-   MySQL 5.7 instances support only the master mode.

-   When the master account is created, the instance restarts once, causing a transient network disconnection in 30s. Make sure that you create an account at proper time, and the application supports auto-reconnection, to prevent disconnections, if any.


**Procedure**

1.  Log on to the [RDS console](https://rds.console.aliyun.com/).
2.  Select the region where the target instance is located.
3.  Click the ID of the instance to visit the Basic Information page.
4.  Select **Accounts** in the left-side navigation pane to visit the Accounts page.
5.  Click **Create Master Account**, as shown in the following figure.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7821/2589_en-US.png)

6.  Select **I understand the above warnings and want to proceed with creating a master account** and click **Next**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7821/2590_en-US.png)

7.  Enter the relevant details in the required fields.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7821/2591_en-US.png)

    Parameter descriptions:

    -   Database Account: The account is a string of 2 to 16 characters. It must contain lowercase letters, numbers, and underscores \(\_\). The account must start with a letter and end with a letter or a number.

    -   Password: Password of the account. The password is a string of 8 to 32 characters. It must contain any three of letters, numbers, hyphens \(-\), and underscores \(\_\).

    -   Re-enter Password: Re-enter the password to verify that the password is entered correctly.

8.  Click **Create**.

    **Note:** After a master account is created, the account name cannot be modified, but the password can be modified later on the console.


