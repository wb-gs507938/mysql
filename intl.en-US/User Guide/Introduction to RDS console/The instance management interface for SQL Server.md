# The instance management interface for SQL Server {#concept_hr3_5hd_zdb .concept}

This document introduces the query information and executable operations supported by the RDS console for an SQL Server instance.

## Log on to the instance management interface {#section_cmz_m3d_zdb .section}

1.  Log on to the [RDS console](http://rds.console.aliyun.com/?spm=5176.doc26126.2.3.Kca631).
2.  Select the region where the target instance is located.
3.  Click the ID of the target instance or **Manage** in the corresponding **Operation** column to enter the instance management interface.

## Overview of instance management interface {#section_f5h_43d_zdb .section}

The following table lists the available information and actions that can be performed. The actual interface may vary slightly with the SQL Server version.

|Navigation pane|Block name|Description|Links of common operations|
|---------------|----------|-----------|--------------------------|
|Operating area at the top| |Allows you to migrate the database, restart, and back up an instance.| -   [Restart instance](https://www.alibabacloud.com/help/doc-detail/26177.htm)
-   [Back up RDS data](https://www.alibabacloud.com/help/doc-detail/26206.htm)

 |
|Basic Information|Basic Information|Allows you to view the basic information of an instance. For example, the instance ID, region, and zone, instance type, intranet, and Internet addresses, intranet, and Internet ports, and perform migration across zones.|[Instance migration across zones](https://www.alibabacloud.com/help/doc-detail/26181.htm)|
|Instance Distribution|Allows you to check the number of temporary instances under the master instance and add a temporary instance.| |
|Operating Status|Allows you to view the running status, billing method, and creation time of an instance, release an instance, and renew a subscription instance.| -   [Release an instance](https://www.alibabacloud.com/help/doc-detail/26184.htm)
-   [Manually renew the subscription instance](https://www.alibabacloud.com/help/doc-detail/26118.htm)

 |
|Configuration Information|Allows you to view the instance types, CPU, database type and version, database memory, and the maximum number of connections, and set the maintenance period.| -   [Configure the maintenance period](https://www.alibabacloud.com/help/doc-detail/26180.htm)

 |
|Resource Information|Allows you to view the storage space and backup usage of an instance.| |
|Account Management|Account List|Allows you to do the following: View all accounts under an instance; Create accounts, master account, or initial account; Change the account password, delete an account, and modify the account permissions.| -   [Create database and account for SQL Server 2008 R2](https://www.alibabacloud.com/help/doc-detail/26145.htm)
-   [Create database and account for SQL Server 2012 and 2016](https://www.alibabacloud.com/help/doc-detail/43164.htm)
-   [Reset instance password](https://www.alibabacloud.com/help/doc-detail/26187.htm)
-   [Change account permissions](https://www.alibabacloud.com/help/doc-detail/26188.htm)

 |
|Service Account Privileges|When an Alibaba Cloud engineer provides technical support, you must authorize the engineer’s service account to view or modify instance configurations and view the table structure, index, and SQL statements.|[Authorize a service account](https://www.alibabacloud.com/help/doc-detail/35152.htm)|
|Database Management| |Allows you to view the databases information under an instance, create, and delete a database.| -   [Create database and account for SQL Server 2008 R2](https://www.alibabacloud.com/help/doc-detail/26145.htm)
-   [Create database and account for SQL Server 2012 and 2016](https://www.alibabacloud.com/help/doc-detail/43164.htm)
-   [Delete database](https://www.alibabacloud.com/help/doc-detail/26191.htm)

 |
|Database Connection|Instance Connection|Allows you to view the network type, access mode, intranet and Internet addresses, intranet and Internet ports, and server name of an instance, change the network type, modify the connection address, and to apply for and release an intranet/Internet address.| -   [Set access mode](https://www.alibabacloud.com/help/doc-detail/26193.htm)
-   [Set network type](https://www.alibabacloud.com/help/doc-detail/26194.htm)
-   [Set intranet and the Internet addresses](https://www.alibabacloud.com/help/doc-detail/26195.htm)

 |
|Monitoring and Alarms|Monitoring|Allows you to view the monitoring information, such as the CPU and memory usage, disk space usage, and IOPS, and set the monitoring frequency.|[Set monitoring frequency](https://www.alibabacloud.com/help/doc-detail/26200.htm)|
|Alarms|Allows you to view the status of monitoring items and cloud account alert contact, and set the alarm rules.|[Set alarm rules](https://www.alibabacloud.com/help/doc-detail/26201.htm)|
|Security Controls|Whitelist Settings|Allows you to view the whitelist information of an instance, modify the whitelist, and add a whitelist group.|[Set whitelist](https://www.alibabacloud.com/help/doc-detail/26198.htm)|
|SSL|Allows you to view an SSL certificate, set SSL, and download a certificate.|[Set SSL encryption](https://www.alibabacloud.com/help/doc-detail/32474.htm)|
|TDE|Allows you to view the status of Transparent Data Encryption \(TDE\) and activate the TDE.|[Set Transparent Data Encryption](https://www.alibabacloud.com/help/doc-detail/33510.htm)|
|Instance Availability|Availability Information|Allows you to view the instance zone type, instance availability, data replication mode, and number of the master/slave database, and switch the master/slave instances.|[Switch master/slave instance](https://www.alibabacloud.com/help/doc-detail/26182.htm)|
|Zone Architecture Diagram|Allows you to view the structural diagrams of the single zone and multi-zone instance.| |
|Log Management|Error Log|Allows you to view SQL statements that are incorrectly executed in the database within a month.|[Log management](https://www.alibabacloud.com/help/doc-detail/26203.htm)|
|Slow SQL Log Summary|Collects SQL statements whose execution period exceeds one second in the database within a month, provides the analysis report for slow query logs, and allows you to download the statistics list.|
|Backup and Recovery|Backup List|Allows you to view the data backup list, and recover data to the master instance.| |
|Temporary Instance|Allows you to create temporary instances.|
|Backup Settings|Allows you to view the backup policies, such as the data backup retention time, backup cycle, and backup time, and modify a backup policy.|[Back up RDS data](https://www.alibabacloud.com/help/doc-detail/26206.htm)|
|Parameter Settings|Modifiable Parameters|Allows you to view the parameter values of an instance, modify the parameter values, and import and export the parameters.|[Set parameters through RDS console](https://www.alibabacloud.com/help/doc-detail/26179.htm)|
|Modification History|Allows you to view parameter modification records.| |

