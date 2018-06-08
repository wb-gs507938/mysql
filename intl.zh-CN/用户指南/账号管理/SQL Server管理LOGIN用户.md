# SQL Server管理LOGIN用户 {#concept_e3l_x2p_ydb .concept}

本文将介绍如何使用SQL命令在RDS SQL Server数据库中创建和管理LOGIN用户。

**说明：** 本文仅适用于RDS SQL Server 2012及以上版本的实例。

## 创建LOGIN用户 {#section_syq_dfp_ydb .section}

执行如下命令，创建LOGIN用户：

```
CREATE LOGIN Test11 WITH PASSWORD=N'4C9ED138-C8F5-4185-9E7A-8325465CA9B7'
```

在创建过程中，LOGIN用户会被授予服务器级、数据库级等权限，您会在**Message**（消息）栏中看到如下信息：

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7932/4174_zh-CN.jpg)

## 更改LOGIN用户信息 {#section_slg_gfp_ydb .section}

执行如下命令，更改LOGIN用户的信息：

```
ALTER LOGIN Test11 WITH PASSWORD=N'123',CHECK_POLICY=OFF
```

您只能修改您创建的LOGIN用户，否则将会出现如下错误：

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7932/4175_zh-CN.jpg)

## 删除LOGIN用户 {#section_b1k_jfp_ydb .section}

执行如下命令，删除LOGIN用户：

`DROP LOGIN Test11`

您只能删除您创建的LOGIN用户，否则会报错。

