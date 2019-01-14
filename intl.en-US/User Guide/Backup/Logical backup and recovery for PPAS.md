# Logical backup and recovery for PPAS {#concept_ork_yq4_ydb .concept}

This document describes the procedure for logical backup and recovery for RDS for PPAS instances.

## Procedure {#section_rg1_pq4_ydb .section}

1.  Install the PPAS program.

    **Note:** 

    You must use the PPAS binary system for export. Using the PostgreSQL community binary system leads to an error.

    -   Download Windows client \([Part 1](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/attach/70088/cn_zh/1547394998142/pem_client-5.0.0-2-windows.part1.rar), [Part 2](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/attach/70088/cn_zh/1547395117351/pem_client-5.0.0-2-windows.part2.rar)\)
    -   [Download Linux client \(32-bit\)](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/attach/70088/cn_zh/1547392528705/pem_client-5.0.0-2-linux.run) 
    -   [Download Linux client \(64-bit\)](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/attach/70088/cn_zh/1547393149148/pem_client-5.0.0-2-linux-x64.run)
2.  Grant all permissions to a role \(to export the data\).

    For example, if role A is used to export data but there are two other roles, namely, B and C, in the database, you must run the following commands to grant role A the permissions of role B and role C.

    ```
     -- Use Role B for logon to run the following command:
     grant B to A;
     -- Then use Role A for logon to run the following command:
     grant C to A;
    ```

    In this way, role A has the permission to access all data tables of role B and role C.

3.  In the directory where `pg_dump` is located, run the following backup command:

    ```
    ./pg_dump -h <host> -p <port> -U <user> -f dump.sql <dbname>
    ```

4.  If recovery is required, you can run the following commands in the directory where `psql` is located:

    ```
     ./psql -h <host> -p <port> -U <user> -d postgres -c "drop database <dbname>"
     ./psql -h <host> -p <port> -U <user> -d postgres -c "create database <dbname>"
     ./psql -h <host> -p <port> -U <user> -f dump.sql -d <dbname>
    ```


## FAQ {#section_ptv_tq4_ydb .section}

1.  The following error occurs when you export data from PPAS:

    ```
    ERROR: permission denied for relation product_component_version
     LOCK TABLE sys.product_component_version IN ACCESS SHARE MODE
    ```

    **Solution**: The cause for this error is that you have used the pg\_dump program of PG to export data from PPAS. You can use the PPAS binary system to export the data. For PPAS downloading methods, see the preceding procedure.

2.  The following error occurs when you export data from PPAS:

    ```
     ERROR: permission denied for relation <user table>
    ```

    **Solution**: The cause for this error is that the account used for data export has no permission to access the data of other roles. If acceptable, you can grant a role the permissions of other roles and then use this role to export data by running the following command:

    ```
    GRANT ROLE<other roles>,<other roles> to <user for pg_dump>
    ```

3.  The following error occurs when you use pg\_dump.

    ```
     pgdump -U xxx -h yyy -p3433 <dbname> -f my.sql
     pg_dump: too many parameters (the first one is ”-f) in the command line
    ```

    **Solution**: When running pg\_dump on Windows, you must append all other parameters with <dbname\>.

4.  A parameter error occurs when you use pg\_dump.

    **Solution**: The possible cause is that the specified parameter is incorrect, such as `pg_dump -Uxxx -h yyy`. This parameter is not allowed since a space is needed next to -U \(other parameters also follow this style\).


