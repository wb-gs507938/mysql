# Download RDS data and log backup {#concept_yjb_pn4_ydb .concept}

You can download RDS data backup files and log backup files that are not encrypted.

## Procedure {#section_lxw_cn4_ydb .section}

1.  Log on to the [RDS console](https://rds.console.aliyun.com/).
2.  Select the region where the target instance is located.
3.  Click the ID of the instance to visit the Basic Information page.
4.  Select **Backup and Recovery** in the left-side navigation pane.
5.  Do the following to download a data backup or a log backup:
    -   Download a data backup.

        1.  Select the **Backup List** tab.
        2.  Specify the time range.
        3.  Find the backup you want and cick **Download** in the **Action** column.

            **Note:** If the backup is used for data restoration, select the backup that is closest to the time for recovery.

        4.  In the Download Instance Backup File dialog box, select a download method.

            ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7966/6231_en-US.png)

            |Download method|Description|
            |---------------|-----------|
            |Download|Directly download the backup file through the Internet.|
            |Copy Intranet Address|If ECS and RDS are in the same region, you can log on to ECS and use the RDS intranet address to download the backup file. This method is faster and more secure.|
            |Copy Internet Address|You can copy the Internet address and use other tools to download the backup file.|

    -   Download a log backup.

        1.  Select the Binlog List tab.
        2.  Specify the time range.
        3.  Find the binlog you want and cick **Download** in the **Action** column.

            **Note:** If the binlog file is used for restoring data to an on-premise database, pay attention to the following:

            -   **Instance Number** of the binlog must be the same as **Instance Number** of the data backup.

            -   The binlog start time must be later than the data backup time and earlier than the restoration time.

        4.  In the Download Binary Log dialog box, select a download method.

            ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7966/6232_en-US.png)

            |Download method|Description|
            |---------------|-----------|
            |Download|Directly download the backup file through the Internet.|
            |Copy Intranet Address|If ECS and RDS are in the same region, you can log on to ECS and use the RDS intranet address to download the backup file. This method is faster and more secure.|
            |Copy Internet Address|You can copy the Internet address and use other tools to download the backup file.|


