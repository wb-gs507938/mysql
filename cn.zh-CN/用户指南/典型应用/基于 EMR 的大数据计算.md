# 基于 EMR 的大数据计算 {#concept_bw3_n4x_wdb .concept}

E-MapReduce 是一项 Web 服务，简化了大数据处理，提供的大数据框架可以让您轻松、高速、经济、安全、稳定地处理大数据，满足如日志分析、数据仓库、商业智能、机器学习、科学模拟等业务需求。您可以运行 Hadoop、Spark 分析 RDS 中数据，也可以把分析完成的数据存放到 RDS 中，提供给在线系统使用。

通过 Sqoop 组件，可以实现 RDS 与 E-MapReduce 间数据的导入导出，实现大数据分析处理。

## 前提条件 {#section_eqw_1px_wdb .section}

-   已开通 E-MapReduce 服务，并完成项目设置。
-   E-MapReduce 版本从 1.3 开始都会默认支持 Sqoop 组件，所以您无需自行安装。

## 操作步骤 {#section_hjr_bpx_wdb .section}

我们这里主要介绍几个常见的数据导入导出场景：

1.  [从 MySQL 到 HDFS](#section_ajk_fpx_wdb)
2.  [从 HDFS 到 MySQL](#section_lj3_hpx_wdb)
3.  [从 MySQL 到 HDFS](#section_ajk_fpx_wdb)
4.  [从 HDFS 到 MySQL](#section_lj3_hpx_wdb)
5.  [使用 SQL 作为导入条件](#section_t5w_npx_wdb)

**说明：** 在执行下面的命令前，请先使用 `su hadoop` 命令切换你的用户为 Hadoop。

## 从 MySQL 到 HDFS {#section_ajk_fpx_wdb .section}

在集群的 Master 节点上执行如下命令：

```
sqoop import --connect jdbc:mysql://<dburi>/<dbname> --username <username> --password <password> --table <tablename> --target-dir <hdfs-dir>
```

参数说明如下：

-   dburi：数据库的访问连接，例如 jdbc:mysql://192.168.1.124:3306/
-   dbname：数据库的名字，例如 user
-   username：数据库登录用户名
-   password：用户对应的密码
-   tablename：MySQL 表的名字
-   hdfs-dir：hdfs 的写入目录，例如 /user/hive/result

详细的参数使用说明请参见 [Sqoop Import](http://sqoop.apache.org/docs/1.4.6/SqoopUserGuide.html?spm=a2c4g.11186623.2.9.6WqAfQ#_syntax)。

## 从 HDFS 到 MySQL {#section_lj3_hpx_wdb .section}

1.  创建好对应 HDFS 中的数据结构的 MySQL 表。
2.  在集群的 Master 节点上执行如下命令，指定要导出的数据文件的路径。

```
 sqoop export --connect jdbc:mysql://<dburi>/<dbname> --username <username> --password <password> --table <tablename> --export-dir <hdfs-dir>
```

-   dburi：数据库的访问连接，例如 jdbc:mysql://192.168.1.124:3306/
-   dbname：数据库的名字，例如 user
-   username：数据库登录用户名
-   password：用户对应的密码
-   tablename：MySQL 的表的名字
-   hdfs-dir：要导到 MySQL 去的 HDFS 的数据目录，例如 /user/hive/result

详细的参数使用说明请参见 [Sqoop Export](http://sqoop.apache.org/docs/1.4.6/SqoopUserGuide.html?spm=a2c4g.11186623.2.10.6WqAfQ#_syntax_4)。

## 从 MySQL 到 Hive {#section_cfv_jpx_wdb .section}

将数据导入 Hive 的同时也新建一个 Hive 表。

```
sqoop import --connect jdbc:mysql://<dburi>/<dbname> --username <username> --password <password> --table <tablename> --fields-terminated-by "\t" --lines-terminated-by "\n" --hive-import --target-dir <hdfs-dir> --hive-table <hive-tablename>
```

-   dburi：数据库的访问连接，例如 jdbc:mysql://192.168.1.124:3306/
-   dbname：数据库的名字，例如 user
-   username：数据库登录用户名
-   password：用户对应的密码
-   tablename：MySQL 的表的名字
-   hdfs-dir：要导到 MySQL 去的 HDFS 的数据目录，例如 /user/hive/result
-   hive-tablename：对应的 Hive 中的表名，可以是 xxx.yyy

详细的参数使用说明请参见 [Sqoop Import](http://sqoop.apache.org/docs/1.4.6/SqoopUserGuide.html?spm=a2c4g.11186623.2.11.6WqAfQ#_syntax)。

## 从 Hive 到 MySQL {#section_ofv_lpx_wdb .section}

请参见[从 HDFS 到 MySQL](cn.zh-CN/用户指南/典型应用/基于 EMR 的大数据计算.md#section_lj3_hpx_wdb)，只需要指定 Hive 表对应的 HDFS 路径即可。

## 使用 SQL 作为导入条件 {#section_t5w_npx_wdb .section}

除了指定 MySQL 的全表导入，还可以写 SQL 来指定导入的数据

```
sqoop import --connect jdbc:mysql://<dburi>/<dbname> --username <username> --password <password> --query <query-sql> --split-by <sp-column> --hive-import --hive-table <hive-tablename> --target-dir <hdfs-dir>
```

-   dburi：数据库的访问连接，例如 jdbc:mysql://192.168.1.124:3306/
-   dbname：数据库的名字，例如 user
-   username：数据库登录用户名
-   password：用户对应的密码
-   query-sql：使用的查询语句，例如 `SELECT * FROM profile WHERE id>1 AND \$CONDITIONS`。记得要用引号包围，最后一定要带上 `AND \$CONDITIONS`
-   sp-column：进行切分的条件，一般跟 MySQL 表的主键
-   hdfs-dir：要导到 MySQL 去的 HDFS 的数据目录，例如 /user/hive/result
-   hive-tablename：对应的 Hive 中的表名，可以是 xxx.yyy

详细的参数使用说明请参见 [Sqoop Query Import](http://sqoop.apache.org/docs/1.4.6/SqoopUserGuide.html?spm=a2c4g.11186623.2.13.6WqAfQ#_free_form_query_imports)。

集群和其他数据库的网络配置请参见 [用 Aliyun E-MapReduce 集群的 Sqoop 工具和数据库同步数据如何配置网络](https://yq.aliyun.com/articles/43799?spm=a2c4g.11186623.2.14.6WqAfQ)。

