# Download data and log backup files {#concept_yjb_pn4_ydb .concept}

You can download data and log backup files that are not encrypted.

## Procedure {#section_lxw_cn4_ydb .section}

1.  Log on to the [RDS console](https://rds.console.aliyun.com/).
2.  Select the region where the target instance is located.
3.  Click the ID of the instance to visit the Basic Information page.
4.  Click **Backup and Recovery** in the left-side navigation pane.
5.  Do as follows to download a data or log backup file:
    -   To download data backups, click the **Backup List** tab.
    -   To download log backups:
        1.  Click the Binlog List tab for MySQL and SQL Server.
        2.  Click the Archive List tab for PostgreSQL and PPAS.
    -   Specify a time range.
    -   Find the data backup or log backup you want and click **Download** in the **Action** column.

        **Note:** If the binlog file is used for restoring data to an on-premise database, pay attention to the following:

        -   **Instance Number** of the binlog must be the same as **Instance Number** of the data backup.
        -   The binlog backup start time must be later than the data backup time and earlier than the restoration time.
    -   In the Download Instance Backup File dialog box, select a download method.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7966/15366349806231_en-US.png)

        |Download method|Description|
        |---------------|-----------|
        |Download|Directly download the backup file through the Internet.|
        |Copy Intranet Address|If ECS and RDS are in the same region, you can log on to ECS and use the RDS intranet IP address to download the backup file. This method is faster and more secure.|
        |Copy Internet Address|You can copy the Internet IP address and use other tools to download the backup file.|


