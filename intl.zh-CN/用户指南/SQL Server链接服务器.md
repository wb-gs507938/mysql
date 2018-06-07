# SQL Server链接服务器 {#concept_g41_mqv_ydb .concept}

本文仅适用于RDS SQL Server 2012及以上版本的高可用系列实例。

目前，创建链接服务器时仍存在如下两个问题：

-   不能用控制台创建链接服务器。虽然能用一系列的存储过程创建，但过程较复杂。

-   由于RDS的设计，暂时还不能提供通过DNS和对应的IP创建链接服务器的方案。


本文将介绍一个简单的创建链接服务器的方法，如下所示：

```
DECLARE
        @linked_server_name sysname = N'my_link_server',
        @data_source sysname = N'***********',   --style: 10.1.10.1,1433
        @user_name sysname = N'****' ,
        @password nvarchar(128) = N'**********',
        @link_server_options xml
        = N'
            <rds_linked_server>
                <config option="data access">true</config>
                <config option="rpc">true</config>
                <config option="rpc out">true</config>
            </rds_linked_server>
        '
        EXEC sp_rds_add_linked_server
            @linked_server_name,
            @data_source,
            @user_name,
            @password,
            @link_server_options
```

链接服务器创建成功后，会出现如下提示：

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7956/4257_zh-CN.jpg)

选择上图中的**Messages**标签页，即会出现如下信息：

The linked server ‘my\_link\_server’ has set option ‘data access’ to ‘true’.

The linked server ‘my\_link\_server’ has set option ‘rpc’ to ‘true’.

The linked server ‘my\_link\_server’ has set option ‘rpc out’ to ‘true’.

create link server ‘my\_link\_server’ successfully.

