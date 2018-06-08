# 迁移 RDS for PPAS 数据到本地 PPAS {#concept_oln_lzv_ydb .concept}

阿里云数据库 PPAS 版支持通过逻辑备份文件将云上数据迁移到本地数据库。

## 操作步骤 {#section_hsz_d1w_ydb .section}

1.  通过 PostgreSQL 客户端，连接云数据库。
2.  执行如下命令，备份数据。

    ```
    pg_dump -U username -h hostname -p port databasename -f filename
    ```

    参数说明如下：

    -   username：数据库用户名
    -   hostname：数据库主机名
    -   port：数据库端口号
    -   databasename：要备份的数据库名
    -   filename：要生成的备份文件名称例如：

        ```
        pg_dump -U ppas_user -h rdsv07z563m7o25cj550public.ppas.rds.aliyuncs.com -p 3433 edb -f ppas.sql
        ```

3.  将备份文件ppas.sql放到目标服务器中。
4.  执行如下命令将数据恢复到本地数据库。

    ```
    psql -U username -h hostname -d desintationdb -p port -f dumpfilename.sql
    ```

    参数说明如下：

    -   username：数据库用户名
    -   hostname：数据库地址
    -   port：数据库端口号
    -   databasename：数据库名
    -   filename：备份文件名称如：

        ```
        psql -U ppas_user -h localhost -d edb -p 5444 -f ppas.sql
        ```

        由于 RDS 数据库的权限设置和本地数据库不一致，在数据导入过程当中可能会出现一些与权限相关的 WARNING 或 ERROR，可以忽略，如：

        ```
        WARNING:  no privileges could be revoked for "xxxxx"
        ERROR:  role "xxxxx" does not exist
        ```


