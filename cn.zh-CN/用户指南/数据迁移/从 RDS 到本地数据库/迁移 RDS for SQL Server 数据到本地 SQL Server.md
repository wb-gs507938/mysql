# 迁移 RDS for SQL Server 数据到本地 SQL Server {#concept_dqz_lyv_ydb .concept}

阿里云数据库 SQL Server 版支持通过物理备份文件将云上数据迁移到本地数据库。

## 操作步骤 {#section_eyt_dzv_ydb .section}

1.  下载云数据库全量和增量物理备份文件 并上传至目标服务器。

    备份文件获取方法请参见 [下载数据备份和日志备份](intl.zh-CN/用户指南/备份与恢复/下载数据备份和日志备份.md#)。

    如果目标服务器可以访问源实例，您也可以使用`wegt "url"`下载备份文件。其中 url 为备份文件下载地址。

2.  下载完成后，解压全量物理备份文件和增量物理备份文件。

    备份文件的命名为 **数据库名+备份类型+日期时间+任务号.bak**，其中 **备份类型** 有三种：

    -   datafull：代表全量备份，如 **rdsumu2myfzbeai1\_datafull\_201402250050\_2250050.bak**
    -   datadiff：代表增量备份，如 **rdsumu2myfzbeai1\_datadiff\_201402260050\_2260050.bak**
    -   log：代表日志备份，如 **rdsumu2myfzbeai1\_log\_201402260050\_2260050.bak**
3.  获取解压后的全量备份文件和增量备份文件，本例以存放至如下路径为例。
    -   全量备份文件存放路径：d:\\backup\\rdsumu2myfzbeai1\_datafull\_201402250050\_2250050.bak
    -   增量备份文件存放路径：d:\\backup\\rdsumu2myfzbeai1\_datadiff\_201402260050\_2260050.bak
4.  登录本地 SQL Server 控制台，通过备份文件查询云数据库的文件逻辑名。

    ```
    restore filelistonly from disk='d:\backup\rdsumu2myfzbeai1_datafull_201402250050_2250050.bak'  
    go
    ```

    系统显示如下，红框中为数据文件逻辑名 data1 和日志文件逻辑名 log。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7989/6112_zh-CN.png)

5.  加载全量备份文件。

    ```
    restore database rdsumu2myfzbeai1 from disk='d:\backup\rdsumu2myfzbeai1_datafull_201402250050_2250050.bak' with   replace,norecovery,stats=10,  
    move 'data1' to 'd:\database\rdsumu2myfzbeai1\data\data1.mdf',  
    move 'log' to 'd:\database\rdsumu2myfzbeai1\log\log.ldf'  
    goo
    ```

    其中：

    -   *d:\\database\\rdsumu2myfzbeai1\\data* 为数据地址，data1.mdf为数据文件逻辑名
    -   *d:\\database\\rdsumu2myfzbeai1\\log* 为日志地址，log.ldf为日志文件逻辑名
    执行完成后，数据库 *rdsumu2myfzbeai1* 将显示 正在还原 状态。

    **说明：** 如果只需恢复全量备份数据，无需执行步骤 6，请直接跳至步骤 7。如果还需要恢复增量备份数据，请执行步骤 6。

6.  加载增量备份文件。

    ```
    restore database rdsumu2myfzbeai1 from disk='D:\backup\rdsumu2myfzbeai1_datadiff_201402260050_2260050.bak' with   replace,norecovery,stats=10,  
    move 'data1' to 'd:\database\rdsumu2myfzbeai1\data\data1.mdf',  
    move 'log' to 'd:\database\rdsumu2myfzbeai1\log\log.ldf'  
    go
    ```

    执行完成后，数据库 rdsumu2myfzbeai1 将显示正在还原状态。

7.  恢复数据库。

    ```
    restore database rdsumu2myfzbeai1 with recovery  
    go
    ```

    执行完成后，数据库rdsumu2myfzbeai1将显示可用状态。


