# Set monitoring frequency {#concept_ug4_x5p_wdb .concept}

## Background information {#section_uxl_cvp_wdb .section}

The RDS console provides abundant performance metrics for users to conveniently view and know the running status of the instances. You can use the RDS console to set the monitoring frequency, view monitoring data of a specific instance, create monitoring views, and compare instances of the same type under the same account.

**Before May 15, 2018, two monitoring frequencies were available:**

-   once per 60 seconds \(monitoring period: 30 days\)

-   once per 300 seconds \(monitoring period: 30 days\)


However, the minute-level monitoring frequencies were not enough for certain users and maintenancen personnel. Therefore, since May 15, 2018, RDS has introduced the second-level monitoring frequency. This faciliates problem locating and improves customer satisfaction.

-   **once per 5 seconds \(monitoring period: 7 days\) The monitoring frequency beyond 7 days is once per minute.**

-   The detailed monitoring policies are described in the following table.

    |Instance type|once per 5 seconds|once per minute \(60 seconds\)|once per 5 minutes \(300 seconds\)|
    |-------------|------------------|------------------------------|----------------------------------|
    |Basic Edition|Not supported|Supported for free|Default configuration|
    |High Availability or Finance Edition: Memory < 8 GB|Not supported|Supported for free|Default configuration|
    |High Availability or Finance Edition: Memory \>= 8 GB|Supported \(Not free\)|Default configuration|Supported for free|


## Restrictions {#section_t54_fvp_wdb .section}

-   You can configure second-level monitoring for instances that meet the following conditions:

    -   The instance is located in these regions: China \(Hangzhou\), China \(Shanghai\), China \(Qingdao\), China \(Beijing\), China \(Shenzhen\)
    -   The instance is an RDS for MySQL instance.
    -   The instance storage type is local SSDs.
    -   The instance memory is 8 GB or more.
-   All engines \(MySQL, SQL Server, PG, PPAS\) and database versions support these monitoring frequencies: once per 60 seconds; once per 300 seconds.


## Procedure {#section_vrd_hvp_wdb .section}

1.  Log on to the [RDS console](https://rds.console.aliyun.com/).
2.  Select the region where the target instance is located.
3.  Click the ID of the target instance to enter the Basic Information page.
4.  Select **Monitoring and Alarms** in the left-side navigation pane.

    **Note:** Different types of databases support different metrics. For more information, see **List of monitoring items** at the end of this article.

5.  Select the **Monitoring** tab page.
6.  Click **Set Monitoring Frequency**.
7.  Select the monitoring frequency in the Set Monitoring Frequency dialog box and click **OK**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7952/3104_en-US.png)

8.  If a Confirm dialog box is displayed, click **OK**.
9.  On the Monitoring page, you can also do the following:

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7952/3107_en-US.png)

    **Interface description:**

    |No.|Description|
    |---|-----------|
    |1|Select the monitoring type.|
    |2|Select the monitoring period.|
    |3|Select the monitoring frequency.|
    |4|Refresh the monitoring result.|
    |5|View monitoring results.|
    |6|Select monitoring items.|


## List of monitoring items {#section_mfg_4vp_wdb .section}

**RDS for MySQL**

|Monitoring items|Description|
|----------------|-----------|
|Disk Space|Disk space usage of the instance, including:-   Overall usage of the disk space
-   Data space usage
-   Log space usage
-   Temporary file space usage
-   System file space usage

Unit: MByte

|
|IOPS|Number of I/O request times of the instance per second. Unit: time/second|
|Total Connections|Total number of current connections, including the number of active connections and total connections.|
|CPU and Memory Usage|Usage of CPU and memory of the instance \(not including memory used by the operating system\).|
|Network Traffic|Incoming/outgoing traffic of an instance per second. Unit: KByte|
|QPS/TPS|The number of SQL statements run and transactions processed per second.|
|InnoDB buffer pool|InnoDB buffer pool read hit rate, utilization rate, and percentage of dirty data blocks.|
|InnoDB Read/Write Volume|Average InnoDB data reads and writes per second. Unit: KByte|
|The number of InnoDB reads and writes per second.|The number of Read and Write times per second of InnoDB.|
|InnoDB log|The number of InnoDB physical writes to the log file, log write requests, and FSYNC writes to the log file.|
|Temporary tables|The number of temporary tables created automatically on the hard disk when the database runs the SQL statement.|
|MyISAM Key Buffer|Average per-second Key Buffer read hit rate, write hit rate and usage of MyISAM.|
|MyISAM read and write times|Times of MyISAM read and write from/to the buffer pool and from/to the hard disk per second.|
|COMDML|The number of statements run for the database per second. The statements include:-   Insert
-   Delete
-   Insert\_Select
-   Replace
-   Replace\_Select
-   Select
-   Update

|
|ROWDML|The number of operations performed on InnoDB, including:-   The number of physical writes to the log file per second
-   The number of rows read in InnoDB tables per second
-   The number of rows updated, deleted, and inserted in InnoDB tables per second

|

**RDS for SQL Server**

|Monitoring item|Description|
|---------------|-----------|
|Disk Space|Disk space usage of the instance, including:-   Overall usage of the disk space
-   Data space usage
-   Log space usage
-   Temporary file space usage
-   System file space usage

Unit: MByte

|
|IOPS|I/O request times of the instance per second. Unit: time/second|
|Connections|Total number of current connections, including the number of active connections and total connections.|
|CPU usage|CPU usage \(including CPU used by the operating system\) of the instance.|
|Network Traffic|Incoming/outgoing traffic of an instance per second. Unit: KByte|
|TPS|The number of transactions processed per second.|
|QPS|The number of SQL statements run per second.|
|Cache hit rate|Read hit rate of the buffer pool.|
|Average full table scans per second|Average number of full table scans per second.|
|SQL compilations per second|The number of compiled SQL statements per second.|
|Page writes of the checking point per second|The number of page writes of the checking point in the instance per second.|
|logons per second|The number of logons per second.|
|Lock timeouts per second|The number of lock timeouts per second.|
|Deadlocks per second|The number of deadlocks in the instance per second.|
|Lock waits per second|The number of lock waits per second.|

**RDS for PostgreSQL**

|Monitoring item|Description|
|---------------|-----------|
|Disk Space|Usage of the instance disk space. Unit: MByte|
|IOPS|The number of I/O requests of the data disk and log disk in the instance per second. Unit: time/second|

**RDS for PPAS**

|Monitoring item|Description|
|---------------|-----------|
|Disk Space|Usage of the instance disk space. Unit: MByte|
|IOPS|The number of I/O requests of the data disk and log disk in the instance per second. Unit: time/second|

