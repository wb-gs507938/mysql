# General introduction to product series {#concept_t5k_fkv_tdb .concept}

Currently, RDS instances are divided into three series: Basic Edition, High-availability Edition and Finance Edition.  Different series support different engine types and instance types. See [Instance type overview](intl.en-US/Product Introduction/Instance types/Instance type overview.md) for more information.

**Note:** Currently the Finance Edition is applicable only to the regions in China.

## Brief introductions {#section_s3n_3kv_tdb .section}

|Series|Introduction|Use case|
|------|------------|--------|
|Basic Edition|It uses the storage-computing isolated architecture and a single computing node, which realizes super high cost effectiveness.| -   Personal learning.
-   Micro websites.
-   Development and testing environments for and small and medium-sized enterprises.

 |
|High-availability Edition|It uses the classic high-availability architecture with one master node and one slave node. The ephemeral SSD storage provides the best and balanced performance.| -   Production databases of large enterprises.
-   Applications for the industries of Internet, Internet of things \(IoT\), retail e-commerce sales, logistics, game, and other industries.

 |

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
|Type configuration|Maximum 32-core 128 GB/2 TB|Maximum 60-core 470 GB/3 TB|
|[Set monitoring](../../../../intl.en-US/User Guide/Monitoring and Alarms/Set monitoring frequency.md) and [alarms](../../../../intl.en-US/User Guide/Monitoring and Alarms/Set monitoring rules.md)|Supported|Supported|
|[IP whitelist](../../../../intl.en-US/User Guide/Security management/Set whitelist.md)|Supported|Supported|
|Backup and recovery|Supported|Supported|
|[Parameter settings ](../../../../intl.en-US/User Guide/Instance management/Set instance parameters/Set parameters through RDS console.md)|Supported|Supported|
|[SSL](../../../../intl.en-US/User Guide/Security management/Set SSL encryption.md) and [TDE](../../../../intl.en-US/User Guide/Security management/Set Transparent Data Encryption.md)|Not supported|Supported \(Currently MySQL 5.7 does not support TDE\)|
|[Log management](../../../../intl.en-US/User Guide/Log management.md)|Not supported|Supported|
|Performance optimization|Not supported|Supported|
|[Read-only instance](../../../../intl.en-US/Quick Start for MySQL/Scale instances/Read-only instance/Introduction to read-only instance.md) \(Additional instances required\)|Not supported|Supported only by MySQL 5.6/5.7|
|[Read/write splitting](../../../../intl.en-US/User Guide/Read/write splitting/Introduction to read/write splitting.md)|Not supported|Supported only in MySQL 5.6|
|Built-in read/write splitting|Not supported|Not supported|
|[SQL audit](../../../../intl.en-US/User Guide/Security management/只有中国站.md)|Not supported|Supported \(Additional payment required\)|
|High-frequency monitoring|Not supported|Supported \(Additional payment required\)|

