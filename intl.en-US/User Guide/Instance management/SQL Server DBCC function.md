# SQL Server DBCC function {#concept_e5g_jmn_wdb .concept}

RDS SQL Server 2012 and later versions support some features of the Database Console Commands \(DBCC\). You only need to use the storage process sp\_rds\_dbcc\_trace to specify the trace flag that you want to enable. You can run `DBCC tracestatus(-1)` to check whether a trace flag is enabled.

Currently, RDS supports the following trace flags:

-   1222
-   1204
-   1117
-   1118
-   1211
-   1224
-   3604

To use DBCC, run the following command:

```
USE master
GO
--database engine edtion
SELECT SERVERPROPERTY('edition')
GO
--create database
CREATE DATABASE testdb
GO
DBCC tracestatus(-1)
exec sp_rds_dbcc_trace 1222,1
WAITFOR DELAY '00:00:10'
DBCC tracestatus(-1)
GO
```

