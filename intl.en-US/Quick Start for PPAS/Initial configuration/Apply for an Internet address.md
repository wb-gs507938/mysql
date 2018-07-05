# Apply for an Internet address {#concept_zx5_ytg_wdb .concept}

If your application is deployed on the ECS instance that is located in the same region and has the same [network type](../../../../intl.en-US/User Guide/Network management/Set network types.md#) with those of your RDS instance, you do not need an Internet address. If your application is deployed on the ECS that is located in the different region or has the different network type with those of your RDS instance, or on a platform other than Alibaba Cloud, an Internet address is necessary to access an RDS instance.

**Note:** When the instances are in the same region \(the zones can be different\), they can access each other through the intranet.

## Background information {#section_eh3_c5g_wdb .section}

RDS supports connections through the intranet addresses and Internet addresses. The [access mode](../../../../intl.en-US/User Guide/Network management/Set access mode.md#) and [instance type](../../../../intl.en-US/Product Introduction/Instance types/Instance type list.md#) have the following effects on the selection of the connection address.

|Instance series|Instance version|Access mode|Connection address|
|---------------|----------------|-----------|------------------|
|Basic Edition| -   MySQL 5.7
-   SQL Server 2012

 |Standard mode| -   Intranet address
-   Internet address
-   Intranet and Internet addresses

 |
|High-availability Edition| -   MySQL 5.5/5.6
-   SQL Server 2008 R2
-   PostgreSQL 9.4
-   PPAS 9.3

 |Standard mode| -   Intranet address
-   Internet address

 |
|Safe connection mode| -   Intranet address
-   Internet address
-   Intranet and Internet addresses

 |
|Finance Edition|MySQL 5.6|Standard mode| -   Intranet address
-   Internet address

 |
|Safe connection mode| -   Intranet address
-   Internet address
-   Intranet and Internet addresses

 |

The applicable scenarios of the connection addresses are as follows:

-   Use the intranet address only:

    -   The system provides an intranet address by default and you can directly modify the connection address.

    -   This condition is applicable when your application is deployed on the ECS instance that is located in the same region and has the same [network type](../../../../intl.en-US/User Guide/Network management/Set network types.md#) as your RDS instance.

-   Use the Internet address only:

    -   This condition is applicable when your application is deployed on the ECS instance that is located in the different region with that of your RDS instance.

    -   This condition is applicable when your application is deployed on the platform other than Alibaba Cloud.

-   Use both of the intranet and Internet addresses:

    -   This condition is applicable when your application is deployed on the ECS instance that is located in the same region and has the same [network type](../../../../intl.en-US/User Guide/Network management/Set network types.md#) as your RDS instance, and on the ECS instances of different regions at the same time.

    -   This condition is applicable when your application is deployed on the ECS instance that is located in the same region and has the same [network type](../../../../intl.en-US/User Guide/Network management/Set network types.md#) as your RDS instance, and on the platform other than Alibaba Cloud at the same time.


## Attention { .section}

-   Before accessing the database, you must add the IP addresses or IP segments used to access the database to a whitelist. For more information, see [Set whitelist](../../../../intl.en-US/User Guide/Security management/Set whitelist.md#).

-   A traffic fee is charged for connections using an Internet address. For more information about pricing and fees charges, see [RDS Pricing](https://www.alibabacloud.com/product/apsaradb-for-rds?spm=a2c63.p38356.a3.8.27427f39WeCYZ1#pricing).

-   Connecting the RDS instance with an Internet address may reduce the instance security. Do proceed with caution. To get a higher transmission rate and a higher security level, we recommend that you migrate your applications to the ECS instances in the same region with that of your RDS.


## Procedure { .section}

1.  Log on to the [RDS console](https://rds.console.aliyun.com/).
2.  Select the region where the target instance is located.
3.  Click the ID of the instance to visit the Basic Information page.
4.  Select **Database Connection** in the left-side navigation pane to visit the Database Connection page.
5.  Click **Apply for Internet Address**, as shown in the following picture.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7861/4046_en-US.png)

6.  On the displayed confirmation window, click **OK** to generate an Internet address.
7.  Click **Modify Connection Address** to modify the connection address and port of the Internet or intranet, as shown in the following picture.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7861/2972_en-US.png)

    Parameter description:

    -   Connection Type: select **intranet Address** or **Internet Address** according to the connection type to be modified.

    -   Connection Address: the address format is `xxx.mysql.rds.aliyuncs.com` and *xxx* is a user-defined field. The address can have 8 to 64 characters including letters and digits. It must begin with a lower-case letter.

    -   Port: indicates the number of the port through which RDS provides external services, which can be an integer within the range \[3200, 3999\].

8.  Click **OK**.

