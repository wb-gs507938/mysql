# 解决MDL锁导致无法操作数据库的问题 {#task_csn_5tt_4fb .task}

异常情况下的元数据锁MDL（metadata lock）会阻塞后续对表的操作，本文介绍通过DMS工具解决该问题。

MySQL 5.5版本开始，引入了MDL锁，用于解决或者保证DDL操作与DML操作之间的一致性，但是在部分场景下会出现阻塞，例如执行DML操作时执行ALTER操作、存在长时间查询时执行ALTER操作等等。

1.   使用DMS登录[RDS数据库](https://dms.console.aliyun.com/#/dms/login)。 

    **说明：** 网络地址:端口需要输入对应RDS实例的内网地址及内网端口，可在RDS实例基本信息页面查看。

2.  在首页上方选择**SQL操作** \> **SQL窗口**。 
3.  在命令行输入show full processlist;并执行，查看所有线程状态，在State列发现大量Waiting for table metadata lock即表示出现阻塞，在对应的Info列可以查看到是对哪个表的操作，找到正在对该表进行操作的会话，记下Id。 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/24465/154095104414301_zh-CN.png)

    **说明：** 这里需要找到的是一直在占用该表的会话，而不是正在等待MDL锁解除的会话，注意区分。可以根据State列的状态和Info列的命令内容来进行分析判断。

4.  在命令行输入killId数字，例如 kill 267，即可中断会话，解除MDL锁。 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/24465/154095104414302_zh-CN.png)


