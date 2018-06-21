# SQL Server DBCC功能 {#concept_e5g_jmn_wdb .concept}

RDS SQL Server 2012及以上版本支持DBCC的部分功能，您只需要使用存储过程`sp_rds_dbcc_trace`指定需要打开的跟踪标记即可。另外，您可以使用`DBCC tracestatus(-1)`查看跟踪标记是否被打开。

目前，RDS支持的跟踪标记有：

-   1222
-   1204
-   1117
-   1118
-   1211
-   1224
-   3604

执行如下命令，即可使用DBCC功能：

1.  ```
USE
            master
```

2.  `GO`
3.  `--database engine edtion`
4.  ```
SELECT
            SERVERPROPERTY('edition')
```

5.  `GO`
6.  ```
--create
            database
```

7.  ```
CREATE DATABASE
            testdb
```

8.  `GO`
9.  10. ```
DBCC
            tracestatus(-1)
```

11. 12. ```
exec
            sp_rds_dbcc_trace 1222,1
```

13. 14. ```
WAITFOR DELAY
            '00:00:10'
```

15. 16. ```
DBCC
            tracestatus(-1)
```

17. `GO`

