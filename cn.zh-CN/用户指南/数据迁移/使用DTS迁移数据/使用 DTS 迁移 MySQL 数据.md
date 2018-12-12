# 使用 DTS 迁移 MySQL 数据 {#concept_nm3_xrv_ydb .concept}

使用数据传输服务（DTS）将本地数据库迁移到 RDS for MySQL，可以实现应用不停服务的情况下，平滑完成数据库的迁移工作。

## 背景信息 {#section_g2h_msv_ydb .section}

DTS 数据迁移支持 MySQL 的结构迁移、全量迁移和增量迁移。

-   结构迁移

    DTS 会将本地数据库的结构定义迁移到目标实例。目前 DTS 支持结构迁移的对象有：表、视图、触发器、存储过程、存储函数。

-   全量迁移

    DTS 会将本地数据库迁移对象的数据全部迁移到目标实例。如果用户还选择了增量迁移，那么全量迁移过程中，为了保证数据一致性，无主键的非事务表会被锁定，锁定期间这些表无法写入，锁定时长依赖于这些表的数据量大小，在这些无主键非事务表迁移完成后，锁才会释放。

-   增量迁移

    增量迁移会将迁移过程进行数据变更同步到目标实例，如果迁移期间进行了 DDL 操作，那么这些结构变更不会迁移到目标实例。


## 迁移限制 {#section_fn3_nsv_ydb .section}

将本地数据库迁移到 RDS 上有以下限制。

-   迁移过程中，不支持 DDL 操作。
-   结构迁移不支持 event 的迁移。
-   如果使用了对象名映射功能后，依赖这个对象的其他对象可能迁移失败。
-   当选择增量迁移时，本地 MySQL 实例需要开启 binlog，且本地库的 binlog\_format 要为 row。如果本地 MySQL 为5.6版本时，它的 binlog\_row\_image 还须设置为 full。
-   迁移后的表不区分大小写，统一变为小写。

## 前提条件 {#section_grd_4sv_ydb .section}

已完成 RDS 实例数据库的准备，可参见[申请外网地址](../../../../cn.zh-CN/快速入门MySQL版/初始化配置/申请外网地址.md#)和 [创建账号和数据库](../../../../cn.zh-CN/快速入门MySQL版/初始化配置/创建账号和数据库.md#)。

## 操作步骤 {#section_lwy_4sv_ydb .section}

本例以有公网 IP 的本地数据库迁移到 RDS 上为例。

**准备本地数据**

在正式迁移之前，需要先在本地数据库和 RDS 实例中创建迁移账号，并在 RDS 实例中创建要迁移的数据库，并将要迁移的数据库的读写权限授权给迁移账号。不同的迁移类型需要不同的权限，如下表所示。

|迁移类型|结构迁移|全量迁移|增量迁移|
|----|----|----|----|
|本地数据库|select|select|select replication slave replication client|
|RDS 实例|读写权限|读写权限|读写权限|

1.  在本地数据库中创建迁移账号。

    ```
    CREATE USER 'username'@'host' IDENTIFIED BY 'password';
    ```

    参数说明：

    -   username：要创建的账号
    -   host：指定该账号登录数据库的主机。如果是本地用户可以使用 localhost，如果想让该用户从任意主机登录，可以使用通配符 %
    -   password：该账号的登录密码
    例：要创建账号为 William，密码为 Changme123 的账号从任意主机登录本地数据库，命令如下：

    ```
    CREATE USER 'William'@'%' IDENTIFIED BY 'Changme123';
    ```

2.  在本地数据库中给迁移账号授权，本地数据库中迁移账号的权限要求请参见上表。

    ```
    GRANT privileges ON databasename.tablename TO 'username'@'host' WITH GRANT OPTION;
    ```

    参数说明：

    -   privileges：该账号的操作权限，如 SELECT、INSERT、UPDATE 等。如果要授权该账号所有权限，则使用 ALL
    -   databasename：数据库名。如果要授权该账号所有的数据库权限，则使用通配符 *\**
    -   tablename：表名。如果要授权该账号所有的表权限，则使用通配符 \*
    -   username：要授权的账号名
    -   host：授权登录数据库的主机名。如果是本地用户可以使用 localhost，如果想让该用户从任意主机登录，可以使用通配符 %
    -   WITH GRANT OPTION：授权该账号能使用GRANT命令，该参数为可选
    例：授权账号 William 对所有数据库和表的所有权限，并可以从任意主机登录本地数据库，命令如下：

    ```
    GRANT ALL ON *.* TO 'William'@'%';
    ```

    **说明：** 如果需要进行增量迁移，那么需要确认本地数据库的 binlog 是否开启并正确设置，执行以下步骤。

3.  开启本地数据库的 binlog。

    使用如下命令查询是否开启了binlog。

    ```
    show global variables like "log_bin";
    ```

    如果查询结果为 log\_bin=OFF，那么本地数据库没有开启 binlog。为了使迁移过程中产生的增量数据能同步迁移，需要修改配置文件 **my.cnf** 中的如下参数。

    ```
    log_bin=mysql_bin
    binlog_format=row
    server_id=大于 1 的整数
    binlog_row_image=full //当本地 MySQL 版本大于 5.6 时，则需设置该项
    ```

4.  修改完成后，重启 MySQL 进程。

    ```
    $mysql_dir/bin/mysqladmin -u root -p shutdown
    $mysql_dir/bin/safe_mysqld &
    ```

    其中，“mysql\_dir”为MySQL安装目录。


**正式迁移操作**

数据准备完毕后，即可进入正式的迁移操作。

1.  进入[DTS管理控制台](http://dts.console.aliyun.com/)。
2.  在左侧选择**数据迁移**，然后单击 **创建迁移任务**。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7977/15446079024264_zh-CN.png)

3.  输入任务名称、本地数据库信息和目标数据库信息，单击 **授权白名单并进入下一步**，如下图所示。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7977/15446079024265_zh-CN.png)

    -   任务名称：自定义任务名称，可以保持默认值。
    -   源库信息
        -   实例类型：本地数据库的实例类型，可以选择有公网IP的自建数据库、ECS上的自建数据库、RDS实例、云数据库MongoDB
        -   数据库类型：本地数据库的类型，可以选择 Oracle、MySQL、SQLServer、PostgreSQL、MongoDB
        -   主机名或 IP 地址：本地数据库所在设备的公网地址
        -   端口：本地数据库的公网端口
        -   账号：本地数据库的迁移账号
        -   密码：本地数据库迁移账号对应的密码
    -   目标库信息
        -   实例类型：默认为 *RDS 实例*
        -   RDS 实例 ID：目标 RDS 实例的 ID。点击下拉菜单将自动联想当前登录 [RDS 管理控制台](https://rds.console.aliyun.com/) 的账号的 RDS 实例，点击选择所需要的实例
        -   账号：目标 RDS 数据库的迁移账号
        -   密码：目标 RDS 数据库迁移账号对应的密码
4.  择迁移类型，并在 迁移对象 中选择要迁移的对象，单击 **\>** 将要迁移的对象放入已选择中，单击 **预检查并启动**，如下图所示。

    **说明：** 数据迁移只会将本地数据库的数据（结构）复制一份到目标数据库，并不会对本地数据库数据（结构）造成影响。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7977/15446079024266_zh-CN.png)

    如果要修改迁移对象在目标数据库上的名字，可以在 *已选择* 列表右侧单击 **编辑**，修改已选择的对象名称，如上图4所示。

    **说明：** 以下以预检查不通过为例进行描述，如果预检查通过，请直接参见步骤 8。

5.  系统显示预检查结果，如下图所示。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7977/15446079034267_zh-CN.png)

6.  单击检测结果 为**失败**的检测项后的 **!**，查看失败详细信息，根据失败详细信息完成错误排查。
7.  错误排查完毕后，在 迁移任务列表页面，选择当前迁移任务，单击 **启动**，如下图所示。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7977/15446079034268_zh-CN.png)

8.  系统预检查通过后，单击**确定**，自动进行迁移任务，如下图所示。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7977/15446079034269_zh-CN.png)


## 后续操作 {#section_sjb_mtv_ydb .section}

因迁移账号拥有读写权限，为了保证本地数据库安全，请在数据迁移完成后，删除本地数据库和 RDS 实例中的迁移账号。

