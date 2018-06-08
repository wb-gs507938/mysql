# 使用SQL命令设置参数 {#concept_wm4_44n_wdb .concept}

**说明：** 本文仅适用于RDS SQL Server 2012及以上版本的实例。关于其它类型和版本的实例设置参数的步骤，请参见[使用控制台设置参数](cn.zh-CN/用户指南/实例管理/设置实例参数/使用控制台设置参数.md#)。

若您需要设置实例的参数，您只需要使用存储过程sp\_rds\_configure指定配置选项即可，若要设置的参数需要重启实例，系统会有相应的提示。

目前，RDS仅支持对实例进行如下配置：

-   fill factor \(%\)
-   max worker threads
-   cost threshold for parallelism
-   max degree of parallelism
-   min server memory \(MB\)
-   max server memory \(MB\)
-   blocked process threshold \(s\)

执行如下命令，即可设置实例参数：

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

