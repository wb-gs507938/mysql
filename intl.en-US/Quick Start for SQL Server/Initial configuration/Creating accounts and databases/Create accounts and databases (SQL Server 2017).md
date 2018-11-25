# Create accounts and databases \(SQL Server 2017\) {#concept_d2l_nlh_wfb .concept}

Before RDS can be used, a database and an account must be created for the RDS instance. For a SQL Server 2017 instance, you need to create an initial account from the RDS console, and then create databases and other accounts through a client. This article uses Microsoft SQL Server Management Studio（SSMS）17.1 as the client.

**Note:** This article is applicable only to RDS for SQL Server 2017. For other versions, see [Create accounts and databases \(SQL Server 2012 or 2016\)](https://www.alibabacloud.com/help/doc-detail/43164.htm) and [Create accounts and databases \(SQL Server 2008 R2\)](https://www.alibabacloud.com/help/doc-detail/26145.htm).

## Precautions {#section_ash_fph_wfb .section}

-   Databases in an instance share all resources of the instance.

-   When assigning permissions to database accounts, assign only the minimum permissions required. If necessary, split accounts and databases into smaller units so that each account can only access data for its own services. If an account does not need to write data to a database, assign read-only permissions.

-   For database security, set strong passwords for the accounts and change the passwords regularly.


## Create an initial account {#section_csh_fph_wfb .section}

1.  Log in to the [RDS console](https://rds.console.aliyun.com/).
2.  Select the region of the target instance.
3.  Click the ID of the instance.
4.  In the left-side navigation pane, select **Accounts** to visit the **Accounts** page.
5.  Click **Create Initial Account**, and fill in the required fields.
    -   Database Account: refers to the name of the account. It can have 2 to 16 characters including the lower-case letters, digits, or underscores \(\_\). It must begin with a letter and end with a letter or digit.

    -   Password: refers to the password corresponding to the initial account. It can have 8 to 32 characters including at least three of the following:

        -   Upper-case letters

        -   Lower-case letters

        -   Digits

        -   Special characters \(!@\#$%^&\*\(\)\_-+=\)

    -   Re-enter Password: re-enter the password to make sure the password is entered correctly.

6.  Click **OK**, and the account is created.

## Create databases and other accounts {#section_bjq_4k4_xfb .section}

1.  Add the IP address of a server or computer to the RDS whitelist. For more information on how to set the whitelist, see [Set the whitelist](intl.en-US/Quick Start for SQL Server/Initial configuration/Set the whitelist.md).
2.  Start the Microsoft SQL Server Management Studio client.
3.  Enter the connection information, as shown in the following figure.

    ![](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/pic/43164/intl_en/1500347363170/Connect%20to%20server.png)

    -   Server type: select **Database Engine**.

    -   Server name: consists of the Internet/intranet address and the corresponding port number of the RDS instance. The connection address and the port number must be separated by a comma, for example, `rm-bptest.sqlserver.rds.aliyuncs.com,3433`. The following shows the procedure to view the connection address and the port information of the RDS instance.

        1.  Log on to the [RDS console](https://rds.console.aliyun.com/).
        2.  Select the region where the target instance is located.
        3.  Click the ID of the instance to visit the **Basic Information** page.
        4.  In the **Basic Information** area, you can find the Internet/intranet address and Internet/intranet port number of the instance, as shown in the following figure.

            ![](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/pic/49015/intl_en/1500277366764/View%20the%20basic%20information%20of%20the%20instance.png)

    -   Authentication: select **SQL Server Authentication**.

    -   Login: refers to the initial account name of the RDS instance.

    -   Password: refers to the password of the initial account of the RDS instance.

4.  Click **Connect**.
5.  Right-click **Databases**, and then select **New Database**.

    ![](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/pic/43164/intl_en/1500349300879/Create%20db_SSMS.png)

6.  In the **New Database** window, select the **General** tab page.
7.  Enter the name of the new database in the **Database name** field, and then click **OK**.

    ![](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/pic/43164/intl_en/1500349586238/Enter%20db%20info_SSMS.png)

8.  When the new database is created successfully, you can find it in **Databases**, as shown in the following figure.

    **Note:** We do not recommend that you do any operations in the default **System Databases**.

    ![](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/pic/43164/intl_en/1500357835479/View%20the%20new%20db_SSMS.png)

9.  Select **Security**, right-click **Logins**, and then select **New Login** to create a standard account, as shown in the following figure.

    ![](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/pic/43164/intl_en/1500358174458/Create%20user_SSMS.png)

10. Enter the name and password of the new account, and select the default database, as shown in the following figure.

    **Note:** Select **SQL Server authentication** and adjust the other password policies based on your business requirements.

    ![](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/pic/43164/intl_en/1500358280145/Enter%20user%20info_SSMS.png)

11. Click **OK**.
12. When the new account is created successfully, you can find it in **Security** \> **Logins**, as shown in the following figure.

    ![](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/pic/43164/intl_en/1500358564937/View%20the%20new%20user_SSMS.png)

13. Double-click the new account to set its properties. You can authorize this account on the **Server Roles** tab page and bind it to certain databases on the **User Mapping**tab page, as shown in the following figure.

    ![](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/pic/43164/intl_en/1500358782406/Set%20user%20properties_SSMS.png)

14. Click **OK**.

