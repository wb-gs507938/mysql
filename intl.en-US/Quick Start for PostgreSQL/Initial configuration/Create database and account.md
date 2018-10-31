# Create database and account {#concept_njz_1gg_wdb .concept}

s

Before using RDS, you must create databases and accounts for the RDS instance. For PostgreSQL instances, you must create an initial account on the RDS console, and then you can create and manage the databases through a client. This document takes the pgAdmin 4 client as an example to introduce how to create databases and accounts for PostgreSQL instances.

## Background information {#section_kcx_dgg_wdb .section}

-   Databases under a single instance share all the resources of this instance. Each PostgreSQL instance supports one initial account, countless general accounts, and countless databases. You must create and manage the general accounts and databases through SQL statements.
-   To migrate your local database to the RDS instance, you must create the same databases and accounts for the RDS instance as your local database.
-   When assigning account permissions for each database, follow the minimum permission’ principle and consider service roles to create accounts. Alternatively, rationally assign read-only and read/write permissions. When necessary, you can split accounts and databases into smaller units so that each account can only access data for its own services. If the account does not need to write data to a database, assign the read-only permission for the account.
-   For database security, set strong passwords for the accounts and change the passwords regularly.

## Procedure {#section_ixc_fgg_wdb .section}

1.  Log on to the [RDS console](https://rds.console.aliyun.com/).
2.  Select the region where the target instance is located.
3.  Click the ID of the instance to visit the Basic Information page.
4.  In the left-side navigation pane, select **Accounts**.
5.  Click **Create Initial Account**.
6.  To create an account, set the related fields.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7850/15409673892960_en-US.png)

    Parameters description:

    -   Database Account: refers to the name of the initial account. It contains 2 to 16 characters including the lower-case letters, digits, or underscores \(\_\). It must begin with a letter and end with a letter or digit.
    -   Password: refers to the password of the initial account. It contains 8 to 32 characters including at least three of the following: capital letters , lower-case letters, digits, and special characters \(!@\#$%^&\*\(\)\_-+=\)
    -   Re-enter Password: Re-enter the password to make sure the password is entered correctly.
7.  Click **OK**.
8.  Add the IP address that is allowed to access the RDS instance to the RDS whitelist. For more information about how to set the whitelist, see [Set whitelist](../../../../intl.en-US/User Guide/Security/Set a whitelist.md#).
9.  Start the pgAdmin 4 client.
10. Right-click **Servers**, and then select **Create** \> **Server**, as shown in the following figure.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7850/15409673894034_en-US.png)

11. On the General tab of Create - Server window, enter server name, as shown in the following figure.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7850/15409673894035_en-US.png)

12. Click the Connection tab, and enter the information of the instance to be connected, as shown in the following figure.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7850/15409673904036_en-US.png)

    Parameters description:

    -   Host name/address: refers to the connection address of the RDS instance. If your application accesses the RDS instance through the intranet, enter the intranet IP address of the RDS instance. If your application accesses the RDS instance through the Internet, enter the Internet IP address of the RDS instance. You can view the connection address and port number as follows:
        1.  Log on to the [RDS console](https://rds.console.aliyun.com/).
        2.  Select the region where the target instance is located.
        3.  Click the ID of the instance to visit the Basic Information page.
        4.  View the intranet and Internet IP addresses and ports in the Basic Information area.
    -   Port: refers to the port number of the the RDS instance. If your application accesses the RDS instance through the intranet, enter the intranet port number of the RDS instance. If your application accesses the RDS instance through the Internet, enter the Internet port number of the RDS instance.
    -   Username: refers to the initial account name of the RDS instance.
    -   Password: refers to the password of the initial account of the RDS instance.
13. Click **Save**.
14. If the connection information is correct, select **Servers** \> **server name** \> **Databases** \> **postgres**. The following interface is displayed, which indicates that the connection to RDS instance is successful.

    **Note:** postgres is the default system database of the RDS instance. Do not do any operation in this database.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7850/15409673904039_en-US.png)

15. Click **postgres**, and then select **Tools** \> **Query Tool**, as shown in the following figure.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7850/15409673906452_en-US.png)

16. Enter the following command on the **Query-1** tab page to create a database, as shown in the following figure.

    ```
    create database <database name>;
    ```

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7850/15409673904040_en-US.png)

17. Click **Execute/Refresh**, as shown in the following figure.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7850/15409673906453_en-US.png)

    If the execution is successful, the new database is created successfully.

18. Right-click **Databases** and click **Refresh**, and then you can find the newly created database, as shown in the following figure.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7850/15409673904041_en-US.png)

19. Enter the following command on the Query-1 tab page to create an account, as shown in the following figure.

    ```
    CREATE ROLE "username" CREATEDB CREATEROLE LOGIN ENCRYPTED PASSWORD 'password';
    ```

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7850/15409673904043_en-US.png)

20. Click **Execute/Refresh**, as shown in the following figure.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7850/15409673906099_en-US.png)

    If the execution is successful, the new account is created successfully.

21. Right-click **Login/Group Roles** and click **Refresh**, and then you can find the newly created account, as shown in the following figure.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7850/15409673904045_en-US.png)


