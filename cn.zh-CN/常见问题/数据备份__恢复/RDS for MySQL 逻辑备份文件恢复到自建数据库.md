# RDS for MySQL 逻辑备份文件恢复到自建数据库 {#concept_zql_2c5_vfb .concept}

使用MySQL自带的 mysqldump 工具可以通过逻辑备份文件恢复数据库，本文将介绍详细的逻辑备份恢复数据库操作步骤。

**说明：** 

-   通过物理备份文件恢复到自建数据库请参见[RDS for MySQL 物理备份文件恢复到自建数据库](intl.zh-CN/常见问题/数据备份__恢复/RDS for MySQL 物理备份文件恢复到自建数据库.md#)。
-   关于云数据库MySQL版如何备份数据，请参见[备份 RDS 数据](../../../../intl.zh-CN/用户指南/备份数据/备份 RDS 数据.md#)。

## 注意事项 {#section_bd4_5gz_5fb .section}

本地MySQL数据库安装在64位的Linux系统中，且与云数据库MySQL版的版本相同。本文使用Linux7的操作系统以及MySQL5.7版本为例进行演示。

## 逻辑备份恢复操作步骤 {#section_lcm_tqt_vfb .section}

1.  登录[RDS管理控制台](https://rds.console.aliyun.com/)。
2.  在页面左上角，选择实例所在地域。
3.  找到目标实例，单击实例ID。
4.  在左侧导航栏中单击**备份恢复**。
5.  选择查询的时间范围，然后单击**查询**。
6.  在数据备份列表中，找到要下载的逻辑备份，并单击其右侧的**下载**。
7.  在实例备份文件下载窗口，单击**复制外网地址**，获取数据备份文件外网下载地址。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/64382/154510030332292_zh-CN.png)

8.  登录自建数据库所在Linux系统，执行如下命令下载逻辑备份文件。

    ```
    wget -c '<数据备份文件外网下载地址>' -O <自定义文件名>.tar
    ```

    **说明：** 

    -   -c：启用断点续传模式。
    -   -O：将下载的结果保存为指定的文件。
9.  执行如下命令解压缩逻辑备份文件，包括系统默认的数据库压缩文件以及自行创建的数据库压缩文件。

    ```
    tar xvf <数据备份文件名>.tar
    ```

10. 根据需要恢复的数据库再次解压缩对应的数据库压缩文件。

    ```
    gzip -d <数据库压缩文件名>.gz
    ```

11. 登录数据库创建对应的空数据库。

    ```
    #mysql -uroot -p<数据库密码>
    mysql> create database <数据库名>;
    Query OK, 1 row affected (0.00 sec)
    mysql> exit
    Bye
    ```

12. 使用如下命令将.sql文件导入对应数据库。

    ```
    mysql -uroot -p<数据库密码> <创建的空数据库名> < ~/<解压缩后数据库名\>.sql
    ```

13. 登录数据库后查看表，已经有了数据，说明已经迁移成功。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/64382/154510030332293_zh-CN.png)


