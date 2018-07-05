# Connect to an instance {#concept_nks_hwg_wdb .concept}

You can connect to an RDS instance through a PostgreSQL client. This document introduces the connection procedure by taking the pgAdmin 4 client as an example.

## Background information {#section_jgt_kwg_wdb .section}

Here, we take the pgAdmin 4 client as an example to connect to an RDS instance. You can see this method when using other clients. When you connect to an RDS instance through clients, choose to use the [intranet or Internet address](../../../../intl.en-US/User Guide/Network management/Set intranet and Internet addresses.md) as follows:

-   Use the intranet address when your client is installed on the ECS that is located in the same region and the same [network type](https://www.alibabacloud.com/help/doc-detail/26194.htm) with those of the RDS instance to be connected.

-   Use the Internet address for the other situations.


## Procedure { .section}

1.  Add the IP address accessing the RDS instance to RDS whitelist. For more information, see [Set a whitelist](../../../../intl.en-US/Quick Start for MySQL/Initial configuration/Set a whitelist.md#).
2.  Start the pgAdmin 4 client.
3.  Right click **Servers**, and then select **Create** \> **Server**, as shown in the following figure.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7863/2976_en-US.png)

4.  On the **General** tab of the **Create - Server** window, enter the server name, as shown in the following figure.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7863/2977_en-US.png)

5.  Select the **Connection** tab and enter the information of the instance to be connected, as shown in the following figure.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7863/2978_en-US.png)

    Parameter description:

    -   Host name/address: refers to the connection address of the RDS instance. If your application accesses the RDS instance by using the intranet, enter the intranet address of the RDS instance. If your application accesses the RDS instance by using the Internet, enter the Internet address of the RDS instance. Do the following steps to find the connection address and port number of the RDS instance:

        1.  Log on to the [RDS console](https://rds.console.aliyun.com/).
        2.  Select the region where the target instance is located.
        3.  Click the ID of the instance to visit the Basic Information page.
        4.  Find the connection addresses and port numbers of the RDS instance.

            ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7863/2979_en-US.png)

    -   Port: refers to the port number of the RDS instance. If your application accesses the RDS instance by using the intranet, enter the intranet port number of the RDS instance. If your application accesses the RDS instance by using the Internet, enter the Internet port number of the RDS instance.

    -   Username: refers to the initial account name of the RDS instance.

    -   Password: refers to the password corresponding to the initial account name of the RDS instance.

6.  Click **Save**.
7.  If the connection information is correct, select **Servers** \> **server name** \> **Databases** \> **edb** or **postgres**, and the following interface appears, which indicates that the connection to RDS instance is successful.

    **Note:** edb and postgres are default system databases of the RDS instance. Do not perform any operation in these databases.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7863/2980_en-US.png)


