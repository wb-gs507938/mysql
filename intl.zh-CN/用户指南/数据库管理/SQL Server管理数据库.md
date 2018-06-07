# SQL Server管理数据库 {#concept_q1d_qmq_wdb .concept}

本文将介绍如何使用SQL命令在RDS SQL Server实例中创建和管理数据库。

**说明：** 本文仅适用于RDS SQL Server 2012及以上版本的实例。

## 创建数据库 {#section_u3p_gnq_wdb .section}

执行如下命令，创建数据库：

**说明：** RDS创建数据库时会产生默认路径，请您不要指定任何文件的路径。

```
CREATE DATABASE TestDb
```

## 更改数据库 {#section_qz3_jnq_wdb .section}

您可以更改数据库的大部分属性，但请不要执行如下操作：

-   不能移动到错误的文件路径。

    例如，若您执行如下命令并指定了错误的文件路径：

    ```
    ALTER DATABASE [TestDb]MODIFY FILE( NAME = N'TestDb', FILENAME = N'E:\KKKK\DDD\DATA\TestDb.mdf' )
    ```

    则系统会返回如下错误信息：

    ```
    Msg 50000, Level 16, State 1, Procedure ******, Line 152
    The file path [ 
    E:\KKKK\DDD\DATA\TestDb.mdf ] is invalid,please specify correct path folder [ E:\mmm\gggg\ ].
    Msg 3609, Level 16, State 2, Line 2
    The transaction ended in the trigger. The batch has been aborted.
    ```

-   不能将数据库的恢复模式设置为FULL之外的其他模式。

    例如，若您执行如下命令并将数据库的恢复模式设置为SIMPLE：

    ```
    ALTER DATABASE [TestDb]
    SET RECOVERY SIMPLE
    ```

    则系统会返回如下错误信息：

    ```
    Msg 50000, Level 16, State 1, Procedure ******, Line 46
    Login User [Test11] can't change database [TestDb] recovery model.
    Msg 3609, Level 16, State 2, Line 2
    The transaction ended in the trigger. The batch has been aborted.
    ```

-   将数据库设置为OFFLINE后，不能直接ONLINE。

    例如，对于当前状态为OFFLINE的数据库，若您直接执行ONLINE的命令，如下所示：

    ```
    USE [master]
      GO
      --set offline
      --ALTER DATABASE [TestDb]
      --SET OFFLINE
      --WITH ROLLBACK AFTER 0
      ALTER DATABASE [TestDb]
      SET ONLINE
    ```

    则系统会返回如下错误信息：

    ```
    Msg 5011, Level 14, State 9, Line 1
    User does not have permission to alter database 'TestDb', the database does not exist, or the database is not in a state that allows access checks.
    Msg 5069, Level 16, State 1, Line 1
    ALTER DATABASE statement failed.
    ```

    若您想把数据库的状态从OFFLINE改成ONLINE，您可以使用sp\_rds\_set\_db\_online存储过程，请执行如下命令：

    ```
    EXEC sp_rds_set_db_online 'TestDb'
    ```


## 删除数据库 {#section_pdj_vnq_wdb .section}

执行如下命令，删除数据库：

```
DROP DATABASE [TestDb]
```

若您在删除数据库时没有对该数据库进行过任何备份，系统会返回如下提示信息：

```
DROP DATABASE [TestDb]
        -------------------------------------------------------------------------------------------------
        Kindly reminder:
            your database [TestDb] does not exist any backup set.
        -------------------------------------------------------------------------------------------------
Login User [Test11] has dropped database [TestDb] .
```

