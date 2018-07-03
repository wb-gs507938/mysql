# Preface {#concept_gws_2dh_wdb .concept}

## Overview {#section_nkl_hdh_wdb .section}

ApsaraDB for Relational Database Service \(RDS\) is a stable and reliable online database service with auto-scaling capabilities. Based on Apsara’s distributed file system and high-performance storage of ephemeral SSD, RDS supports MySQL, SQL Server, PostgreSQL, and PPAS engines, and provides a complete set of solutions for disaster recovery, backup, restoration, monitoring, migration, and others. This helps you to operate and manage your own database. To learn about the benefits of RDS, see [Benefits](../../../../intl.en-US/Product Introduction/Benefits.md#).

This document describes RDS features and functions and further explains the procedure to configure RDS through the [RDS console](https://rds.console.aliyun.com/) . With the help of this information you can also manage the RDS through APIs and SDKs.

If you need technical assistance, you can open the [RDS console](https://rds.console.aliyun.com/) and choose **Support \> Open a new ticket** or [click here](https://workorder-intl.console.aliyun.com/#/ticket/createIndex)  to submit a ticket.

For more information about functions and pricing of RDS, log on to the [official website of ApsaraDB for RDS](https://www.alibabacloud.com/product/apsaradb-for-rds).

## Declaration {#section_hnn_3dh_wdb .section}

Some product features or services described in this document may be unavailable for certain regions. See the relevant commercial contracts for specific Terms and Conditions.

This document serves as a user guide. No content in this document can constitute any express or implied warranty.

The content of this document is updated as per the product upgrade and many other respective factors. You must first verify the document with your latest corresponding software version.

## Consideration {#section_jks_jdh_wdb .section}

RDS includes multiple types of databases. This document takes the MySQL database as an example to describe the features and usage of all the RDS products. Some types of databases may not include certain features. The actual interface may vary slightly.

## General terms { .section}

-   Instance: A database service process that takes up physical memory independently. You can set different memory size, disk space, and database type, among which the memory specification determines the performance of the instance. After the instance is created, you can change the configuration and delete the instance at any time.
-   Database: A logical unit created in an instance. Multiple databases can be created in an instance, and the database name is unique within the instance.
-   Region and zone: A region is a physical datacenter. A zone is a physical area that has independent power supply and networks. For more information, see [Alibaba Cloud Global Infrastructure](https://www.alibabacloud.com/global-locations).

## General terms {#section_pyp_ndh_wdb .section}

|Term|Description|
|----|-----------|
|Local database/Source database|Refers to the database deployed in the local equipment room or the database not on the ApsaraDB. In most cases, it refers to the source database to be migrated to the ApsaraDB in this document.|
|RDS for XX \(MySQL, SQL Server, PostgreSQL, PPAS\)|It indicates the RDS of a specific database type, for example, RDS for MySQL means the instance enabled on the RDS and whose database type is MySQL.|

