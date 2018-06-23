# Create account and database for MySQL 5.7 Basic Edition {#concept_qn2_r2g_vdb .concept}

**Note:** This document is applicable only to MySQL 5.7 Basic Edition instance. For more information on how to create database and account for MySQL 5.7 High-availability Edition and MySQL 5.6 instance, see [Create account and database for MySQL 5.7 High-availability Edition/5.5/5.6 instances](intl.en-US/Quick Start for MySQL/Initial configuration/Create database and account/Create account and database for MySQL 5.7 High-availability Edition/5.5/5.6 instances.md#).

Before RDS can be used, a database and an account must be created for the RDS instance. For MySQL 5.7 Basic Edition instance, you must create an initial account on the RDS console. Then you can create and manage the databases through a client. This document takes the client MySQL-Front as an example to introduce how to create databases and accounts for MySQL 5.7 Basic Edition instance.

## Background information {#section_gzr_zzm_vdb .section}

-   Databases under a single instance share all the resources of this instance. Each instance supports one initial account, countless general accounts, and countless databases. You must create and manage the general accounts and databases through SQL statements. For more information, see [Commonly used SQL commands \(MySQL\)](https://www.alibabacloud.com/help/zh/doc-detail/43889.htm).

-   To migrate the local database to RDS, you must create the same database and account in RDS instance as those of the local database.

-   When assigning account permissions for each database, follow the minimum permission’ principle and service roles to create accounts and rationally assign Read-only and Read/Write permissions. When necessary, you can split accounts and databases into smaller units so that each account can only access data for its own services. If the account does not need to write data to a database, assign Read-only permission.

-   For database security, set strong passwords for the accounts and change the passwords regularly.


## Procedure {#section_h5c_b1n_vdb .section}

1.  Create an initial account.
    1.  Log on to the [RDS console](https://rds.console.aliyun.com/).
    2.  Select the region where the target instance is located.
    3.  Click the ID of the instance to visit the Basic Information page.
    4.  Select **Accounts** in the left-side navigation pane.
    5.  Click **Create Initial Account**.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7820/2432_en-US.png)

        **Parameter description:**

        |Parameters|Description|
        |----------|-----------|
        |Database Account|Refers to the name of the initial account. It can have 2 to 16 characters including the lower-case letters, digits, or underscores. It must begin with a letter and end with a letter or digit.|
        |Password|Refers to the password corresponding to the initial account. It can have 8 to 32 characters including at least three of the following: capital letters, lower-case letters, digits, and special characters \(!@\#$%^&\*\(\)\_-+=\)|
        |Re-enter Password|Enter the password again to make sure that a correct password is entered.|

    6.  Click ****OK****.
    7.  In the RDS whitelist, add the IP address that needs to access the RDS instance. For more information, see [Set a whitelist](intl.en-US/Quick Start for MySQL/Initial configuration/Set a whitelist.md#).
    8.  Start the MySQL-Front client.
    9.  In the Open Connection window, click **New**, as shown in the following figure.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7820/2575_en-US.png)

    10. Enter the information of the RDS instance to be connected, as shown in the following figure.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7820/2576_en-US.png)

        Parameters description:

        -   Description Name: refers to the task name for MySQL-Front to connect each database. If you do not name this task, it is the same with the Host by default.

        -   Host: refers to the connection address. If your client accesses the RDS instance through the intranet, enter the intranet address of the RDS instance. If your client accesses the RDS instance through the Internet, enter the Internet address of the RDS instance. The following shows the procedure to view the connection address and the port information of the RDS instance.

            1.  Log on to the [RDS console](https://rds.console.aliyun.com/).
            2.  Select the region where the target instance is located.
            3.  Click the ID of the instance to visit the Basic Information page.
            4.  On the Basic Information page, you can view information about intranet and Internet IP addresses and ports, as shown in the following figure:

                ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7820/2577_en-US.png)

        -   Port: refers to the port number of the RDS instance. If your application accesses the RDS instance by using the intranet, enter the intranet port number of the RDS instance. If your application accesses the RDS instance by using the Internet, enter the Internet port number of the RDS instance.

        -   User: refers to the initial account name of the RDS instance.

        -   Password: refers to the password corresponding to the initial account of the RDS instance.

    11. Click **OK**.
    12. In the Open Connection window, select the connection task that you created and click **Open**, as shown in the following figure.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7820/2578_en-US.png)

    13. When the instance is successfully connected, click **SQL Editor**, as shown in the following figure.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7820/2579_en-US.png)

    14. Enter the following command in the SQL editor.

        ```
        create database <database name> DEFAULT CHARACTER SET gbk COLLATE gbk_chinese_ci;
        ```

    15. Click the **Run** icon as shown in the following figure to run the command. The database creation is completed.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7820/2580_en-US.png)

    16. In the left directory tree, double click **User**, and then select **New** \> **\> User** to add a user, as shown in the following figure.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7820/2581_en-US.png)

    17. On the General tab page, enter the name and the password of the user, as shown in the following figure.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7820/2582_en-US.png)

    18. On the Rights tab page, click **New** to authorize the user, as shown in the following figure.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7820/2583_en-US.png)

    19. Click **OK**. An account is created.
    20. Double-click **Users**, and you can query all accounts under the instance, as shown in the following figure.

        ![](images/2584_en-US.png)


