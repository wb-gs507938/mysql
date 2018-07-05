# Logical backup and recovery for PPAS {#concept_ork_yq4_ydb .concept}

This chapter describes the steps for logical backup and recovery from the RDS instances for PPAS.

## Procedure {#section_rg1_pq4_ydb .section}

1.  Install the PPAS program.

    **Note:** 

    You must use the PPAS binary system for export. Using the Postgresql community binary system leads to an error.

    Windows users: [http://yunpan.taobao.com/s/2Y03fmh7PF0](http://yunpan.taobao.com/s/2Y03fmh7PF0) \(Access code: VAXVAc\).

    Linux users: [http://yunpan.taobao.com/s/1H1T5Kqog8s](http://yunpan.taobao.com/s/1H1T5Kqog8s) \(Access code: 561TH4\).

2.  Grant the permissions of all roles to a role \(to export the data\).

    For example, if Role A is used to export data but there are two other roles, namely, B and C, in the database, you must run the following commands to grant Role A the permissions of Role B and Role C.

    ```
     -- Use Role B for logon to run the following command:
     grant B to A;
     -- Then use Role A for logon to run the following command:
     grant C to A;
    ```

    In this way, Role A has the permissions to access all data tables of Role B and Role C.

3.  In the directory where pg\_dump is located, run the following backup command.

    ```
    ./pg_dump -h <host> -p <port> -U <user> -f dump.sql <dbname>
    ```

4.  If recovery is required, you can run the following commands in the directory where psql is located.

    ```
     ./psql -h <host> -p <port> -U <user> -d postgres -c "drop database <dbname>"
     ./psql -h <host> -p <port> -U <user> -d postgres -c "create database <dbname>"
     ./psql -h <host> -p <port> -U <user> -f dump.sql -d <dbname>
    ```


## FAQs {#section_ptv_tq4_ydb .section}

1.  The following error occurs when you export data from PPAS.

    ```
    ERROR: permission denied for relation product_component_version
     LOCK TABLE sys.product_component_version IN ACCESS SHARE MODE
    ```

    **Solution**: The cause for this error is that you have used the pg\_dump program of PG to export data from PPAS. You can use PPAS binary system to export the data. For PPAS downloading methods, see the proceding steps.

2.  The following error occurs when you export data from PPAS.

    ```
     ERROR: permission denied for relation <user table>
    ```

    **Solution**: The cause for this error is that the account used for data export has no permission to access the data of other roles. If acceptable, you can grant a role the permissions of other roles and then use this role to export data, namely, running the following command.

    ```
    GRANT ROLE<other roles>,<other roles> to <user for pg_dump>
    ```

3.  The following error occurs when you use pg\_dump.

    ```
     pgdump -U xxx -h yyy -p3433 <dbname> -f my.sql
     pg_dump: too many parameters (the first one is ”-f) in the command line
    ```

    **Solution**: When running pg\_dump on the Windows platform, you must append all other parameters with <dbname\>.

4.  A parameter error occurs when you use pg\_dump.

    **Solution**: The possible cause is that the specified parameter is incorrect, for example,

    ```
    pg_dump -Uxxx -h yyy.
    ```

    This parameter is not allowed since a white space is needed next to -U \(other parameters also follow this style\).


