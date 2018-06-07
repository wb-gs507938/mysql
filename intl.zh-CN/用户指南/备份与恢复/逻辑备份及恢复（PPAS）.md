# 逻辑备份及恢复（PPAS） {#concept_ork_yq4_ydb .concept}

本章介绍从 RDS for PPAS 实例进行逻辑备份和恢复的步骤。

## 操作步骤 {#section_rg1_pq4_ydb .section}

1.  安装 PPAS 程序。

    **说明：** 

    必须使用 PPAS 二进制进行导出，使用 Postgresql 社区版二进制会报错。

    Windows版下载地址：[http://yunpan.taobao.com/s/2Y03fmh7PF0](http://yunpan.taobao.com/s/2Y03fmh7PF0) \(提取码：VAXVAc\)

    Linux版下载地址：[http://yunpan.taobao.com/s/1H1T5Kqog8s](http://yunpan.taobao.com/s/1H1T5Kqog8s) \(提取码：561TH4\)

2.  将所有用户权限赋给一个用户（用于数据导出）。

    例如：如果导出时使用的用户为 A，而数据库中还有 B，C 两个用户，则需要执行下面的命令，把 B 和 C 的权限赋给 A。

    ```
    --以用户B登录，然后执行：
     grant B to A;
     --再以用户A登录，然后执行：
     grant C to A;
    ```

    这样，A 就有了访问所有 B 和 C 的数据表的权限。

3.  在 pg\_dump 所在目录，执行下面的命令进行备份。

    ```
    ./pg_dump -h <host> -p <port> -U <user> -f dump.sql <dbname>
    ```

4.  如果需要恢复，可以在 psql 所在目录执行如下命令。

    ```
    ./psql  -h <host> -p <port> -U <user> -d postgres -c "drop database <dbname>"
     ./psql  -h <host> -p <port> -U <user> -d postgres -c "create database <dbname>"
     ./psql  -h <host> -p <port> -U <user> -f dump.sql -d <dbname>
    ```


## 常见问题 {#section_ptv_tq4_ydb .section}

1.  从PPAS导出遇到如下权限错误。

    ```
    ERROR:  permission denied for relation product_component_version
     LOCK TABLE sys.product_component_version IN ACCESS SHARE MODE
    ```

    **解决方案**：这是由于用户使用 PG 的 pg\_dump 程序导出 PPAS 造成的。使用 PPAS 的二进制即可。PPAS 的下载方法见上面的步骤。

2.  从PPAS导出遇到如下权限错误。

    ```
     ERROR:  permission denied for relation <用户表>
    ```

    **解决方案**：这是由于导出时使用的账号没有访问其他用户数据的权限导致。解决方法为（如果用户可以接受），将其他用户的权限都授权给一个用户，再用这个用户导出，即执行如下命令。

    ```
    GRANT ROLE <other roles>,<other roles> to <user for pg_dump>
    ```

3.  使用pg\_dump时遇到如下问题。

    ```
    pgdump -U xxx -h yyy -p3433 <dbname> -f my.sql
     pg_dump: 命令行参数太多（第一个是”-f）
    ```

    **解决方案**：在 windows 平台执行 pg\_dump 时，必须把 <dbname\> 放在所有其他参数后面。

4.  使用 pg\_dump 时报参数错误。

    **解决方案**：可能是参数指定不正确，如：`pg_dump -Uxxx -h yyy`，这种方式是不允许的, -U 后面要有空格（其他参数类似）。


