# 设置MySQL循环执行事件 {#concept_akq_frc_wfb .concept}

## 背景信息 {#section_ivh_3w1_wfb .section}

使用 DMS 工具可以帮助您方便快捷地循环执行事件，本文以如下事件为例进行步骤的详细说明：

**ID为10的test1字段值每2分钟增加1**

## 前提条件 {#section_bd4_5gz_5fb .section}

用户登录的数据库必须开启事件支持，通过执行`SELECT @@event_scheduler;`命令来查看数据库是否支持事件：

-   若结果返回ON，说明数据库开启了事件支持。

-   若结果返回OFF，说明数据库未开启事件支持，执行`SET GLOBAL event_scheduler = ON;`命令来开启事件支持。


## 操作步骤 {#section_lcm_tqt_vfb .section}

1.  登录[RDS管理控制台](https://rds.console.aliyun.com/)。
2.  在页面左上角，选择实例所在的地域。
3.  找到目标实例，单击实例ID。
4.  在右上角单击**登录数据库**，使用高权限账号[登录数据库](https://help.aliyun.com/document_detail/64703.html)。
5.  在首页上方选择**创建** \> **事件**打开新建：事件页面。
6.  设置以下参数：

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/64573/154320188732558_zh-CN.png)

    |分类|参数|说明|
    |--|--|--|
    |事件基本信息|事件名称|事件的名称。|
    |到期后删除|     -   固定时间的事件执行后是否删除该事件。
    -   循环事件到结束时间后是否删除该事件。
 |
    |状态|事件的状态：    -   开启：事件处于可执行状态。
    -   禁用：事件处于暂时停止执行状态。
    -   从库禁用：只有主库可以执行事件。
|
    |注释|填写事件的详细注释。|
    |执行时间定义|固定时间|在固定时间执行一次事件。|
    |循环时间|每隔一段时间执行一次事件。**说明：** 这里的一段时间是由**时间单位的数量**+**时间单位**组成。

|
    |开始时间|循环事件的开始时间。|
    |结束时间|循环事件的结束时间。|
    |事件语句|-|具体的SQL语句。|

    **说明：** 设置循环事件时，对于间隔时间的设置举例如下：

    -   到达开始时间后，每2分钟执行一次事件。

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/64573/154320188732559_zh-CN.png)

    -   到达开始时间后，每1个月执行一次事件。

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/64573/154320188732560_zh-CN.png)

7.  单击**保存**，在弹出的确认框中确认SQL语句并单击**确定**。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/64573/154320188732561_zh-CN.png)

8.  在对应的数据库中使用`show events;`就可以查询到该循环事件。

    **说明：** 若要删除事件，可以使用`drop event <事件名称>;`命令。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/64573/154320188732562_zh-CN.png)


