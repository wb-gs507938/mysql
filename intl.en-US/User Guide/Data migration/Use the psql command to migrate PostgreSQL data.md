# Use the psql command to migrate PostgreSQL data {#concept_qhq_gbw_ydb .concept}

This example describes how to use the psql command to restore the PostgreSQL data backup file to the target RDS.

## Background information {#section_rdh_5bw_ydb .section}

PostgreSQL supports logical backup. To import PostgreSQL data, use the pg\_dump logical backup function to export the backup file and then import it to the RDS through psql.

## Prerequisites {#section_pbc_vbw_ydb .section}

You have prepared the RDS instance. For more information, see [Apply for an Internet address](../intl.en-US/Quick Start for PostgreSQL/Initial configuration/Apply for an Internet address.md#) and [../DNMYSQ1877999/EN-US\_TP\_7850.md\#](../intl.en-US/Quick Start for PostgreSQL/Initial configuration/Create database and account.md#).

## Prepare local data {#section_us5_vbw_ydb .section}

1.  Connect to the local PostgreSQL database through the PostgreSQL client.
2.  Run the following command to back up the data.

    ```
    pg_dump -U username -h hostname -p port databasename -f filename
    ```

    Parameters are described as follows:

    -   username: User name for the local database.
    -   hostname: Local database host name. localhost can be used if you log on to the local database host.
    -   port: Local database port number.
    -   databasename: Name of the local database to be backed up.
    -   filename: Name of the backup file to be generated.
    For example, to use the database account William to back up the local PostgreSQL database,  log in to the PostgreSQL host and run the following command:

    ```
    pg_dump -U William -h localhost -p 3433 pg001 -f pg001.sql
    ```


## Perform the migration {#section_d1b_1cw_ydb .section}

**Note:** Network stability and data security is improved when data is restored through the RDS intranet. We recommend that you upload the data to the ECS and then restore the data to the target RDS through the intranet. If the data file is too large, compress it before uploading. This scenario is explained in the following example:

1.  Log on to the ECS.
2.  Run the following command through the PostgreSQL client to import the data into the RDS.

    ```
    psql -U username -h hostname -d desintationdb -p port -f dumpfilename.sql
    ```

    Parameters are described as follows:

    -   username: PostgreSQL database user name on the RDS
    -   hostname: PostgreSQL database address on the RDS
    -   port: PostgreSQL database port number on the RDS
    -   databasename: PostgreSQL database name on the RDS
    -   filename: Local backup data file name
    For example:

    ```
    psql -U William -h postgresql.rds.aliyuncs.com -d pg001 -p 3433 -f pg001.sql
    ```

    Since the permission configuration of the RDS database is inconsistent with that of the local database, some permission-related warnings or errors may occur during the data import. They can be ignored, for example:

    ```
    WARNING: no privileges could be revoked for "xxxxx"
    ERROR: role "xxxxx" does not exist
    ```


