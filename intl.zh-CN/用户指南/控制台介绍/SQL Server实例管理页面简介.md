# SQL Server实例管理页面简介 {#concept_hr3_5hd_zdb .concept}

本文将介绍在RDS管理控制台上SQL Server类型的实例目前所支持查询的信息和可以执行的操作。

## 登录实例管理页面的步骤 {#section_cmz_m3d_zdb .section}

1.  登录[RDS管理控制台](http://rds.console.aliyun.com/?spm=5176.doc26126.2.3.Kca631)。
2.  选择目标实例所在地域。
3.  单击实例ID或操作栏下的**管理**，即可进入实例的管理详情页面。

## 实例管理页面简介 {#section_f5h_43d_zdb .section}

下表列出了SQL Server实例的管理页面所支持的查询信息以及可执行的操作。不同版本的SQL Server实例所支持的操作不同，所以操作台显示信息会有差异，请以实际界面为准。

|管理页名称|区块名称|描述|常用相关操作链接|
|-----|----|--|--------|
|界面上方操作区| |可进行登录、迁移数据库，重启、备份实例等操作。| -   [登录数据库](https://help.aliyun.com/document_detail/26138.html)
-   [迁移数据库](https://help.aliyun.com/document_detail/26147.html)
-   [重启实例](https://help.aliyun.com/document_detail/26177.html)
-   [备份实例](https://help.aliyun.com/document_detail/26206.html)

 |
|基本信息|基本信息|可查看实例的基本信息，如实例ID、地域可用区、实例类型、内外网地址、内外网端口等，并进行迁移可用区等操作。|[迁移可用区](https://help.aliyun.com/document_detail/26181.html)|
|实例分布|可查询主实例下临时实例的个数，并进行添加临时实例等操作。| |
|运行状态|可查看实例的运行状态、付费类型、创建时间等信息，并进行释放实例、变更计费方式、给包年包月实例续费等操作。| -   [释放实例](https://help.aliyun.com/document_detail/26184.html)
-   [变更实例计费方式](https://help.aliyun.com/document_detail/52594.html)
-   [续费包年包月实例](https://help.aliyun.com/document_detail/26118.html)

 |
|配置信息|可查看实例的规格、CPU、数据库类型和版本、数据库内存、最大连接数等，并进行设置可维护时间段等操作。| -   [设置可维护时间段](https://help.aliyun.com/document_detail/26180.html)

 |
|使用量统计|可查看实例的存储空间、备份使用量等信息。| |
|账号管理|用户账号|可查看该实例下所有账号的信息，并进行创建账号、修改账号密码、删除账号、修改账号权限等操作。| -   [创建数据库和账号（SQL Server 2008 R2）](https://help.aliyun.com/document_detail/26145.html)
-   [创建数据库和帐号（SQL Server 2012）](https://help.aliyun.com/document_detail/43164.html)
-   [重置密码](https://help.aliyun.com/document_detail/26187.html)
-   [修改账号权限](https://help.aliyun.com/document_detail/26188.html)
-   [删除账号](https://help.aliyun.com/document_detail/50887.html)

 |
|服务授权账号|在阿里云工程师提供技术支持时，您需要对其服务账号进行授权，工程师才能进行相应的操作，如查看或修改实例配置，查看表结构、索引、SQL语句等。|[授权服务账号](https://help.aliyun.com/document_detail/35152.html)|
|数据库管理| |可查看该实例下的数据库信息，并进行创建数据库、删除数据库、迁入备份文件（bak）等操作。| -   [创建数据库和账号（SQL Server 2008 R2）](https://help.aliyun.com/document_detail/26145.html)
-   [创建数据库和帐号（SQL Server 2012）](https://help.aliyun.com/document_detail/43164.html)
-   [删除数据库](https://help.aliyun.com/document_detail/26191.html)
-   [RDS 迁移SQL server数据库，FTP 服务器无法登录的处理](https://help.aliyun.com/document_detail/41804.html)

 |
|数据库连接|实例连接|可查看实例的网络类型、访问模式、内网地址、内网端口、服务器名称等信息，并进行切换网络类型、修改连接地址、申请和释放内外网等操作。| -   [设置访问模式](https://help.aliyun.com/document_detail/26193.html)
-   [设置网络类型](https://help.aliyun.com/document_detail/26194.html)
-   [设置内外网地址](https://help.aliyun.com/document_detail/26195.html)

 |
|监控与报警|监控|可查看监控信息，如CPU和内存利用率、磁盘空间使用量、IOPS等，并进行设置监控频率等操作。|[设置监控频率](https://help.aliyun.com/document_detail/26200.html)|
|报警|可查看监控项状态、云账号报警联系人等信息，并进行设置报警规则等操作。|[设置报警规则](https://help.aliyun.com/document_detail/26201.html)|
|数据安全性|白名单设置|可查看实例的白名单信息，并进行修改白名单、添加白名单分组等操作。|[设置白名单](https://help.aliyun.com/document_detail/26198.html)|
|SQL审计|可查看SQL审计信息，并进行开启、关闭SQL审计功能等操作。|[SQL审计](https://help.aliyun.com/document_detail/26197.html)|
|SSL|可查看SSL证书信息，并进行设置SSL、下载证书等操作。|[设置SSL加密](https://help.aliyun.com/document_detail/32474.html)|
|TDE|可查看透明数据加密（TDE）状态，并进行开通TDE的操作。|[设置透明数据加密](https://help.aliyun.com/document_detail/33510.html)|
|服务可用性|实例可用性|可查看实例可用区的类型、实例可用性、数据复制方式、主备库编号等信息，并进行切换主备实例等操作。|[切换主备实例](https://help.aliyun.com/document_detail/26182.html)|
|可用区架构|可查看单可用区和多可用区的架构图。| |
|备份文件迁入记录|FTP文件|可查看迁入备份文件的记录。| |
|日志管理|错误日志|可查看1个月内数据库中执行错误的SQL语句。|[日志管理](https://help.aliyun.com/document_detail/26203.html)|
|慢日志统计|对1个月内数据库中执行时间超过1秒的SQL语句进行统计汇总，给出慢查询日志的分析报告，并进行下载该统计列表的操作。|
|备份恢复|数据备份|可查看数据备份列表，并进行恢复数据到主实例等操作。| -   [恢复RDS for SQL Server/ PPAS/ PostgreSQL数据](https://help.aliyun.com/document_detail/50603.html)
-   [RDS For SQL Server如何收缩事务日志](https://help.aliyun.com/document_detail/41796.html)

 |
|临时实例|可进行创建临时实例的操作。|
|备份设置|可查看备份策略，如数据备份保留时间、备份周期、备份时间等，并进行修改备份策略的操作。|[备份RDS数据](https://help.aliyun.com/document_detail/26206.html)|
|参数设置|可修改参数|可查看实例的参数值，并进行修改参数值、导入和导出参数等操作。|[设置参数](https://help.aliyun.com/document_detail/26179.html)|
|修改历史|可查看修改参数的记录。| |

