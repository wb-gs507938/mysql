# Compress data with TokuDB for MySQL 5.6 {#concept_hhr_wzv_ydb .concept}

RDS for MySQL 5.6 supports data compression through the TokuDB storage engine. A large number of tests showed that, after data tables are switched from the InnoDB storage engine to the TokuDB storage engine, the amount of data can be reduced by 80% to 90%, that is, 2 TB of data can be compressed to 400 GB or even lower. The TokuDB storage engine also supports transactions and online DDL operations, which are compatible with applications running on a MyISAM or an InnoDB storage engine.

## Restrictions {#section_gfv_jbw_ydb .section}

-   The TokuDB storage engine does not support foreign keys.
-   The TokuDB storage engine is not applicable to scenarios where frequent and massive reading of data is required.

## Procedure {#section_r4k_lbw_ydb .section}

1.  Run the following command to check the MySQL version.

    ```
    SELECT version();
    ```

    **Note:** Currently, only MySQL 5.6 supports the TokuDB storage engine. For MySQL 5.1 or 5.5, you have to upgrade it to MySQL 5.6 first.

2.  Set the loose\_tokudb\_buffer\_pool\_ratio to indicate the proportion that TokuDB occupies in the shared cache of TokuDB and InnoDB.

    ```
    select sum(data_length) into @all_size from information_schema.tables where engine='innodb';
    select sum(data_length) into @change_size from information_schema.tables where engine='innodb' and concat(table_schema, '.', table_name) in ('XX.XXXX', 'XX.XXXX', 'XX.XXXX');    
    select round(@change_size/@all_size*100);
    ```

    In the preceding code, XX.XXXX refers to the database and table to be transferred to the TokuDB storage engine.

3.  Restart the instance.

    For more information, see [Restart an instance](https://www.alibabacloud.com/help/doc-detail/26177.htm).

4.  Modify the storage engine.

    ```
    ALTER TABLE XX.XXXX ENGINE=TokuDB
    ```

    In the preceding code, XX.XXXX refers to the database and table to be transferred to the TokuDB storage engine.


