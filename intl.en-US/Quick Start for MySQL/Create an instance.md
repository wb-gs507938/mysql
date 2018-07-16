# Create an instance {#concept_wzp_ncf_vdb .concept}

You can use the RDS console or API to create RDS instances. For more information about instance pricing, see [Pricing of ApsaraDB for RDS](https://www.alibabacloud.com/product/apsaradb-for-rds?spm=a3c0i.7938564.220486.8.10521d15zCpnIt#pricing). This document describes how to use the RDS console to create an instance. For more information about how to use the APIs to create an instance, see [CreateDBInstance](../../../../intl.en-US/API Reference/API Reference/Instance management/CreateDBInstance.md#).

## Prerequisites {#section_hyl_tcf_vdb .section}

-   You must have registered to an Alibaba Cloud account.
-   If you are creating a Pay-As-You-Go instance, make sure that your account balance is sufficient.

## Procedure {#section_o45_5cf_vdb .section}

1.  Log on to the [RDS console](https://rds.console.aliyun.com/?spm=5176.doc43185.2.7.mR2Syx).
2.  On the Instances page, click **Create Instance**.
3.  Select **Subscription** or **Pay-As-You-Go**. For more information about the billing method, see [Billing items and billing methods](../../../../intl.en-US/Purchase Guide/Billing items and billing methods.md#).
4.  Select the instance configuration. The parameters are described as follows:
    -   Basic configuration
        -   Region and zone: Select the region and zone in which the instance is located. Some regions support a single zone or multi-zone, while some regions support only a single zone.

            **Note:** Products in different regions cannot intercommunicate through the intranet, and you cannot change the instance region after buying an instance. Therefore, be careful when selecting the region.

        -   Database engine: RDS supports MySQL, SQL Server, PostgreSQL, and PPAS. Different database types are supported in different regions. Verify with the actual interface while using this document.
        -   Version: The database version. Currently, RDS supports MySQL 5.5/5.6/5.7, SQL Server 2008 R2/2012, PostgreSQL 9.4, and PPAS 9.3. Different database versions are supported in different regions. Verify with the actual interface while using this document.

            For the MySQL database, we recommend that you select MySQL 5.6 because it supports the TokuDB storage engine, which can save the storage cost by greatly reducing the space occupied by data files.

        -   Series: RDS instances support the Basic Edition, High-availability Edition, and Finance Edition. Different database versions support different series. Verify with the actual interface while using this document.
    -   Network type: RDS supports the classic network and virtual private cloud \(VPC\). VPC needs to be created beforehand. Alternatively, you can change the network type after creating instances. For more information, see [Set network type](../../../../intl.en-US/User Guide/Network management/Set network type.md#).
    -   Type: The CPU and memory occupied by the instance. The number of connections and maximum IOPS \(measured respectively for read and write, up to double of the benchmark with mixed read/write\) vary depending on different types. For more information on instance specifications, see [Instance type list](../../../../intl.en-US/Product Introduction/Instance types/Instance type list.md#).
    -   Storage: The storage space contains space for data, system files, binlog files, and transaction files.
    -   Subscription time: Set the duration of the subscription instance.
    -   Quantity: The number of instances with the same configurations to be purchased.
5.  Click **Buy Now** to go to the **Confirm Order** page.

    **Note:** To buy multiple instances of different configurations, you can click **Add To List** for each instance type and click **Batch Purchase**.

6.  Select **Product Terms of Service and Service Level Notice and Terms of Use**, and then:
    -   Click **Pay**, if the billing method of the instance is subscription.
    -   Click **Activate**, if the billing method of the instance is Pay-As-You-Go.

