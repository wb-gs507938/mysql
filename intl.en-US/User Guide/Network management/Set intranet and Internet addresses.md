# Set intranet and Internet addresses {#concept_tv3_pq1_ydb .concept}

You can select the connection type \(intranet or Internet\) of the instance according to the business requirements. The system generates the intranet address by default, so this document mainly introduces how to apply for the Internet address, set the connection address of the Internet or intranet, and release the Internet address.

## Background information {#section_j4h_tq1_ydb .section}

RDS supports connections through the intranet addresses and Internet addresses. The [series](../../../../intl.en-US/Product Introduction/Product editions/General introduction to product series.md), version, and [access mode](intl.en-US/User Guide/Network management/Set access mode.md#) have the following effects on the selection of the connection address.

|Instance series|Instance version|Access mode|Connection address|
|:--------------|:---------------|:----------|:-----------------|
|Basic Edition| -   MySQL 5.7
-   SQL Server 2012

 |Standard mode| -   Intranet address
-   Internet address
-   intranet and Internet addresses

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
-   intranet and Internet addresses

 |
|Finance Edition|MySQL 5.6|Standard mode| -   Intranet address
-   Internet address

 |
|Safe connection mode| -   Intranet address
-   Internet address
-   intranet and Internet addresses

 |

The applicable scenarios of the connection addresses are as follows:

-   Use the intranet address only:

    -   The system provides an intranet address by default and you can directly modify the connection address.

    -   This scenario is applicable when your application is deployed on the ECS instance that is located in the same region and has the same network type with those of your RDS instance.

-   Use the Internet address only:

    -   This scenario is applicable when your application is deployed on the ECS instance that is located in the different region with that of your RDS instance.

    -   This scenario is applicable when your application is deployed on the platform other than Alibaba Cloud.

-   Use both of the intranet and Internet addresses:

    -   This scenario is applicable when your application is deployed on the ECS instance that is located in the same region and has the same [network type](intl.en-US/User Guide/Network management/Set network type.md#) as your RDS instance, and on the ECS instances of different regions at the same time.

    -   This scenario is applicable when your application is deployed on the ECS instance that is located in the same region and has the same [network type](intl.en-US/User Guide/Network management/Set network type.md#) as your RDS instance, and on the platform other than Alibaba Cloud at the same time.


## Attentions {#section_ok3_rr1_ydb .section}

-   Before accessing the database, you must add the IP addresses or IP segments used to access the database to a whitelist. For more information, see Set whitelist.

-   The RDS charges a fee for traffic over the Internet address. For detailed charges, see [RDS Pricing](https://www.alibabacloud.com/product/apsaradb-for-rds?spm=a3c0i.7938564.220486.3.FrsJgg#pricing).

-   Connecting to the RDS instance with an Internet address reduces the instance security. To get a higher transmission rate and a higher security level, we recommend that you migrate your applications to the ECS instances in the same region with that of your RDS.


## Apply for the Internet address {#section_adc_sr1_ydb .section}

1.  Log on to the [RDS console](https://rds.console.aliyun.com/) .
2.  Select the region where the target instance is located.
3.  Click the ID of the instance to visit the Basic Information page.
4.  Select Connection options in the left-side navigation pane.
5.  Click **Apply for Internet Address**, as shown in the following picture.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7945/15335196883991_en-US.png)

6.  On the displayed confirmation window, click **OK** to generate an Internet address.

## Modify the connection address {#section_upj_cs1_ydb .section}

You can modify the Internet and intranet connection address as per your needs. Do as follows:

1.  Log on to the [RDS console](https://rds.console.aliyun.com/).
2.  Select the region where the target instance is located.
3.  Click the ID of the instance to visit the Basic Information page.
4.  Select Connection options in the left-side navigation pane.
5.  Select the Instance Connection tab.
6.  In the Connection Information area, click **Modify Connection Address**.
7.  Select the connection type and modify its connection addresses and port number, and then click **OK**, as shown in the following figure.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7945/15335196883992_en-US.png)

    Parameters description:

    -   Connection type: Select intranet address or Internet address according to the connection type to be modified.

    -   Connection Address: the address format is xxx.sqlserver.rds.aliyuncs.com and xxx is a user-defined field. The address can have 8 to 64 characters including letters and digits. It must begin with a lower-case letter.

    -   Port: indicates the number of the port through which RDS provides external services, which can be an integer within the range \[3200, 3999\].


## Release the Internet address {#section_pjm_ps1_ydb .section}

If you must release the Internet address, do as follows:

**Note:** The operation is displayed under the safe connection mode. For more information about safe connection mode, see [Set access mode](intl.en-US/User Guide/Network management/Set access mode.md#).

1.  Log on to the [RDS console](https://rds.console.aliyun.com/).
2.  Select the region where the target instance is located.
3.  Click the ID of the instance to visit the Basic Information page.
4.  Select Connection options in the left-side navigation pane.
5.  Select the Instance Connection tab.
6.  In the Connection Information area, click **Release Internet Address**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7945/15335196883993_en-US.png)

7.  Click **Confirm** on the displayed confirmation interface to release the Internet address.

