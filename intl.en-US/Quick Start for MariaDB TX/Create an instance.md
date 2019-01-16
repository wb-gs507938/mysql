# Create an instance {#concept_wzp_ncf_vdb .concept}

You can use the RDS console or an API to create an RDS instance. For more information about instance pricing, see [Pricing of ApsaraDB for RDS](https://www.alibabacloud.com/product/apsaradb-for-rds?spm=a3c0i.7938564.220486.8.10521d15zCpnIt#pricing). This document describes how to use the RDS console to create an instance. For more information about how to use an API to create an instance, see [CreateDBInstance](../../../../../intl.en-US/API Reference/Instance management/Create an RDS instance.md#).

## Prerequisites {#section_hyl_tcf_vdb .section}

-   You have registered an Alibaba Cloud account.
-   If you are creating a Pay-As-You-Go instance, make sure that your account balance is sufficient.

## Procedure {#section_o45_5cf_vdb .section}

1.  Log on to the [RDS console](https://rds.console.aliyun.com/?spm=5176.doc43185.2.7.mR2Syx).
2.  On the Instances page, click **Create Instance**.
3.  Select **Subscription** or **Pay-As-You-Go**. For more information about billing methods, see [Billing items and billing methods](../../../../../intl.en-US/Purchase Guide/Billing items and billing methods.md#).
4.  Select the instance configuration. The parameters are described as follows:
    -   Basic configuration
        -   Region and zone: Select the region and zone in which the instance is located. Some regions support both single-zone and multi-zone instances, while some regions support only single-zone instances.

            **Note:** Products in different regions cannot intercommunicate through the intranet, and you cannot change the instance region after creating an instance. Therefore, exercise caution when you select the region.

        -   Database engine: RDS supports MySQL, SQL Server, PostgreSQL, PPAS, and MariaDB TX. Different database types are supported in different regions.
        -   Version: indicates the database version. The MariaDB TX version is 10.3.
        -   Series: RDS for MariaDB TX instances support the High-availability Edition. For more information, see [../../../../../dita-oss-bucket/SP\_60/DNMYSQ1821992/EN-US\_TP\_7787.md](../../../../../intl.en-US/Product Introduction/Product editions/General introduction to product series.md).
    -   Network type: RDS supports the classic network and virtual private cloud \(VPC\). For more information, see [Network types](../../../../../intl.en-US/User Guide/Connection management/Set network type.md#).
    -   Specifications: indicate the CPU and memory occupied by the instance, the number of connections, and the maximum IOPS. For more information about instance specifications, see [Instance type list](../../../../../intl.en-US/Product Introduction/Instance types/Instance type list.md#).
    -   Storage: indicates space used by data, system files, binlog files, and transaction files.
    -   Subscription time: indicates the duration of a Subscription instance.
    -   Quantity: indicates the number of instances with the same configurations to be purchased.
5.  Click **Buy Now** to go to the **Confirm Order** page.
6.  Select **Product Terms of Service and Service Level Notice and Terms of Use**, and then click **Pay Now**.

