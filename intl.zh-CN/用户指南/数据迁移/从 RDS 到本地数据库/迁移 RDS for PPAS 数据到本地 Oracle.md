# 迁移 RDS for PPAS 数据到本地 Oracle {#concept_ft5_ms5_ydb .concept}

## 限制说明 {#section_jjb_ds5_ydb .section}

当前只支持文件及普通数据类型进行导出，不支持 BLOB 等二进制类型。

## 前提条件 {#section_df5_ds5_ydb .section}

-   已安装好 Oracle 数据库的服务器。
-   在 RDS for PPAS 数据库实例的白名单中添加 Oracle 服务器的IP地址，具体操作请参见[设置白名单](../cn.zh-CN/快速入门PPAS版/初始化配置/设置白名单.md#)。
-   用户需要按 RDS for PPAS 数据库中的表结构在 Oracle 中建立对应的表结构。
-   已获取 PostgreSQL 客户端并上传到 Oracle 数据库服务器上。

## 操作步骤 {#section_jlr_2s5_ydb .section}

**说明：** 本例以将 RDS for PPAS 数据迁移到安装在云服务器 ECS 上的 Oracle 为例。本例中的云服务器 ECS 操作系统为 CentOS 6.5。

1.  在 Oracle 数据库服务器上安装 PostgreSQL 客户端。

    ```
    [root@oraclexe ~]# yum install postgresql.x86_64
     [root@oraclexe ~]# /usr/bin/psql --version
     psql (PostgreSQL) 8.4.20
    ```

2.  在 ECS 中配置对 RDS for PPAS 实例的无密码登录。

    ```
    [root@oraclexe ~]# vim ~/.pgpass
     [root@oraclexe ~]# cat ~/.pgpass 
     rm-2ze466l5u1k657yyn.ppas.rds.aliyuncs.com:3433:ora:myadmin:xxxxxxx
     //参数格式为 HOSTNAME:PORT:DATABASE:USERNAME:PASSWORD
     [root@oraclexe ~]# chmod 0600 ~/.pgpass
    ```

    **说明：** 配置文件 .pgpass 位于 HOME 目录下。

3.  测试 ECS 和 RDS for PPAS 连接。

    ```
    [root@oraclexe ~]# psql -h rm-2ze466l5u1k657yyn.ppas.rds.aliyuncs.com -p 3433 -U myadmin ora
     psql.bin (9.3.1.3, 服务器 9.3.13.37)
     输入 "help" 来获取帮助信息.
     ora=>
    ```

    如果能以 ora 用户登录 RDS for PPAS，则连接成功。测试成功后，返回到 root 用户。

    ```
    ora=> \q
     [root@oraclexe ~]#
    ```

4.  在 ECS 中建立数据导出脚本。
    1.  建立文件 ppas\_exp\_all\_tables\_to\_csv.sh。

        ```
         vi ppas_exp_all_tables_to_csv.sh
        ```

    2.  将如下文本插入到 ppas\_exp\_all\_tables\_to\_csv.sh 脚本。

        ```
        # ppas_exp_all_tables_to_csv.sh <hostname> <port> <username> <database>
         # Author: Xiao Shaocong (Scott Siu)
         # E-Mail: shaocong.xsc@alibaba-inc.com
         TMP_PATH="/tmp/ppas_tables_$1_$2_$3_$4"
         mkdir $TMP_PATH
         if [ $? -ne 0 ]
         then
             exit 1;
         fi
         echo "select '$1 $2 $3 $4 ' || tablename || ' $TMP_PATH ' || tablename from pg_tables where tableowner='$3' and (schemaname='$3' or schemaname='public');" > /tmp/ppas_tables_$1_$2_$3_$4.sql
         psql -h $1 -p $2 -U $3 $4 -f /tmp/ppas_tables_$1_$2_$3_$4.sql | head -n -2 | tail -n +3 | awk -F " " '{printf ("psql -h %s -p %s -U %s %s -c \"\\copy %s TO '\''%s/%s'\'' CSV HEADER\"\n",$1,$2,$3,$4,$5,$6,$7)}' | sh
        ```

5.  给 ppas\_exp\_all\_tables\_to\_csv.sh 脚本添加执行权限。

    ```
     [root@oraclexe ~]# chmod 0755 ppas_exp_all_tables_to_csv.sh
    ```

6.  在 ECS 中执行数据导出脚本。

    ```
    [root@oraclexe ~]# ./ppas_exp_all_tables_to_csv.sh rm-2ze466l5u1k657yyn.ppas.rds.aliyuncs.com 3433 myadmin ora
    ```

7.  验证导出 CSV 文件的数据。

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

8.  将 CSV 导入到 Oracle。
    -   方案 1：通过 Oracle 的 SQL\*Loader 进行数据导入，详情请参考：[Oracle SQL Loader Overview](http://www.oracle.com/technetwork/database/enterprise-edition/sql-loader-overview-095816.html)。
    -   方案 2：通过 Oracle SQL Developer 进行数据导入，详情请参考：[SQL Developer Concepts and Usage](https://docs.oracle.com/cd/E35137_01/appdev.32/e35117/intro.htm)。

## 问题处理 {#section_elf_ts5_ydb .section}

**问题**

执行数据导出脚本时，提示无法创建目录，如下所示。

```
[root@oraclexe ~]# ./ppas_exp_all_tables_to_csv.sh rm-2ze466l5u1k657yyn.ppas.rds.aliyuncs.com 3433 myadmin ora
mkdir: 无法创建目录"/tmp/ppas_tables_rm-2ze466l5u1k657yyn.ppas.rds.aliyuncs.com_3433_myadmin_ora": 文件已存在
```

**处理步骤**

删除已存在的目录。

```
[root@oraclexe ~]# rm -rf /tmp/ppas_tables_rm-2ze466l5u1k657yyn.ppas.rds.aliyuncs.com_3433_myadmin_ora
```

