# SQL audit {#concept_njf_cr4_ydb .concept}

The SQL audit function allows you to view SQL details and periodically audit RDS instances.

## Attentions {#section_a2j_4ng_g2b .section}

-   Certain RDS instance types do not support the SQL audit function.
-   The SQL audit function does not affect instance performance.
-   SQL audit logs are kept for 30 days.
-   Exported SQL audit files are kept for 2 days.
-   The SQL audit function is disabled by default. Enabling this function incurs charges. For more information, see [Pricing](https://www.alibabacloud.com/product/apsaradb-for-rds#pricing).

## Differences between SQL audit logs and binlog {#section_uyq_kr4_ydb .section}

For MySQL instances, you can use SQL audit logs or binlog to view incremental data. Differences between them are as follows:

-   SQL audit logs: Similar to MySQL audit logs, SQL audit logs collect information about all DML and DDL operations. The information is obtained through network protocol analysis. The SQL audit function does not parse actual parameter values, and a small number of records may be lost when the SQL query volume is large. Therefore, using SQL audit logs to collect incremental data may be inaccurate.
-   Binlog: Binary logs accurately record all ADD, DELETE, and MODIFY operations and can accurately recover incremental data. Binary logs are stored in the instance temporarily. The system regularly transfers them to OSS and they are stored on OSS for 7 days. The system cannot save binlog files where data is being written, so certain binary logs are not uploaded when you click **Upload Binlog** on the RDS console.

    Therefore, binary logs accurately record incremental data, but you cannot obtain real-time binary logs.


## Enable SQL audit {#section_bwj_nr4_ydb .section}

1.  Log on to the [RDS console](https://rdsnew.console.aliyun.com).
2.  Select the region where the target instance is located.
3.  Click the ID of the target instance to go to the **Basic Information** page.
4.  In the left-side navigation pane, click **Security**.
5.  Click the **SQL Audit** tab and click **Enable now**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7947/15440599034138_en-US.png)

6.  In the displayed dialog box, click **Confirm**.

## Disable SQL audit {#section_o4j_sr4_ydb .section}

To save costs, you can disable the SQL audit function when you do not need it.

**Note:** Disabling the SQL audit function deletes all SQL audit logs. Export logs before disabling the function.

1.  Log on to the [RDS console](https://rdsnew.console.aliyun.com).
2.  Select the region where the target instance is located.
3.  Click the ID of the target instance to go to the **Basic Information** page.
4.  In the left-side navigation pane, click **Security**.
5.  Click the **SQL Audit** tab. Click **Export File** and then click **Confirm**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7947/15440599046540_en-US.png)

6.  Download the SQL audit file and put it in a local directory.
7.  Click **Disable SQL Audit Log** and then click **Confirm**.

