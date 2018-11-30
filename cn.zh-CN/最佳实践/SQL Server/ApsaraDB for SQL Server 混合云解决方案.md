# ApsaraDB for SQL Server 混合云解决方案 {#concept_tnt_5bv_42b .concept}

## **场景说明** {#section_u1t_fns_xfb .section}

ApsaraDB for SQL Server混合云解决方案用于实现本地SQL Server服务与RDS for SQL Server服务之间的数据传输或者同步。利用SQL Server复制技术实现数据的同步，其典型应用场景就是写数据在本地，读数据在RDS for SQL Server。

## **方案架构** {#section_ck1_kns_xfb .section}

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/64969/154354695032970_zh-CN.png)

## **方案解析** {#section_xq3_qns_xfb .section}

1.  **整体结构**

    这是SQL Server典型的2+3的的高可用和高扩展解决方案，主备使用镜像完成数据库同步，以提供故障转移。分发单独放在一台服务器，其目的是解决publisher故障转移时，分发服务器可以提供持续同步数据到订阅服务器。发布（publisher\)和分发（distributor\)是放在用户本地，拥有自主权限。

    订阅（subscriber）放在RDS上，建议不要用高可用RDS实例来做订阅，购买单实例来做订阅是比较合适的，方便后续不断扩展。如果有主备高可用，订阅服务器也是利用镜像来实现高可用，一旦发生切换，订阅服务器将无法正常同步数据。

    **说明：** RDS和LOCAL最好开通VPN或者专线。

2.  **Distributor**

    **说明：** 需要一个单独的服务器作为分发服务器，不要将分发服务器放在发布服务器上，否则一旦主备发生切换，分发服务器将不能正常工作。

    1.  安装SQL Server ，安装时必须要选择replication功能。
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

    3.  如果不在域环境或域环境未开启自动映射，您需要注册分发服务器和订阅服务器的别名映射。订阅服务器注册流程较复杂，请参考如下步骤：
        1.  在RDS上创建一个可以登录的账户，并分配权限，详细的操作步骤请参见[创建数据库和账号SQL Server 2008 R2版](../../../../cn.zh-CN/快速入门SQL Server版/初始化配置/创建数据库和账号/创建数据库和账号SQL Server 2008 R2版.md#)、[创建数据库和账号SQL Server 2012/2016版](../../../../cn.zh-CN/快速入门SQL Server版/初始化配置/创建数据库和账号/创建数据库和账号SQL Server 2012__2016版.md#)。
        2.  查看主机的HOST NAME。
        3.  开通实例的外网地址，具体方法请参见[申请外网地址](https://help.aliyun.com/document_detail/97736.html)。
        4.  在Server配置管理器配置别名。

            **说明：** 32位和64位的SQL Native Client都需要配置。

            ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/64969/154354695032971_zh-CN.png)

    4.  在分发服务器上注册发布服务器（主备都需要注册）。

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/64969/154354695032972_zh-CN.png)

3.  **Publisher**

    在发布服务器例如rds-test-master/rds-test-slave上分别做以下配置：

    1.  配置分发服务器，并指定分发服务器为rds-test-dist。

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/64969/154354695032973_zh-CN.png)

    2.  与分发服务器一样，需要将所有订阅服务器注册真实的HOST NAME地址。
    3.  在发布服务器上创建一张包含有主键的表。
    4.  创建发布。

        **说明：** 只能选事务复制，建议使用SQL登录连接到发布。

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/64969/154354695032974_zh-CN.png)

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/64969/154354695032975_zh-CN.png)

4.  **Subscriber**

    订阅端放在RDS上， RDS实例可以是基础版本、高可用版本或者WEB版本。但建议发布服务器、分发服务器和订阅服务器这三者的版本保持一致。

    **说明：** 创建订阅时需要注意以下几点：

    -   订阅端放在RDS上，应该申请外网地址。
    -   需要取得订阅服务器的名称，因为在分发和发布服务器上做别名映射时需要真实的订阅服务器名称。
    -   订阅的方式只能是Push\(推送），不能是Pull\(拉取）。
    -   订阅的登录方式不能使用SQL Agent Account，需要使用SQL 登录方式。

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/64969/154354695032976_zh-CN.png)

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/64969/154354695032977_zh-CN.png)

5.  **镜像与复制共存**

    镜像和复制共存时，如果MASTER-SLAVE发生了故障转移，如何让数据库继续提供服务，需要注意以下几点：

    1.  主备的日志读取和复制关系的矫正。如果MASTER 宕机，发生了故障转移，此时SLAVE如果要提供服务，日志读取器会等待镜像日志先同步，再做发布，但如果MASTER发生硬件故障，此时SLAVE需要打开一个跟踪标记1448，在镜像故障的情况下可以继续分发数据。

        **说明：** 1448标记用于在事务复制和镜像共用时，改变LogReader的读取限，当镜像故障时仍然可以从Principle读取日志。

    2.  日志读取代理、快照代理需要设置partner server。
6.  **复制与RDS共存**
    -   RDS只能作为订阅，不能作为发布和分发。
    -   RDS的订阅数据库类型不限。

