# Limits {#concept_hb5_px2_vdb .concept}

To guarantee the stability and security of ApsaraDB for MySQL, certain limits to database and management properties apply.

|Items|Restrictions|
|-----|------------|
|Parameter modification|The [RDS console](https://rds.console.aliyun.com/) or API must be used to modify database parameters. But some parameters cannot be modified. For more information, see [Set parameters through RDS console](../../../../intl.en-US/User Guide/Instance management/Set instance parameters/Set parameters through RDS console.md#).|
|Root permission|The root or sa permission is not provided.|
|Backup| -   The command line or graphical interface can be used to perform logical backup.
-   For physical backup, the [RDS console](https://rds.console.aliyun.com/) or API must be used.

 |
|Restoration| -   The command line or graphical interface can be used to perform logical restoration.
-   For physical restoration, the [RDS console](https://rds.console.aliyun.com/) or API must be used.

 |
|Migration| -   The command line or graphical interface can be used to perform logical import.
-   You can use mysql command line tool or Data Transmission Service \(DTS\) to perform data migration.

 |
|MySQL storage engine| -   Currently only InnoDB and TokuDB are supported. The MyISAM engine has defects and may cause data loss. If you create MyISAM engine tables, they are automatically converted to InnoDB engine tables. For more information, see [Why does RDS for MySQL not support the MyISAM engine?](https://www.alibabacloud.com/help/doc-detail/52558.htm) 
-   The InnoDB storage engine is recommended for performance and security requirements.
-   The Memory engine is not supported. If you create Memory engine tables, they are automatically converted to InnoDB engine tables.

 |
|Replication|MySQL provides a dual-node cluster of master/slave MySQL replications architecture, so you do not need to build them manually. The slave instance in the architecture is invisible to you, and your application cannot access to the slave instance directly.|
|Restarting the RDS instance|Instance must be restarted through the [RDS console](https://rds.console.aliyun.com/) or API.|
|User, password, and database management|By default, you use the RDS console to perform user, password, and database management such as creating or deleting an instance, modifying privileges and changing password. MySQL also allows you to create a master account for finer-grained management controls.|
|Common account| -   Does not support custom authorization.
-   The account management and database management interfaces exist on the RDS console.
-   Instances that support common accounts also support master accounts.

 |
|Master account| -   Support custom authorization.
-   To manage accounts and databases, use SQL statements

 |
|Network settings|If a MySQL 5.5/5.6 instance is in a classic network and its [access mode](../../../../intl.en-US/User Guide/Network management/Set access mode.md) is safe connection mode, do not enable net.ipv4.tcp\_timestamps in SNAT mode.|

