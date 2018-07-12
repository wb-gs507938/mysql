# Database management of SQL Server instances {#concept_q1d_qmq_wdb .concept}

This document describes how to create and manage databases in an instance of ApsaraDB for SQL Server by using SQL commands.

**Note:** The operation described in this document is applicable only to instances of RDS SQL Server 2012 and later versions.

## Create a database {#section_u3p_gnq_wdb .section}

Run the following command to create a database:

**Note:** A default path is generated when you create a database in RDS. Therefore, do not specify any file path.

```
CREATE DATABASE TestDb
```

## Modify a database {#section_qz3_jnq_wdb .section}

You can modify many database attributes as needed. However, do not perform the following operations unless necessary:

-   Do not move the database to an incorrect file path.

    For example, if you specify an incorrect file path while running the following command:

    ```
    ALTER DATABASE [TestDb]
    MODIFY FILE
    ( NAME = N'TestDb', FILENAME = N'E:\KKKK\DDD\DATA\TestDb.mdf' )
    ```

    The following error message is returned:

    ```
    Msg 50000, Level 16, State 1, Procedure ******, Line 152
    The file path [ 
    E:\KKKK\DDD\DATA\TestDb.mdf ] is invalid,please specify correct path folder [ E:\mmm\gggg\ ].
    Msg 3609, Level 16, State 2, Line 2
    The transaction ended in the trigger. The batch has been aborted.
    ```

-   Do not set the database recovery mode to a mode other than FULL.

    For example, if you set the database recovery mode to SIMPLE while running the following command:

    ```
    ALTER DATABASE [TestDb]
    SET RECOVERY SIMPLE
    ```

    The following error message is returned:

    ```
    Msg 50000, Level 16, State 1, Procedure ******, Line 46
    Login User [Test11] can't change database [TestDb] recovery model.
    Msg 3609, Level 16, State 2, Line 2
    The transaction ended in the trigger. The batch has been aborted.
    ```

-   Do not set a database in offline state to online directly.

    For example, if you run the following ONLINE command directly:

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

    The following error message is returned:

    ```
    Msg 5011, Level 14, State 9, Line 1
    User does not have permission to alter database 'TestDb', the database does not exist, or the database is not in a state that allows access checks.
    Msg 5069, Level 16, State 1, Line 1
    ALTER DATABASE statement failed.
    ```

    To change the database status from offline to online, run the following command in the sp\_rds\_set\_db\_online stored procedure:

    ```
    EXEC sp_rds_set_db_online 'TestDb'
    ```


## Delete a database {#section_pdj_vnq_wdb .section}

Run the following command to delete a database:

```
DROP DATABASE [TestDb]
```

The following prompt appears if the database to be deleted is not backed up:

```
DROP DATABASE [TestDb]
        
        Kindly reminder:
            your database [TestDb] does not exist any backup set.
        
Login User [Test11] has dropped database [TestDb] .
```

