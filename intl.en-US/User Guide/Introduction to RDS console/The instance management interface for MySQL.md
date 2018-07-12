# The instance management interface for MySQL {#concept_oqj_nhh_wdb .concept}

This document introduces the query information and executable operations supported by the RDS console for a MySQL instance.

## Log on to the instance management interface {#section_qcs_phh_wdb .section}

1.  Log on to the [RDS console](http://rds.console.aliyun.com/?spm=5176.doc26126.2.3.Kca631).
2.  Select the region where the target instance is located.
3.  Click the ID of the target instance or **Manage** in the corresponding **Operation** column to enter the instance management interface.

## Overview of instance management interface {#section_th2_fdd_zdb .section}

The following table lists the query information and executable operations supported by the RDS console for MySQL instance. As MySQL instances of different versions support different operations, information displayed on the console may vary accordingly. See the actual interface when using this document.

|**Navigation pane**|**Block name**|**Description**|**Links of common operations**|
|Operation buttons at the top of the page| |You can migrate the database, and restart or back up an instance.| -   [Restart instance](https://www.alibabacloud.com/help/doc-detail/26177.htm)
-   [Back up RDS data](https://www.alibabacloud.com/help/doc-detail/26206.htm)

 |
|Basic Information|Basic Information|You can view the basic information of an instance. For example, the instance ID, region, and zone, instance type, intranet and Internet addresses, intranet and Internet ports, and perform migration across zones.|[Instance migration across zones](https://www.alibabacloud.com/help/doc-detail/26181.htm)|
|Instance Distribution|You can query the number of read-only and temporary instances under the primary instance, and the operation of adding read-only instances, adding temporary instances and so on.|[Create a read-only instance](https://www.alibabacloud.com/help/doc-detail/56991.htm)|
|Operating Status|You can view the running status, billing method, and creation time of an instance, and release an instance, renew a subscription instance and so on.| -   [Release an instance](https://www.alibabacloud.com/help/doc-detail/26184.htm)
-   [Manually renew a subscription instance](https://www.alibabacloud.com/help/doc-detail/26118.htm)

 |
|Configuration Information|You can view the instance types, CPU, database type and version, database memory, and the maximum number of connections, and upgrade the database version, set the maintenance period and so on.| -   [Upgrade database](https://www.alibabacloud.com/help/doc-detail/35363.htm)
-   [Configure the maintenance period](https://www.alibabacloud.com/help/doc-detail/26180.htm)

 |
|Resource Information|You can view the storage space and backup usage of an instance.| |
|Account Management|Account List| You can do the following: View all accounts under an instance; Create accounts, master account, or initial account; Change the account password, delete an account, and modify the account permissions.| -   [Create account](https://www.alibabacloud.com/help/doc-detail/26186.htm)
-   [Create account and database for MySQL 5.7 High-availability Edition/5.5/5.6 instances](https://www.alibabacloud.com/help/doc-detail/26129.htm)
-   [Create account and database for MySQL 5.7 Basic Edition](https://www.alibabacloud.com/help/doc-detail/49015.htm)
-   [Create master account](https://www.alibabacloud.com/help/doc-detail/26130.htm)
-   [Reset instance password](https://www.alibabacloud.com/help/doc-detail/26187.htm)
-   [Change account permissions](https://www.alibabacloud.com/help/doc-detail/26188.htm)

 |
|Service Account Privileges|When an Alibaba Cloud engineer provides technical support, you must authorize the engineer’s service account to view or modify the instance configurations and view the table structure, index, and SQL statements.|[Authorize a service account](https://www.alibabacloud.com/help/doc-detail/35152.htm)|
|Database Management| | You can view the databases information under an instance, and create and delete databases.| -   [Create account and database for MySQL 5.7 High-availability Edition/5.5/5.6 instances](https://www.alibabacloud.com/help/doc-detail/26129.htm)
-   [Create account and database for MySQL 5.7 Basic Edition](https://www.alibabacloud.com/help/doc-detail/49015.htm)
-   [Delete database](https://www.alibabacloud.com/help/doc-detail/26191.htm)

 |
|Database Connection|Instance Connection|You can view the network type, access mode, intranet address, and port of an instance, change the network type, modify the connection address, and to apply for and release an intranet/Internet address.| -   [Set access mode](https://www.alibabacloud.com/help/doc-detail/26193.htm)
-   [Set network type](https://www.alibabacloud.com/help/doc-detail/26194.htm)
-   [Set intranet and the Internet addresses](https://www.alibabacloud.com/help/doc-detail/26195.htm)

 |
|Monitoring and Alarms|Monitoring|You can view the monitoring information, such as the CPU and memory usage, disk space usage, and IOPS, and set the monitoring frequency.|[Set monitoring frequency](https://www.alibabacloud.com/help/doc-detail/26200.htm)|
|Alarms|You can set the alarm rules and view the status of monitoring items and the alarm contact.|[Set monitoring rules](https://www.alibabacloud.com/help/doc-detail/26201.htm)|
|Security Controls|Whitelist settings|You can view the whitelist information of an instance, modify the whitelist, and add a whitelist group.|[Set whitelist](https://www.alibabacloud.com/help/doc-detail/26198.htm)|
|SSL|You can view an SSL certificate, set SSL, and download a certificate.|[Set SSL encryption](https://www.alibabacloud.com/help/doc-detail/32474.htm)|
|TDE|You can view the status of Transparent Data Encryption \(TDE\) and activate the TDE.|[Set Transparent Data Encryption](https://www.alibabacloud.com/help/doc-detail/33510.htm)|
|Instance Availability|Availability Information|You can view the instance zone type, instance availability, data replication mode, and ID of the master/slave node, switch the master/slave instances, and modify the data replication mode.| -   [Switch master/slave instance](https://www.alibabacloud.com/help/doc-detail/26182.htm)
-   [Modify the data replication mode](https://www.alibabacloud.com/help/doc-detail/26183.htm)

 |
|Zone Architecture Diagram|You can view the structural diagrams of a single zone and multi-zone instance.| |
|Log Management|Error Log|You can view SQL statements that are incorrectly executed in the database within a month.|[Log management](https://www.alibabacloud.com/help/doc-detail/26203.htm)|
|Slow SQL Log Details|You can view SQL statements whose execution period exceeds one second in the database within a month, and deduplicate similar statements.|
|Slow SQL Log Summary|Collects SQL statements whose execution period exceeds one second in the database within a month, provides the analysis report for slow query logs, and allows you to download the statistics list.|
|Backup and Recovery|Backup List|You can view the data backup list, recover data to the master instance, and delete and download the backup data.| -   [Recover data to the master instance through a temporary instance](https://www.alibabacloud.com/help/doc-detail/50603.htm)
-   [Download RDS data and log backup](https://www.alibabacloud.com/help/doc-detail/26208.htm)

 |
|Binlog List|You can view and download binlog files.|
|Temporary Instance|You can create temporary instances which can be used to restore the lost data.|
|Backup Settings|You can modify a backup policy and view the backup policies, such as the data backup retention time, backup cycle, and backup time.|[Back up RDS data](https://www.alibabacloud.com/help/doc-detail/26206.htm)|
|Parameter Settings|Modifiable Parameters|You can view the parameter values of an instance, modify the parameter values, and import and export the parameters.|[Set parameters through RDS console](https://www.alibabacloud.com/help/doc-detail/26179.htm)|
|Modification History|You can view parameter modification records.| |

