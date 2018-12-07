# RDS for PostgreSQL/PPAS 如何定位本地 IP {#concept_59014_zh .concept}

用户的公网 IP 不固定，使用本地 IP 查看工具定位到的 IP 不准确，即使将查询到的本地 IP 加入了 RDS for PostgreSQL/PPAS的白名单中，连接 RDS 的时候也报错。

## 处理步骤 { .section}

1.  将 IP 地址 0.0.0.0/0 加入 RDS for PostgreSQL 的白名单，操作方法请参见[设置白名单](../../../../intl.zh-CN/快速入门PostgreSQL版/初始化配置/设置白名单.md)。
2.  使用 pgAdmin 4客户端连接[RDS for PostgreSQL](../../../../intl.zh-CN/快速入门PostgreSQL版/连接实例.md#)或者[RDS for PPAS](../../../../intl.zh-CN/快速入门PPAS版/连接实例.md#)实例。
3.  在左侧展开**数据库**，选择**postgres**，单击上方**工具** \> **查询工具**。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/8222/154415473533854_zh-CN.png)

4.  输入如下查询命令并执行。

    ```
    select datname, pid, usename,client_addr, client_hostname, client_port,query  from pg_stat_activity;
    
    ```

5.  查看结果里query列是select所对应的client\_addr列的IP，即为真实的出口IP。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/8222/154415473533855_zh-CN.png)


