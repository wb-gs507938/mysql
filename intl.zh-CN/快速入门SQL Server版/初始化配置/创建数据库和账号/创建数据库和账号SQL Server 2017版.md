# 创建数据库和账号SQL Server 2017版 {#concept_d2l_nlh_wfb .concept}

若要使用云数据库RDS，您需要在实例中创建数据库和账号。对于SQL Server 2012版本的实例，您需要通过RDS控制台创建一个初始账号，然后通过客户端创建和管理数据库。本文将以Microsoft SQL Server Management Studio（SSMS）17.1版本的客户端为例介绍如何在SQL Server 2012版本的实例中创建数据库和账号的操作步骤。

**说明：** 本文仅适用于SQL Server 2012版本的实例。关于如何在SQL Server 2008 R2版本的实例中创建数据库和账号，请参见文档[创建数据库和账号SQL Server 2008 R2版](intl.zh-CN/快速入门SQL Server版/初始化配置/创建数据库和账号/创建数据库和账号SQL Server 2008 R2版.md#)。

## 注意事项 {#section_ash_fph_wfb .section}

-   同一实例下的数据库共享该实例下的所有资源。您可以通过SQL命令管理普通账号和数据库。

-   分配数据库账号权限时，请按最小权限原则和业务角色创建账号，并合理分配只读和读写权限。必要时可以把数据库账号和数据库拆分成更小粒度，使每个数据库账号只能访问其业务之内的数据。如果不需要数据库写入操作，请分配只读权限。

-   为保障数据库的安全，请将数据库账号的密码设置为强密码，并定期更换。


## 操作步骤 {#section_csh_fph_wfb .section}

1.  登录[RDS管理控制台](https://rds.console.aliyun.com/)。
2.  选择目标实例所在地域。
3.  单击目标实例的ID，进入基本信息页面。
4.  在左侧导航栏中，选择**账号管理**，进入账号管理页面。
5.  单击**创建初始账号**。
6.  输入要创建的账号信息。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/64588/154285354932576_zh-CN.png)

    参数说明：

    -   **数据库账号**：长度为2~16个字符，由小写字母、数字或下划线组成。但开头需为字母，结尾需为字母或数字。

**说明：** test、root等为保留关键字，不能设置为账号名。

    -   **密码**：该账号对应的密码。由大写字母、小写字母、数字、特殊字符中的任意三种组成；特殊字符为!@\#$%^&\*\(\)\_+-=；长度为8~32个字符。

    -   **确认密码**：输入与密码一致的字段，以确保密码正确输入。

7.  单击**确定**。
8.  将要访问RDS实例的IP地址加入RDS白名单中。关于如何设置白名单，请参见[设置白名单](../../../../intl.zh-CN/快速入门MySQL版/初始化配置/设置白名单.md#)。
9.  启动Microsoft SQL Server Management Studio客户端。
10. 新建连接信息，如下图所示。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7839/15428535492775_zh-CN.png)

    参数说明：

    -   **服务器类型**：选择**数据库引擎**。

    -   **服务器名称**：由RDS实例的内网或外网地址和端口号组成，网络地址与端口号之间用英文状态的逗号隔开，如`rm-bptest.sqlserver.rds.aliyuncs.com,3433`。查看RDS实例的内外网地址及端口信息的步骤如下：

        1.  登录[RDS管理控制台](https://rds.console.aliyun.com/)。
        2.  选择目标实例所在地域。
        3.  单击目标实例的ID，进入基本信息页面。
        4.  在基本信息栏中，即可查看内外网地址及内外网端口信息。

            ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7839/15428535492776_zh-CN.png)

    -   **身份验证**：选择**SQL Server身份验证**。

    -   **登录名**：要访问RDS实例的账号名称。

    -   **密码**：要访问RDS实例的账号所对应的密码。

11. 单击**连接**。
12. 右击**数据库**，选择**新建数据库**。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7839/15428535492777_zh-CN.png)

13. 在新建数据库页面的数据库名称栏中输入要新建的数据库名称，单击**确定**。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7839/15428535492778_zh-CN.png)

14. 数据库创建成功后，您可以在左边的目录树中找到新建的数据库。

    **说明：** 请不要在系统数据库中进行任何操作。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7839/15428535502779_zh-CN.png)

15. 选择**安全性**，右击**登录名**，选择新建登录名，如下图所示，即可创建该实例下的普通账号。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7839/15428535502780_zh-CN.png)

16. 填写账号名称和密码，并选择账号的默认数据库。

    **说明：** 身份验证请选择**SQL Server身份验证**，其他密码策略请根据需要自行调整。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7839/15428535502782_zh-CN.png)

17. 单击**确定**。
18. 普通账号创建完成后，您可以在左边的目录树中查看该新建账号。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7839/15428535502783_zh-CN.png)

19. 双击该账号，即会开启该账号的登录属性页面。您可以在服务器角色页面对该账号授权并在用户映射页面绑定数据库。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7839/15428535502784_zh-CN.png)

20. 单击**确定**。

