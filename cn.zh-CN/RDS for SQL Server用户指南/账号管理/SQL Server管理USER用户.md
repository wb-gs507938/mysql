# SQL Server管理USER用户 {#concept_gq4_5fp_ydb .concept}

您只能在自己创建的用户数据库中创建普通用户，无法在系统数据库中创建用户。本文将介绍如何使用SQL命令在RDS SQL Server数据库中创建和管理USER。

**说明：** 本文仅适用于RDS SQL Server 2012及以上版本的实例。

## 前提条件 {#section_l34_xfp_ydb .section}

-   已创建用户数据库。关于创建数据库的命令，请参见[SQL命令管理数据库](cn.zh-CN/RDS for SQL Server用户指南/数据库管理/SQL命令管理数据库.md#)。

-   已创建LOGIN用户，并登录到要创建普通用户的数据库中。关于创建LOGIN用户的命令，请参见[SQL Server管理LOGIN用户](cn.zh-CN/RDS for SQL Server用户指南/账号管理/SQL Server管理LOGIN用户.md#)。


## 创建USER用户 {#section_dlq_yfp_ydb .section}

执行如下命令，在数据库TestDB中创建USER用户。

```
USE TestDB
GO
CREATE USER [Test] FOR LOGIN [Test]
```

## 更改USER用户信息 {#section_xg3_1gp_ydb .section}

您可以更改USER用户的信息，与SQL Server原始的操作方法相同。

```
USE TestDB
GO
ALTER USER test WITH LOGIN=test
```

## 删除USER用户 {#section_g3r_cgp_ydb .section}

执行如下命令，以删除USER用户，与SQL Server原始的操作方法相同。

```
USE TestDB
GO
DROP USER test
```

