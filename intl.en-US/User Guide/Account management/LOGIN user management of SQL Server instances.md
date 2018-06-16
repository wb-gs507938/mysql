# LOGIN user management of SQL Server instances {#concept_e3l_x2p_ydb .concept}

This document describes how to create and manage LOGIN users in a database of ApsaraDB for SQL Server.

**Note:** The operation described in this document is applicable only to instances of RDS SQL Server 2012 and later versions.

## Create a LOGIN user {#section_syq_dfp_ydb .section}

Run the following command to create a LOGIN user.

```
CREATE LOGIN Test11 WITH PASSWORD=N'4C9ED138-C8F5-4185-9E7A-8325465CA9B7'
```

When creation is in progress, the LOGIN user is assigned permissions at the server level and database level. The Message area shows the following information.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7932/4174_en-US.jpg)

## Modify LOGIN {#section_slg_gfp_ydb .section}

Run the following command to modify a LOGIN user.

```
ALTER LOGIN Test11 WITH PASSWORD=N'123',CHECK_POLICY=OFF
```

The following error is returned if you attempt to modify a LOGIN user not created by you.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7932/4175_en-US.jpg)

## Delete a LOGIN user {#section_b1k_jfp_ydb .section}

Run the following command to delete a LOGIN user.

`DROP LOGIN Test11`

An error is returned if you attempt to delete a LOGIN user not created by you.

