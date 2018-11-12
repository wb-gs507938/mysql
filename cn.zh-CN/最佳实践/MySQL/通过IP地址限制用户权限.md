# 通过IP地址限制用户权限 {#task_cz5_gpl_sfb .task}

在白名单上放通多个IP地址的情况下，会导致同一个用户在这些IP地址内部拥有相同权限，在安全性上有较大缺陷。例如某个账号由于安全性要求只允许在总公司登录，分公司只能使用只读权限的账号登录。

[创建高权限账号](https://help.aliyun.com/document_detail/87038.html)。

1.   登录[RDS管理控制台](https://rds.console.aliyun.com/)。 
2.   在页面左上角，选择实例所在的地域。 
3.   找到目标实例，单击实例ID。 
4.  在右上角单击**登录数据库**，使用高权限账号[登录数据库](https://help.aliyun.com/document_detail/64703.html)。 
5.   单击**SQL操作** \> **SQL窗口**。 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/60906/154198779830625_zh-CN.png)

6.  通过以下命令创建新用户并授权管理数据库，允许用户通过某IP地址访问数据库，此账号在控制台上无法查看到所属数据库。 

    **示例**

    创建新用户test001并授权管理rds001数据库，允许从42.120.74.119访问数据库。

    ```
    CREATE USER `test001`@`42.120.74.119`IDENTIFIED BY 'passwd';
    GRANT PROCESS, REPLICATION SLAVE, REPLICATION CLIENT ON *.* TO 'test001'@'42.120.74.119';
    GRANT ALL PRIVILEGES ON `rds001`.* TO 'test001'@'42.120.74.119';
    GRANT SELECT ON `mysql`.`help_topic` TO 'test001'@'42.120.74.119';
    GRANT SELECT ON `mysql`.`func` TO 'test001'@'42.120.74.119';
    GRANT SELECT ON `mysql`.`time_zone` TO 'test001'@'42.120.74.119';
    GRANT SELECT ON `mysql`.`slow_log` TO 'test001'@'42.120.74.119';
    GRANT SELECT ON `mysql`.`time_zone_transition` TO 'test001'@'42.120.74.119';
    GRANT SELECT ON `mysql`.`event` TO 'test001'@'42.120.74.119';
    GRANT SELECT ON `mysql`.`proc` TO 'test001'@'42.120.74.119';
    GRANT SELECT ON `mysql`.`help_category` TO 'test001'@'42.120.74.119';
    GRANT SELECT ON `mysql`.`help_relation` TO 'test001'@'42.120.74.119';
    GRANT SELECT ON `mysql`.`help_keyword` TO 'test001'@'42.120.74.119';
    GRANT SELECT ON `mysql`.`general_log` TO 'test001'@'42.120.74.119';
    GRANT SELECT ON `mysql`.`time_zone_leap_second` TO 'test001'@'42.120.74.119';
    GRANT SELECT ON `mysql`.`time_zone_transition_type` TO 'test001'@'42.120.74.119';
    GRANT SELECT ON `mysql`.`time_zone_name` TO 'test001'@'42.120.74.119';
    ```

    **说明：** 

    -   如果将所有的42.120.74.119更改为%，就和通过控制台创建的账号一样了，也可以在控制台看见此账号的所属数据库。
    -   如果想要修改IP为42.120.74.120，可以使用如下命令：

        ```
        RENAME USER `test001`@`42.120.74.119` TO `test001`@`42.120.74.120`;
        ```


