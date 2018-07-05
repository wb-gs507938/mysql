# Migrate RDS for PPAS to local Oracle {#concept_ft5_ms5_ydb .concept}

## Constraints {#section_jjb_ds5_ydb .section}

Now only files and normal types of data can be exported. BLOB and other binary types are not supported.

## Prerequisites {#section_df5_ds5_ydb .section}

-   An Oracle database must be installed on the server.
-   The IP address of the Oracle server must be added to the whitelist of the RDS for PPAS database instance. For specific instructions, see [Set whitelist](../../../../intl.en-US/Quick Start for PPAS/Initial configuration/Set a whitelist.md#).
-   You must create a table structure in Oracle that corresponds to the RDS for PPAS database table structure.
-   The PostgreSQL client has been uploaded to the Oracle database server.

## Procedure {#section_jlr_2s5_ydb .section}

**Note:** This document uses the migration of data from RDS for PPAS to an Oracle database installed on an ECS instance as an example. In this example, the ECS instance OS is CentOS 6.5.

1.  Install the PostgreSQL client on the Oracle database server.

    ```
     [root@oraclexe ~]# yum install postgresql.x86_64
     [root@oraclexe ~]# /usr/bin/psql --version
     psql (PostgreSQL) 8.4.20
    ```

2.  On the ECS instance, configure password-free logon for RDS for PPAS.

    ```
     [root@oraclexe ~]# vim ~/.pgpass
     [root@oraclexe ~]# cat ~/.pgpass 
     rm-2ze466l5u1k657yyn.ppas.rds.aliyuncs.com:3433:ora:myadmin:xxxxxxx
     //Parameter format: HOSTNAME:PORT:DATABASE:USERNAME:PASSWORD
     [root@oraclexe ~]# chmod 0600 ~/.pgpass
    ```

    **Note:** The configuration file .pgpass is located in the HOME directory.

3.  Test the connection between ECS and RDS for PPAS.

    ```
     [root@oraclexe ~]# psql -h rm-2ze466l5u1k657yyn.ppas.rds.aliyuncs.com -p 3433 -U myadmin ora
     psql.bin (9.3.1.3, server 9.3.13.37)
     Input "help" to obtain help information.
     ora=>
    ```

    If you can log on to RDS for PPAS as ora, it means that the connection has been established. After a successful test, return to the root user.

    ```
     ora=> \q
     [root@oraclexe ~]#
    ```

4.  Create a data export script in the ECS instance.
    1.  Create a file ppas\_exp\_all\_tables\_to\_csv.sh.

        ```
         vi ppas_exp_all_tables_to_csv.sh
        ```

    2.  Insert the following text into the ppas\_exp\_all\_tables\_to\_csv.sh script.

        ```
        # ppas_exp_all_tables_to_csv.sh <hostname> <port> <username> <database>
         # Author: Xiao Shaocong (Scott Siu)
         # Email: shaocong.xsc@alibaba-inc.com
         TMP_PATH="/tmp/ppas_tables_$1_$2_$3_$4"
         mkdir $TMP_PATH
         if [ $? -ne 0 ]
         then
             exit 1;
         fi
         echo "select '$1 $2 $3 $4 ' || tablename || ' $TMP_PATH ' || tablename from pg_tables where tableowner='$3' and (schemaname='$3' or schemaname='public');" > /tmp/ppas_tables_$1_$2_$3_$4.sql
         psql -h $1 -p $2 -U $3 $4 -f /tmp/ppas_tables_$1_$2_$3_$4.sql | head -n -2 | tail -n +3 | awk -F " " '{printf ("psql -h %s -p %s -U %s %s -c \"\\copy %s TO '\''%s/%s'\'' CSV HEADER\"\n",$1,$2,$3,$4,$5,$6,$7)}' | sh
        ```

5.  Grant the execution permission to the ppas\_exp\_all\_tables\_to\_csv.sh script.

    ```
     [root@oraclexe ~]# chmod 0755 ppas_exp_all_tables_to_csv.sh
    ```

6.  Run the data export script in the ECS instance.

    ```
     [root@oraclexe ~]# ./ppas_exp_all_tables_to_csv.sh rm-2ze466l5u1k657yyn.ppas.rds.aliyuncs.com 3433 myadmin ora
    ```

7.  Verify the data in the exported CSV file.

    ```
     [root@oraclexe ~]# cat /tmp/ppas_tables_rm-2ze466l5u1k657yyn.ppas.rds.aliyuncs.com_3433_myadmin_ora/*
     deptno,dname,loc
     10,ACCOUNTING,NEW YORK
     20,RESEARCH,DALLAS
     30,SALES,CHICAGO
     40,OPERATIONS,BOSTON
     empno,ename,job,mgr,hiredate,sal,comm,deptno
     7369,SMITH,CLERK,7902,17-DEC-80 00:00:00,800.00,,20
     7499,ALLEN,SALESMAN,7698,20-FEB-81 00:00:00,1600.00,300.00,30
     7521,WARD,SALESMAN,7698,22-FEB-81 00:00:00,1250.00,500.00,30
     7566,JONES,MANAGER,7839,02-APR-81 00:00:00,2975.00,,20
     7654,MARTIN,SALESMAN,7698,28-SEP-81 00:00:00,1250.00,1400.00,30
     7698,BLAKE,MANAGER,7839,01-MAY-81 00:00:00,2850.00,,30
     7782,CLARK,MANAGER,7839,09-JUN-81 00:00:00,2450.00,,10
     7788,SCOTT,ANALYST,7566,19-APR-87 00:00:00,3000.00,,20
     7839,KING,PRESIDENT,,17-NOV-81 00:00:00,5000.00,,10
     7844,TURNER,SALESMAN,7698,08-SEP-81 00:00:00,1500.00,0.00,30
     7876,ADAMS,CLERK,7788,23-MAY-87 00:00:00,1100.00,,20
     7900,JAMES,CLERK,7698,03-DEC-81 00:00:00,950.00,,30
     7902,FORD,ANALYST,7566,03-DEC-81 00:00:00,3000.00,,20
     7934,MILLER,CLERK,7782,23-JAN-82 00:00:00,1300.00,,10
     empno,startdate,enddate,job,sal,comm,deptno,chgdesc
     7369,17-DEC-80 00:00:00,,CLERK,800.00,,20,New Hire
     7499,20-FEB-81 00:00:00,,SALESMAN,1600.00,300.00,30,New Hire
     7521,22-FEB-81 00:00:00,,SALESMAN,1250.00,500.00,30,New Hire
     7566,02-APR-81 00:00:00,,MANAGER,2975.00,,20,New Hire
     7654,28-SEP-81 00:00:00,,SALESMAN,1250.00,1400.00,30,New Hire
     7698,01-MAY-81 00:00:00,,MANAGER,2850.00,,30,New Hire
     7782,09-JUN-81 00:00:00,,MANAGER,2450.00,,10,New Hire
     7788,19-APR-87 00:00:00,12-APR-88 00:00:00,CLERK,1000.00,,20,New Hire
     7788,13-APR-88 00:00:00,04-MAY-89 00:00:00,CLERK,1040.00,,20,Raise
     7788,05-MAY-90 00:00:00,,ANALYST,3000.00,,20,Promoted to Analyst
     7839,17-NOV-81 00:00:00,,PRESIDENT,5000.00,,10,New Hire
     7844,08-SEP-81 00:00:00,,SALESMAN,1500.00,0.00,30,New Hire
     7876,23-MAY-87 00:00:00,,CLERK,1100.00,,20,New Hire
     7900,03-DEC-81 00:00:00,14-JAN-83 00:00:00,CLERK,950.00,,10,New Hire
     7900,15-JAN-83 00:00:00,,CLERK,950.00,,30,Changed to Dept 30
     7902,03-DEC-81 00:00:00,,ANALYST,3000.00,,20,New Hire
     7934,23-JAN-82 00:00:00,,CLERK,1300.00,,10,New Hire
    ```

8.  Import the CSV file into Oracle.
    -   Method 1: Use Oracle SQL Loader to import data. For more information, see [Oracle SQL Loader Overview](http://www.oracle.com/technetwork/database/enterprise-edition/sql-loader-overview-095816.html).
    -   Method 2: Use Oracle SQL Developer to import data. For more information, see [SQL Developer Concepts and Usage](https://docs.oracle.com/cd/E35137_01/appdev.32/e35117/intro.htm).

## Troubleshooting {#section_elf_ts5_ydb .section}

**Problem**

During the execution of data export script, the system displays a message that a directory cannot be created as follows.

```
[root@oraclexe ~]# ./ppas_exp_all_tables_to_csv.sh rm-2ze466l5u1k657yyn.ppas.rds.aliyuncs.com 3433 myadmin ora
mkdir: Cannot create directory: "/tmp/ppas_tables_rm-2ze466l5u1k657yyn.ppas.rds.aliyuncs.com_3433_myadmin_ora": file already exists
```

**Handling process**

Delete the existing directory.

```
[root@oraclexe ~]# rm -rf /tmp/ppas_tables_rm-2ze466l5u1k657yyn.ppas.rds.aliyuncs.com_3433_myadmin_ora
```

