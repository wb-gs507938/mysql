# MySQL 5.7基础版创建数据库和账号 {#concept_qn2_r2g_vdb .concept}

**说明：** 

本文仅适用于MySQL 5.7基础版本的实例。关于如何在MySQL 5.7高可用版、MySQL 5.5和MySQL 5.6版本的实例中创建数据库和账号，请参见文档[MySQL 5.7高可用版/5.5/5.6创建数据库和账号](intl.zh-CN/快速入门MySQL版/初始化配置/创建数据库和账号/MySQL 5.7高可用版/5.5/5.6创建数据库和账号.md#)

若要使用云数据库RDS，您需要在实例中创建数据库和账号。对于MySQL 5.7基础版本的实例，您需要通过RDS控制台创建一个初始账号，通过客户端创建和管理数据库。本文将以MySQL-Front客户端为例介绍如何在MySQL 5.7版本的实例中创建数据库和账号的操作步骤。

## 注意事项 {#section_gzr_zzm_vdb .section}

-   同一实例下的数据库共享该实例下的所有资源。每个实例支持创建无数个数据库，支持创建一个初始账号以及无数个普通账号。您可以通过SQL命令创建、管理普通账号和数据库，详情请参见[常用SQL命令（MySQL）](https://www.alibabacloud.com/help/zh/doc-detail/43889.htm)。

-   如果您要迁移本地数据库到RDS，请在RDS实例中创建与本地数据库一致的迁移账号和数据库。

-   分配数据库账号权限时，请按最小权限原则和业务角色创建账号，并合理分配只读和读写权限。必要时可以把数据库账号和数据库拆分成更小粒度，使每个数据库账号只能访问其业务之内的数据。如果不需要数据库写入操作，请分配只读权限。

-   为保障数据库的安全，请将数据库账号的密码设置为强密码，并定期更换。


## 操作步骤 {#section_h5c_b1n_vdb .section}

1.  登录[RDS管理控制台](https://rds.console.aliyun.com/)。
2.  选择目标实例所在地域。
3.  单击目标实例的ID，进入基本信息页面。
4.  在左侧导航栏中，选择**账号管理**，进入账号管理页面。
5.  单击**创建初始账号**。
6.  输入要创建的账号信息，如下图所示。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7820/15329156082432_zh-CN.png)

    **参数说明：**

    |参数|说明|
    |--|--|
    |数据库账号|长度为2~16个字符，由小写字母、数字或下划线组成，且必须以字母开头，以字母或数字结尾。**说明：** 建议您一次授权数据库的数量不要超过25个。

|
    |密码|该账号对应的密码。长度为8~32个字符，由字母、数字、中划线或下划线中的任意三种组成。|
    |确认密码|输入与密码一致的字段，以确保密码正确输入。|

7.  单击****确定****。
8.  将要访问RDS实例的IP地址加入RDS白名单中。关于如何设置白名单，请参见[设置白名单](intl.zh-CN/快速入门MySQL版/初始化配置/设置白名单.md#)。
9.  启动MySQL-Front客户端。
10. 在打开登录信息窗口，单击**新建**，如下图所示。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7820/15329156082575_zh-CN.png)

11. 输入要连接的RDS实例信息，如下图所示。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7820/15329156082576_zh-CN.png)

    参数说明：

    -   名称：MySQL-Front连接数据库的任务名称。若不填，系统会将默认与Host一致。

    -   Host：若使用内网连接，需输入RDS实例的内网地址。若使用外网连接，需输入RDS实例的外网地址。查看RDS实例的内外网地址及端口信息的步骤如下：

        1.  登录[RDS管理控制台](https://rds.console.aliyun.com/)。
        2.  选择目标实例所在地域。
        3.  单击目标实例的ID，进入基本信息页面。
        4.  在基本信息栏中，即可查看内外网地址及内外网端口信息，如下图所示：

            ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7820/15329156082577_zh-CN.png)

    -   端口：若使用内网连接，需输入RDS实例的内网端口。若使用外网连接，需输入RDS实例的外网端口。

    -   用户：RDS实例的初始账号名称。

    -   密码：RDS实例的初始账号所对应的密码。

12. 单击**确定**。
13. 在打开登录信息窗口，选中刚才创建的连接，单击**打开**，如下图所示。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7820/15329156082578_zh-CN.png)

14. 实例连接成功后，单击**SQL编辑器**，如下图所示。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7820/15329156082579_zh-CN.png)

15. 在SQL编辑器中输入如下命令：

    ```
    create database <database name> DEFAULT CHARACTER SET gbk COLLATE gbk_chinese_ci;
    ```

16. 单击**运行**按钮，如下图所示，完成创建数据库。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7820/15329156082580_zh-CN.png)

17. 在左侧目录树中右击**用户**，选择**新建** \> **用户**来创建普通账号，如下图所示。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7820/15329156082581_zh-CN.png)

18. 在信息标签页中，填写账号的名称、主机和密码，如下图所示。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7820/15329156082582_zh-CN.png)

19. 在权限标签页中，对该账号进行授权，如下图所示。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7820/15329156082583_zh-CN.png)

20. 单击**确定**，完成创建账号。
21. 双击**用户**，即可查询该实例下的所有账号。

