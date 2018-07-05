# Linked server of SQL Server instances {#concept_g41_mqv_ydb .concept}

This article is applicable only to high-availability instances of RDS SQL Server 2012 and later versions.

Currently, linked server creation has the following constraints:

-   You cannot create a linked server on the RDS console.
-   Creating a linked server with a series of stored procedures is complicated.
-   You cannot create a linked server by using DNS and the corresponding IP address.

Despite the constraints, this article provides a simple method for creating a linked server.

```
DECLARE
        @linked_server_name sysname = N'my_link_server',
        @data_source sysname = N'***********', --style: 10.1.10.1,1433
        @user_name sysname = N'****' ,
        @password nvarchar(128) = N'**********',
        @link_server_options xml
        = N'
            <rds_linked_server>
                <config option="data access">true</config>
                <config option="rpc">true</config>
                <config option="rpc out">true</config>
            </rds_linked_server>
        
        EXEC sp_rds_add_linked_server
            @linked_server_name,
            @data_source,
            @user_name,
            @password,
            @link_server_options
```

The following message “create successfully” appears after the linked server is successfully created.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7956/4257_en-US.jpg)

Click the **Messages** tab shown in the preceding figure, and the following information is displayed.

```
The linked server 'my_link_server' has set option 'data access' to 'true'.
The linked server 'my_link_server' has set option 'rpc’ to 'true'.
The linked server 'my_link_server' has set option 'rpc out' to 'true'.
create link server 'my_link_server' successfully.
```

