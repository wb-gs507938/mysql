# Use SQL commands to set parameters {#concept_wm4_44n_wdb .concept}

**Note:** The operation described in this document is applicable only to instances of RDS SQL Server 2012 and later versions. For the procedure of setting parameters for instances of other types and versions, see [Set parameters on the console](https://help.aliyun.com/document_detail/26179.html).

To set instance parameters, you only need to specify configuration options in the sp\_rds\_configure storage process. A prompt appears if the instance must be restarted to apply the parameter settings.

Currently, RDS only supports the following instance configurations:

-   fill factor \(%\)
-   max worker threads
-   cost threshold for parallelism
-   max degree of parallelism
-   min server memory \(MB\)
-   max server memory \(MB\)
-   blocked process threshold \(s\)

Run the following command to set instance parameters:

```
USE master
GO
--database engine edtion
SELECT SERVERPROPERTY('edition')
GO
--create database
CREATE DATABASE testdb
GO
SELECT * 
FROM sys.configurations
WHERE NAME = 'max degree of parallelism'
EXEC sp_rds_configure 'max degree of parallelism',0
WAITFOR DELAY '00:00:10'
SELECT * 
FROM sys.configurations
WHERE NAME = 'max degree of parallelism'
```

