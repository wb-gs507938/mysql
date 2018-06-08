# Migrate RDS for PostgreSQL data to the local PostgreSQL database {#concept_jzm_bzv_ydb .concept}

RDS for PostgreSQL supports the migration of cloud data to the local database by using logical backup files.

## Procedure {#section_ysb_qzv_ydb .section}

1.  Connect the PostgreSQL client to RDS.
2.  Run the following command to back up the data.

    ```
    pg_dump -U username -h hostname -p port databasename -f filename
    ```

    Parameters description:

    -   username: Indicates the username used for database logon.
    -   hostname: Indicates the host name of the database.
    -   port: Indicates the database port number.
    -   databasename: Indicates the name of the database you want to back up.
    -   filename: Indicates the name of the backup file to be generated.
    For example:

    ```
    pg_dump -U myuser -h rds2z2tp80v3752wb455.pg.rds.aliyuncs.com -p 3433 pg001 -f pg001.sql
    ```

3.  Save the pg001.sql backup file to the target server.
4.  Run the following command to recover data to the local database:

    ```
    psql -U username -h hostname -d desintationdb -p port -f dumpfilename.sql
    ```

    Parameter description:

    -   username: Indicates the username used for database logon.
    -   hostname: Indicates the database address.
    -   port: Indicates the database port number.
    -   databasename: Indicates the database name.
    -   filename: Indicates the backup file name.
    For example:

    ```
    psql -U myuser -h localhost -d pg001 -p 5432 -f pg001.sql
    ```

    Since the permission configuration of the RDS database is inconsistent with that of the local database, some permission-related warnings or errors may occur during the data import. They can be ignored, for example:

    ```
    WARNING: no privileges could be revoked for "xxxxx"
    ERROR: role "xxxxx" does not exist
    ```


