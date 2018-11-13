# 诊断慢SQL {#concept_v2y_4vn_wdb .concept}

您可以查看实例中最近1个月内的慢SQL信息，对于某些慢SQL，CloudDBA会提供相应的优化建议。本文将介绍如何诊断慢SQL。

## 前提条件 {#section_uyn_rvn_wdb .section}

目前仅如下版本实例支持此功能：

-   MySQL 5.7 高可用版
-   MySQL 5.6版
-   MySQL 5.5 高可用版
-   PostgreSQL 10.0版
-   PPAS 10.0版

**说明：** 共享型实例不支持CloudDBA。

## 操作步骤 {#section_cqs_svn_wdb .section}

1.  登录[RDS管理控制台](https://rds.console.aliyun.com/)。
2.  选择目标实例所在地域。
3.  单击目标实例ID，进入基本信息页面。
4.  在左侧导航栏中，选择**CloudDBA** \> **问题诊断**，进入问题诊断页面。
5.  选择**慢SQL**标签页。
6.  选择要查询的时间，单击**确定**，如下图所示。

    **说明：** 目前，系统只支持显示最近1个月内的慢SQL数据。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7906/15421018273062_zh-CN.png)

7.  若实例中有慢SQL，图示中会显示慢SQL产生的时间点和个数。单击图示中的慢SQL信息，其下方的列表中会显示慢SQL详情，如下图所示。

    **说明：** 将鼠标悬浮在某一时间点上，即可查看该时间点时的慢SQL个数。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7906/15421018273063_zh-CN.png)

8.  单击sql\_text栏中的慢SQL语句，如下图所示。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7906/15421018273064_zh-CN.png)

9.  单击**SQL优化建议**，即可查看系统给出的优化建议，如下图所示。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7906/15421018273065_zh-CN.png)


