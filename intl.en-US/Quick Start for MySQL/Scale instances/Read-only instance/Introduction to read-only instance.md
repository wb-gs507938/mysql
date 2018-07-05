# Introduction to read-only instance {#concept_cst_z45_vdb .concept}

## Scenario {#section_lkt_qp5_vdb .section}

For a business that needs a lesser number of write requests but a greater number of read requests to the database, a single instance might not resist the read pressure. It may affect the business operations. To achieve the elastic expansion of the read ability and to share the pressure of the database, you can create one or more read-only instances in a region. The read-only instances can handle massive read requests sent to the database and increase the application throughput.

## Overview {#section_iw3_zqc_zdb .section}

A read-only instance is a read-only copy of the master instance. Changes in the master instance are also automatically synchronized to all relevant read-only instances through the native replication capability of MySQL. The synchronization works even if the master and read-only instances have different network types. The read-only instance and the master instance must be in the same region, but they can be in the different zones. The following topology displays the positioning of the read-only instance.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7826/6089_en-US.png)

## Note {#section_jk2_tp5_vdb .section}

-   Currently, only the following ApsaraDB for RDS versions support read-only instances: MySQL 5.6 and MySQL 5.7 \(excluding MySQL 5.7 Basic Edition\)

-   A read-only instance is in a single-node architecture with no slave node.


## Pricing {#section_fwf_5p5_vdb .section}

The billing method of read-only instances is Pay-As-You-Go. For more information, see [Pricing](https://www.alibabacloud.com/product/apsaradb-for-rds?spm=a3c0i.7938564.220486.8.10521d15K8Buqg#pricing).

**Note:** For information about data retention policies for read-only instances, see [Expiration and overdue payment](../../../../intl.en-US/Purchase Guide/Expiration and overdue payment.md).

## Features {#section_zx1_zp5_vdb .section}

Read-only instances offer the following features:

-   The specifications of a read-only instance can differ from those of the master instance, and can be changed at any time, to facilitate easy elastic upgrade and downgrade.

-   Read-only instances support billing measured per hour, which is user-friendly and cost-efficient.

-   No account or database maintenance is required for a read-only instance. Both the account and database are synchronized through the primary instance.

-   Read-only instances support independent whitelist configuration.

-   Read-only instances support system performance monitoring.

    Up to 20 system performance monitoring views can be used, which includes disk capacity, IOPS, connections, CPU utilization, and network traffic. Users can view the load of instances at ease.

-   Read-only instances provide optimization suggestions.

    Optimization tools support storage engine check, primary key check, large table check, and excessive indexing and missing indexing checks.


## Restrictions { .section}

Read-only instances have the following usage restrictions:

-   One master instance can only have five read-only instances.

-   Read-only instances do not support backup settings or temporary backup.

-   Instance recovery:

    -   Read-only instances do not support the creation of temporary instances through backup files or any point in time backups. Read-only instances do not support the overwriting of instances using backup sets.

    -   After creating a read-only instance, the master instance does not support data recovery through the direct overwriting of instances using backup sets.

-   You cannot migrate data to read-only instances.

-   You cannot create or delete databases for read-only instances.

-   You cannot create or delete accounts for read-only instances.

-   You cannot authorize accounts or modify account passwords for read-only instances.


