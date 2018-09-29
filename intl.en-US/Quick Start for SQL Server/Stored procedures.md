# Stored procedures {#concept_xpp_gg3_v2b .concept}

-   [Copy a database in an instance](#)
-   [Bring a database online](#)
-   [Set global database privileges](#)
-   [Delete a database](#)
-   [Set change tracking](#)
-   [Enable change data capture](#)
-   [Disable change data capture](#)
-   [Configure instance parameters](#)
-   [Add a linked server](#)
-   [Set a trace flag](#)
-   [Rename a database](#)

## Copy a database in the instance {#section_os1_3g3_v2b .section}

**T-SQL**

sp\_rds\_copy\_database

**Supported editions:**

-   High-Availability Edition
-   Basic Edition

**Description**

Copies a database in an instance.

**Note:** The remaining storage capacity of the instance must be at least 1.3 times the database size.

**Method**

```
EXEC sp_rds_copy_database 'testdb','testdb_copy'
```

-   The first parameter represents the source database.
-   The second parameter represents the target database.

## Bring a database online {#section_xzd_nr3_v2b .section}

**T-SQL**

sp\_rds\_set\_db\_online

**Supported editions:**

-   High-availability Edition
-   Basic Edition

**Description**

After you bring a database offline, you cannot directly bring it online by running the ALTER DATABASE statement. Use this stored procedure to bring a database online.

**Method**

```
EXEC sp_rds_set_db_online 'db'
```

The parameter represents the database to be brought online.

## Set global database privileges {#section_zxg_gs3_v2b .section}

**T-SQL**

sp\_rds\_set\_all\_db\_privileges

**Supported editions:**

-   High-Availability Edition
-   Basic Edition

**Description**

Grants the privileges of all or multiple databases to a user.

**Note:** Your current database privileges must be higher or equal to the privileges you want to grant.

**Method**

```
sp_rds_set_all_db_privileges 'user','db_owner','db1,db2...'
```

-   The first parameter represents the user that you want to grant privileges to.
-   The second parameter represents the database role to be granted to the user.
-   The third parameter represents the databases. You can specify one or more databases, and separate multiple database databases with commas \(,\). \(If the parameter is left blank, it indicates all user databases.\)

## Delete a database {#section_ycd_4s3_v2b .section}

**T-SQL**

sp\_rds\_drop\_database

**Supported editions:**

High-Availability Edition

**Note:** The Basic Edition currently does not support this stored procedure. For the Basic Edition, you can delete a database by running `DROP DATABASE db`.

**Description**

Delete a database from the instance. Dependent objects will be deleted when a database is deleted. The High-Availability Edition automatically deletes the mirror and terminates the database connection.

**Method**

```
EXEC sp_rds_drop_database 'db'
```

The parameter represents the database to be deleted.

## Set change tracking {#section_mtt_bt3_v2b .section}

**T-SQL**

sp\_rds\_change\_tracking

**Supported editions:**

High-Availability Edition

**Description**

Sets change tracking for the database.

**Method**

```
EXEC sp_rds_change_tracking 'db',1
```

-   The first parameter represents the database name.
-   The second parameter indicates whether change tracking is enabled.
    -   1: Enable.
    -   0: Disable.

## Enable change data capture \(CDC\) {#section_vkq_rt3_v2b .section}

**T-SQL**

sp\_rds\_cdc\_enable\_db

**Supported editions:**

High-Availability Edition

**Note:** If mirroring exists, this stored procedure also removes the availability group. In this case, this stored procedure is not recommended.

**Description**

Enables change data capture.

**Method**

```

USE db
GO
sp_rds_cdc_disable_db
```

## Disables change data capture {#section_pf3_453_v2b .section}

**T-SQL**

sp\_rds\_cdc\_disable\_db

**Supported editions:**

High-Availability Edition

**Note:** If mirroring exists, this stored procedure also removes the availability group. In this case, this stored procedure is not recommended.

**Description**

Disables change data capture.

**Method**

```

USE db
GO
sp_rds_cdc_disable_db
```

## Configure instance parameters {#section_exf_v53_v2b .section}

**T-SQL**

sp\_rds\_configure

**Supported editions:**

-   High-availability Edition
-   Basic Edition

**Description**

Sets instance parameters. If your instance has primary and secondary nodes, the configuration is automatically synchronized from the primary node to the secondary node.

Parameters currently supported:

-   fill factor \(%\)
-   maximum worker threads
-   cost threshold for parallelism
-   max degree of parallelism
-   min server memory \(MB\)
-   max server memory \(MB\)
-   blocked process threshold \(s\)

**Method**

```

EXEC sp_rds_configure 'max degree of parallelism',4
```

-   The first parameter represents the instance parameters to be set.
-   The second parameter represents the instance parameter value.

## Add a linked server {#section_ckn_jv3_v2b .section}

**T-SQL**

sp\_rds\_add\_linked\_server

**Supported editions:**

-   SQL Server 2012/2016 Standard Edition High-Availability series
-   SQL Server 2012/2016 Enterprise Edition High-Availability series

**Description**

Adds a linked server to the instance. Supports distributed transactions. The linked server created for both the primary and secondary nodes. If a switchover occurs, you do not need to add the link server again.

**Method**

```

DECLARE
@linked_server_name sysname = N'yangzhao_slb',
@data_source sysname = N'****.sqlserver.rds.aliyuncs.com,3888', --style: 10.1.10.1,1433
@user_name sysname = N'ay15' ,
@password nvarchar(128) = N'******',
@source_user_name sysname = N'test',
@source_password nvarchar(128) = N'******',
@link_server_options xml
= N'
            <rds_linked_server>
                <config option="data access">true</config>
                <config option="rpc">true</config>
                <config option="rpc out">true</config>
            </rds_linked_server>
'

EXEC sp_rds_add_linked_server
@linked_server_name,
@data_source,
@user_name,
@password,
@source_user_name,
@source_password,
@link_server_options

```

## Set a trace flag {#section_xxq_5v3_v2b .section}

**T-SQL statements**

sp\_rds\_dbcc\_trace

**Supported editions:**

-   High-availability Edition
-   Basic Edition

**Description**

Sets trace flags for the instance. Only partial trace flags are currently supported. If your instance has primary and secondary nodes, the trace flags are automatically synchronized from the primary node to the secondary node.

**Method**

```
EXEC sp_rds_dbcc_trace '1222',1/0
```

-   The first parameter represents the trace flag.
-   The second parameter indicates whether the trace flag is enabled or disabled.
    -   1: Enable.
    -   0: Disable.

## Rename a database {#section_llf_fw3_v2b .section}

**T-SQL**

sp\_rds\_rename\_database

**Supported editions:**

Basic Edition

**Description**

Renames a database.

**Note:** This stored proceudre does not rename the physical database file.

**Method**

```
EXEC sp_rds_rename_database 'db','new_db'
```

-   The first parameter represents the database to be renamed.
-   The second parameter represents the new name of the database.

