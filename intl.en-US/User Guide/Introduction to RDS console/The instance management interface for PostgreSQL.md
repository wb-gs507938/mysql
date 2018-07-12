# The instance management interface for PostgreSQL {#concept_jwz_v3d_zdb .concept}

This document introduces the query information and executable operations supported by the RDS console for the PostgreSQL instance.

## Log on to the instance management interface {#section_yvj_2kd_zdb .section}

1.  Log on to the [RDS console](http://rds.console.aliyun.com/?spm=5176.doc26126.2.3.Kca631).
2.  Select the region where the target instance is located.
3.  Click the ID of the target instance or **Manage** in the corresponding **Operation** column to enter the instance management interface.

## Overview of the instance management interface {#section_ocr_fkd_zdb .section}

The following table lists the available information and actions that can be performed.

|Navigation pane|Area name|Description|Links of common operations|
|---------------|---------|-----------|--------------------------|
|Operation buttons at the top of the page| |This area allows you to migrate the database, restart, and back up an instance.| -   [Restart an instance](https://www.alibabacloud.com/help/doc-detail/26177.htm)
-   [Back up RDS data](https://www.alibabacloud.com/help/doc-detail/26206.htm)

 |
|Basic Information|Basic Information|This area allows you to view the the basic information of an instance. For example, the instance ID, region, and zone, instance type, intranet and the Internet addresses, intranet and the Internet port number.| |
|Instance Distribution|This area allows you to check the number of temporary instances under a master instance, and add temporary instances.| |
|Operating Status|This area allows you to view the running status, billing method, and creation time of an instance, release an instance, and renew a subscription instance.| -   [Release an instance](https://www.alibabacloud.com/help/doc-detail/26184.htm)
-   [Manually renew the subscription instance](https://www.alibabacloud.com/help/doc-detail/26118.htm)

 |
|Configuration Information|This area allows you to view the instance types, CPU, database type and version, database memory, and the maximum number of connections, and set the maintenance period.|[Configure the maintenance period](https://www.alibabacloud.com/help/doc-detail/26180.htm)|
|Resource Information|This area allows you to view the storage space and backup usage of an instance.| |
|Account Management|Account List|This area allows you to view the account information of the instance, create an initial account, and modify the account password.| -   [Create database and account](https://www.alibabacloud.com/help/doc-detail/26156.htm)
-   [Reset instance password](https://www.alibabacloud.com/help/doc-detail/26187.htm)

 |
|Database connection|Instance connection|This area allows you to view the network type, access mode, intranet and the Internet addresses, and port of an instance, change the network type, modify the connection address, and to apply for and release an intranet/Internet address.| -   [Set access mode](https://www.alibabacloud.com/help/doc-detail/26193.htm)
-   [Set network types](https://www.alibabacloud.com/help/doc-detail/26194.htm)
-   [Set intranet and Internet addresses](https://www.alibabacloud.com/help/doc-detail/26195.htm)

 |
|Monitoring and Alarms|Monitoring|This area allows you to view the monitoring information, such as the CPU and memory usage, disk space usage, and IOPS, and set the monitoring frequency.|[Set monitoring frequency](https://www.alibabacloud.com/help/doc-detail/26200.htm)|
|Alarms|This area allows you to view the status of monitoring items, cloud account, and the alarm contact, and set alarm rules.|[Set monitoring rules](https://www.alibabacloud.com/help/doc-detail/26201.htm)|
|Security Controls|Whitelist settings|This area allows you to view the whitelist information of an instance, modify the whitelist, and add a whitelist group.|[Set whitelist](https://www.alibabacloud.com/help/doc-detail/26198.htm)|
|Instance Availability|Availability Information|This area allows you to view the instance zone type, instance availability, data replication mode, and number of the master/slave database, and switch the master/slave instances.|[Switch master/slave instance](https://www.alibabacloud.com/help/doc-detail/26182.htm)|
|Zone Architecture Diagram|This area allows you to view the structural diagrams of the single zone and multi-zone instance.| |
|Log management|Error Log|This area allows you to view SQL statements that are incorrectly run in the database within a month.|[Log management](https://www.alibabacloud.com/help/doc-detail/26203.htm)|
|Slow SQL Log Details|This area allows you to view SQL statements whose running period exceeds one second in the database within a month, and deduplicate similar statements.|
|Backup and Recovery|Backup List|This area allows you to view the data backup list, and download the backup data.|[Download RDS data and log backup](https://www.alibabacloud.com/help/doc-detail/26208.htm)|
|Temporary instance|This area allows you to create temporary instances.|
|Archive List|This area allows you to view the detailed list of archived logs, and download the archived logs.| |
|Backup Settings|This area allows you to modify a backup policy and view the backup policies, such as the data backup retention time, backup cycle, and backup time.|[Back up RDS data](https://www.alibabacloud.com/help/doc-detail/26206.htm)|

 

