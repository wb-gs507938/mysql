# ApsaraDB for SQL Server 混合云解决方案 {#concept_tnt_5bv_42b .concept}

## **场景说明** {#section_u1t_fns_xfb .section}

本地SQL Server服务需要与RDS SQL Server服务之间进行数据传输或者同步，这里通过SQL Server复制技术来实现数据的同步，它的典型应用场景是，写数据在本地，读数据放在RDS，这样实现混合云的一种解决方案。

## **方案架构** {#section_ck1_kns_xfb .section}

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/64969/154322136732970_zh-CN.png)

## **方案解析** {#section_xq3_qns_xfb .section}

1.  **整体结构**

    这是SQL Server典型的2+3的的高可用和高扩展解决方案，主备使用镜像完成数据库同步，以提供故障转移，分发单独放在一台服务器，其目的是解决publisher故障转移时，分发服务器可以提供持续同步数据到订阅。发布（publisher\)和分发（distributor\)是放在用户本地，拥有自主权限。订阅放在RDS上，建议不要用高可用RDS来做分发，购买单实例来做订阅是比较合适的，由于订阅可以不断扩展，如果有主备高可用，订阅服务器也是利用镜像来实现高可用，一旦发生切换，订阅服务器将无法正常同步数据。

2.  **Distributor**

    **说明：** 配置Distributor，必须要先安装一个SQL Server。分发服务器需要一个单独的服务器来充当，不要将分发服务器放在发布服务器上，那样一旦主备发生切换，分发服务器不能正常工作。

    1.  安装SQL Server ，安装必须要选择replication功能。
    2.  配置分发服务器。

        ```
        USE master
        EXEC sp_adddistributor @distributor = N'RDS-TEST-DIST', @password = N''
        GO
        
        EXEC sp_adddistributiondb 
            @database = N'distribution', 
            @data_folder = N'C:\Program Files\Microsoft SQL Server\MSSQL11.MSSQLSERVER\MSSQL\Data',
            @log_folder = N'C:\Program Files\Microsoft SQL Server\MSSQL11.MSSQLSERVER\MSSQL\Data', 
            @log_file_size = 2,
            @min_distretention = 0, 
            @max_distretention = 72, 
            @history_retention = 48, 
            @security_mode = 1
        GO
        
        USE [distribution] 
        GO
        IF (
            NOT EXISTS (
                SELECT * 
                FROM sysobjects 
                where name = 'UIProperties' and type = 'U ')
        ) 
        
            CREATE TABLE UIProperties(id int) 
        
        IF (
            EXISTS (
                SELECT * 
                FROM ::fn_listextendedproperty('SnapshotFolder', 'user', 'dbo', 'table', 'UIProperties', null, null)
                )
        ) 
            EXEC sp_updateextendedproperty 
                N'SnapshotFolder', 
                N'C:\Program Files\Microsoft SQL Server\MSSQL11.MSSQLSERVER\MSSQL\ReplData', 
                'user', dbo, 
                'table', 
                'UIProperties' 
        ELSE 
            EXEC sp_addextendedproperty N'SnapshotFolder',
             N'C:\Program Files\Microsoft SQL Server\MSSQL11.MSSQLSERVER\MSSQL\ReplData', 
             'user', dbo, 
             'table', 
             'UIProperties'
        GO
        ```

    3.  如果不在域环境，则需要注册一下分发服务器和订阅服务器的别名映射，流程如下：
        1.  在RDS上创建一个可以登录的账户，并分配权限。
        2.  查看主机的HOST NAME。
        3.  开通实例的外网地址,并获得VIP\(VIP估计会变，这里需要特别关注）。
        4.  通过SQL Server配置管理器配置好别名，注意32位和64位的SQL Native Client都需要配置。

            ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/64969/154322136732971_zh-CN.png)

    4.  在分发服务器上注册发布服务器（主备都需要注册） ，如下图。

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/64969/154322136732972_zh-CN.png)

3.  **Publisher**

    在发布服务器上rds-test-master/rds-test-slave上都分别要做一下配置：

    1.  配置分发服务器，并指定分发服务器为rds-test-dist。

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/64969/154322136732973_zh-CN.png)

    2.  与分发服务器一样，需要将所有订阅服务器注册到真实的的HOST NAME地址。
    3.  发布不服务器上创建一张包含有主键的表。
    4.  创建发布，注意只能选事务复制，连接到发布建议使用SQL登录。

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/64969/154322136832974_zh-CN.png)

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/64969/154322136832975_zh-CN.png)

4.  **Subscriber**

    订阅端是放在RDS, RDS可以是基础版本，也可以是高可用班，甚至可以是WEB版本，我的实验版本都包含了这些版本。但建议版本只在同一个迭代的版本你选取，即使如果发布、分发是2012，订阅建议也是，这三者建议保持一致。

    **说明：** 创建分发注意以下几点：

    -   订阅在RDS，应该申请外网地址。
    -   需要取得订阅服务器的服务器名字，在分发和发布上做别名时，一定要制定真实的订阅服务器。
    -   订阅的方式只能是push\(推送），不能是Pull\(拉取）。
    -   订阅的登录方式不能使用SQL Agent account，需要使用SQL 登录方式。

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/64969/154322136832976_zh-CN.png)

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/64969/154322136832977_zh-CN.png)

5.  **镜像与复制共存**

    镜像和复制共存主要要考虑的一个点是，如果MASTER-SLAVE发生了故障转移，如何让数据库提供服务器，有3个地方需要关注：

    1.  主备的日志读取和复制关系的矫正，如果你的MASTER 宕机了，发生了故障转移，这个时候SLAVE如果要提供服务器，日志读取器会等待镜像日志先同步，再做分发，但有时候可能原MASTER发生硬件故障，这时候，就需要打开一个跟踪标记1448，在不等最小日志确认的情况下可以继续分发数据。
    2.  日志读取代理需要设置partner server。
    3.  快照代理同样需要设置partner server。
6.  **复制与RDS共存**

    需要说明的是RDS只能作为订阅，不能作为分发和发布。RDS的订阅数据库类型不限。


## **注意事项** {#section_g3k_c2t_xfb .section}

-   要作为订阅，需要开通外网。
-   RDS和LOCAL最好开通VPN或者专线。
-   订阅服务器不能直接使用，需要配置网络别名映射。

