# General introduction to product series {#concept_t5k_fkv_tdb .concept}

Currently, RDS instances are divided into four series: Basic Edition, High-availability Edition, Cluster Edition, and Finance Edition. Different series support different engine types and instance types. For more information, see [Instance type overview](intl.en-US/Product Introduction/Instance types/Instance type overview.md).

**Note:** Currently the Finance Edition is applicable only to regions in China.

## Brief introduction {#section_s3n_3kv_tdb .section}

|Series|Introduction|Use cases|
|------|------------|---------|
|Basic Edition|It uses the storage-computing-isolated architecture and a single computing node, realizing super high cost effectiveness. For more information, see [Basic Edition](intl.en-US/Product Introduction/Product editions/Basic Edition.md).| -   Personal learning
-   Small websites
-   Development and test environments for small- and medium-sized enterprises

 |
|High-availability Edition|It uses the classic high-availability architecture with one master node and one slave node. The ephemeral SSD storage provides the best and balanced performance.| -   Production databases of large-sized enterprises
-   Applications for Internet, Internet of things \(IoT\), retail e-commerce sales, logistics, gaming, and other industries

 |
|Cluster Edition|It applies to only SQL Server 2017 Enterprise and is developed based on AlwaysOn technology. It provides a master and a slave node, and supports up to seven read-only nodes that horizontally scale read capabilities. For more information, see [Cluster Edition \(AlwaysOn Edition\)](intl.en-US/Product Introduction/Product editions/Cluster Edition (AlwaysOn Edition).md).|Large- and medium-sized enterprises, such as online retail enterprises, automobile companies, and large ERP systems.|

## Feature differences {#section_gjb_nmv_tdb .section}

|Feature|Basic Edition|High-availability Edition|
|-------|-------------|-------------------------|
|Engine| -   MySQL 5.7
-   SQL Server 2012 Web, Enterprise
-   SQL Server 2016 Web

 | -   MySQL 5.5/5.6/5.7
-   SQL Server 2008 R2 Enterprise
-   SQL Server 2012 Standard, Enterprise
-   SQL Server 2016 Standard, Enterprise
-   PostgreSQL 9.4
-   PPAS 9.3

 |
|Number of nodes|1|2|
|Maximum configuration|32-core 128 GB/2 TB|60-core 470 GB/3 TB|
|[Set monitoring](../../../../intl.en-US/User Guide/Monitoring and Alarming/Set the monitoring frequency.md) and [alarms](../../../../intl.en-US/User Guide/Monitoring and Alarming/Set monitoring rules.md)|Supported|Supported|
|[IP whitelist](../../../../intl.en-US/User Guide/Security/Set a whitelist.md)|Supported|Supported|
|Backup and recovery|Supported|Supported|
|[Parameter settings ](../../../../intl.en-US/User Guide/Instance management/Set instance parameters/Set parameters through the RDS console.md)|Supported|Supported|
|[SSL](../../../../intl.en-US/User Guide/Security/Set SSL encryption.md) and [TDE](../../../../intl.en-US/User Guide/Security/Set TDE.md)|Not supported|Supported \(Currently MySQL 5.7 does not support TDE\)|
|[Log management](../../../../intl.en-US/User Guide/Log management.md)|Not supported|Supported|
|Performance optimization|Not supported|Supported|
|[Read-only instance](../../../../intl.en-US/Quick Start for MySQL/Scale instances/Read-only instance/Introduction to read-only instances.md) \(Additional instances required\)|Not supported|Supported only by MySQL 5.6/5.7|
|[Read/write splitting](../../../../intl.en-US/User Guide/Read__write splitting/Introduction to read__write splitting.md)|Not supported|Supported only by MySQL 5.6|
|Built-in read/write splitting|Not supported|Not supported|
|[SQL audit](../../../../intl.en-US/User Guide/Security/SQL audit.md)|Not supported|Supported \(Additional payment required\)|
|High-frequency monitoring|Not supported|Supported \(Additional payment required\)|

