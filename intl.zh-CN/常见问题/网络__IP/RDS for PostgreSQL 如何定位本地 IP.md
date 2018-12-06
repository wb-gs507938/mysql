# RDS for PostgreSQL 如何定位本地 IP {#concept_59014_zh .concept}

用户的公网 IP 不固定，使用本地 IP 查看工具定位到的 IP 不准确，即使将查询到的本地 IP 加入了 RDS for PostgreSQL的白名单中，连接 RDS 的时候也报错。

## 处理步骤 { .section}

1.  将 IP 地址 0.0.0.0/0 或您公司的 IP 段加入 RDS for PostgreSQL 的白名单，操作方法请参见[设置白名单](../../../../intl.zh-CN/快速入门PostgreSQL版/初始化配置/设置白名单.md)。
2.  使用 pgsql 客户端链接 RDS for PostgreSQL。

    ```
    psql -hRDS连接地址 -U账户 -p3432 postgres(需要手动输入密码)
    
    ```

    ![](http://ata2-img.cn-hangzhou.img-pub.aliyun-inc.com/6ded3dd6ff89f6e3a616327a5adb6113.png)

3.  查询连接信息。

    ```
    select datname, pid, usename,client_addr, client_hostname, client_port,query  from pg_stat_activity;
    
    ```

    查询结果如下所示。进程中 **query** 字段为 **select datname, pid, usename,client\_addr, client\_hostname, client\_port,query from pg\_stat\_activity** 的行对应的 **client\_addr** 就是用户的出口 IP。

    ```
    postgres=> select datname, pid, usename,client_addr, client_hostname, client_port,query  from pg_stat_activity;
    datname  |  pid  | usename  |  client_addr   | client_hostname | client_port |                                                query
    ----------+-------+----------+----------------+-----------------+-------------+------------------------------------------------------------------------------------------------------
    postgres | 35260 | postgres | 192.168.1.2 |                 |        9879 | select datname, pid, usename,client_addr, client_hostname, client_port,query  from pg_stat_activity;
    (1 row)
    
    ```


