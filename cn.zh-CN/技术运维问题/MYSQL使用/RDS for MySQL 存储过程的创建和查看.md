# RDS for MySQL 存储过程的创建和查看 {#concept_fyb_wld_n2b .concept}

## 1. 创建存储过程 {#section_atw_wld_n2b .section}

可以通过 DMS 或 MySQL 客户端登录到 RDS， 创建存储过程。示例代码如下：

```
DROP PROCEDURE IF EXISTS TEST_PROC;DELIMITER //CREATE PROCEDURE TEST_PROC(IN ID int,OUT NAME VARCHAR(50))BEGINIF(ID = 1) THEN SET NAME = ‘test1’;END IF;IF(ID = 2) THEN SET NAME = ‘test2’;END IF;SELECT version();END //; 
```

![](https://img.alicdn.com/tfscom/TB1N3lJKXXXXXbcXpXXXXXXXXXX.JPG)

## 2. 查看存储过程 {#section_htw_wld_n2b .section}

在 RDS for MySQL中，有两种方法查看数据库中的存储过程：

1、通过系统表查询

```
select * from mysql.proc where db=’‘ and type=’procedure’ order by name;
```

![](https://img.alicdn.com/tfscom/TB1GobhMXXXXXcZXpXXXXXXXXXX)

2. 登录到数据库中，执行命令：

```
show procedure status;show create procedure \G;
```

![](https://img.alicdn.com/tfscom/TB1NmBzKXXXXXb2XFXXXXXXXXXX.JPG)

![](https://img.alicdn.com/tfscom/TB1hVlAKXXXXXatXFXXXXXXXXXX.JPG)![](data:image/gif;base64,R0lGODlhAQABAPABAP///wAAACH5BAEKAAAALAAAAAABAAEAAAICRAEAOw==)

如问题还未解决，请联系[售后技术支持](https://selfservice.console.aliyun.com/ticket/createIndex.htm?spm=a2c4g.11186623.2.5.w2plu9)。

