# Create database and account {#concept_jx1_w5g_wdb .concept}

Before RDS can be used, a database and an account must be created for the RDS instance. For PPAS instance, you must create an initial account on the RDS console. And then you can create and manage the databases through a client. This document takes the client pgAdmin 4 as an example to introduce how to create databases and accounts for PPAS instance.

## Precautions {#section_zfc_bvg_wdb .section}

-   Databases under a single instance share all the resources of this instance. Each PPAS instance supports one initial account, countless general accounts, and countless databases. You must create and manage the general accounts and databases through SQL statements.

-   To migrate the local database to RDS, you must create the same database and account in RDS instance as those of the local database.

-   When assigning account permissions for each database, follow the minimum permission principle and service roles to create accounts and rationally assign Read-only and Read/Write permissions. When necessary, you can split accounts and databases into smaller units so that each account can only access data for its own services. If the account does not need to write data to a database, assign Read-only permission.

-   For database security, set strong passwords for the accounts and change the passwords regularly.


## Procedure { .section}

1.  Log on to the [RDS console](https://rds.console.aliyun.com/).
2.  Select the region where the target instance is located.
3.  Click the ID of the instance to visit the Basic Information page.
4.  In the left-side navigation pane, select **Accounts**.
5.  Click **Create Initial Account**。
6.  Fill in the required fields.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7862/6102_en-US.png)

    Parameter description:

    -   Database Account: refers to the name of the initial account. It can have 2 to 16 characters including the lower-case letters, digits, or underscores. It must begin with a letter and end with a letter or digit.

    -   Password: refers to the password corresponding to the initial account. It can have 8 to 32 characters including at least three of the following: upper-case letters, lower-case letters, digits, and special characters !@\#$%^&\*\(\)\_-+=

    -   Re-enter Password: re-enter the password to make sure that the password is entered correctly.

7.  Click **OK**, and the initial account creation is completed.
8.  Add the IP address accessing the RDS instance to RDS whitelist. For more information on how to set whitelist, see [Set whitelist](../../../../intl.en-US/User Guide/Security management/Set whitelist.md#).
9.  Start the pgAdmin 4 client.
10. Right click **Servers**, and then select **Create** \> **Server**, as shown in the following figure.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7862/4047_en-US.png)

11. On the General tab of Create Server window, enter server name, as shown in the following figure.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7862/4048_en-US.png)

12. Select the Connection tab, and enter the information of the instance to be connected, as shown in the following figure.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7862/4049_en-US.png)

    Parameter description:

    -   Host name/address: refers to the connection address of the RDS instance. If your application accesses the RDS instance by using the intranet, enter the intranet address of the RDS instance. If your application accesses the RDS instance by using the Internet, enter the Internet address of the RDS instance. The following procedure shows how to find the connection address and port number of the RDS instance.

        1.  Log on to the [RDS console](https://rds.console.aliyun.com/).
        2.  Select the region where the target instance is located.
        3.  Click the ID of the instance to visit the Basic Information page.
        4.  Find the Internet/intranet address and Internet/intranet port number of the instance, as shown in the following figure.

            ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7862/4050_en-US.png)

    -   Port: refers to the port number of the RDS instance. If your application accesses the RDS instance by using the intranet, enter the intranet port number of the RDS instance. If your application accesses the RDS instance by using the Internet, enter the Internet port number of the RDS instance.

    -   Username: refers to the initial account name of the RDS instance.

    -   Password: refers to the password corresponding to the initial account of the RDS instance.

13. Click **Save**.
14. If the connection information is correct, select **Servers** \> **server name** \> **Databases** \> **edb or postgres**, and the following interface appears, which indicates that the connection to RDS instance is successful.

    **Note:** edb and postgres are the default system databases of the RDS instance. Do not do any operation in these two databases.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7862/4051_en-US.png)

15. Select **edb** or **postgres**, and then select **Tools** \> **Query Tool**, as shown in the following figure.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7862/4052_en-US.png)

16. Enter the following command on the **Query-1** tab page to create database, as shown in the following figure.

    ```
    create database <database name>;
    ```

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7862/4053_en-US.png)

17. Click the **Execute/Refresh** icon, as shown in the following figure.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7862/4054_en-US.png)

18. If the execution is successful, it indicates that the new database is created successfully. Right click **Databases** and click **Refresh**, and then you can find the newly created database, as shown in the following figure.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7862/4055_en-US.png)

19. Enter the following command on the Query-1 tab page to create account, as shown in the following figure.

    ```
    CREATE ROLE "username" CREATEDB CREATEROLE LOGIN ENCRYPTED PASSWORD 'password';
    ```

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7862/4056_en-US.png)

20. Click the **Execute/Refresh** icon, as shown in the following figure.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7862/4057_en-US.png)

21. If the execution is successful, it indicates that the new account is created successfully. Right click **Login/Group Roles** and click **Refresh**, and then you can find the newly created account, as shown in the following figure.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7862/4058_en-US.png)


