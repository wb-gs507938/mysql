# 通过数据传输服务（DTS）将RDS的数据实时同步至DataHub {#concept_udx_nyx_gfb .concept}

为了让数据可以实时进入流计算等大数据产品进行数据实时分析，您可以使用数据传输服务（DTS）将RDS数据实时同步到 DataHub。

## 准备工作 {#section_krh_yzx_gfb .section}

-   创建一个数据库和表，您可以选择使用阿里云的RDS数据库，也可以在本地服务器上自建数据库。本案例以**华东1**区的RDS MySQL数据库为例，数据库表的名称为datav\_test，字段及数据如下图所示。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/21843/153802936112934_zh-CN.png)

-   登录[阿里云Datahub控制台](https://datahub.console.aliyun.com/datahub)，选择**华东1**，单击**创建Project**，创建一个DataHub项目（本案例的项目名称为dts\_test）。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/21843/153802936112936_zh-CN.png)


## 数据同步 {#section_jzn_bcy_gfb .section}

1.  进入[阿里云DTS控制台](https://dts.console.aliyun.com)，单击左侧菜单栏中的**数据同步**。
2.  单击**创建同步作业**，购买数据传输服务实例，配置如下图所示。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/21843/153802936112941_zh-CN.png)

    **说明：** 

    -   **源实例**选择MySQL，**目标实例**选择Datahub。
    -   源实例区域和目标实例区域以及同步作业实例区域需保持一致。
3.  购买成功后，返回控制台，单击实例右侧的**配置同步链路**。
4.  选择同步通道的源及目标实例，如下图所示，完成后单击**授权白名单并进入下一步**。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/21843/153802936112945_zh-CN.png)

5.  选择同步对象。选择需要同步的表，单击![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/21843/153802936112947_zh-CN.png)图标按钮。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/21843/153802936112946_zh-CN.png)

6.  单击**预检查并启动**，启动预检查。如果预检查成功，系统会显示如下对话框。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/21843/153802936112948_zh-CN.png)

7.  单击**关闭**，返回数据同步页面，单击页面右上角的**刷新**，查看实例状态。此时正常情况下，实例的状态应该显示为初始化中。

    **说明：** 初始化的时间依赖于同步表的数量大小。

8.  当初始化完成后，同步链路即进入同步中的状态，此时源跟目标实例的同步链路才真正建立完成。单击页面右上角的**刷新**，查看实例的同步概况。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/21843/153802936112949_zh-CN.png)

9.  进入[阿里云Datahub控制台](https://datahub.console.aliyun.com/datahub)，单击项目右侧的**查看**，进入Topics页面，可以看到已经同步完成的表的名称即为topic的名称。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/21843/153802936312950_zh-CN.png)

10. 单击topic右侧的**查看**，选择Schema页签，查看已经同步完成的表的结构。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/21843/153802936312951_zh-CN.png)


## 数据采集 {#section_ogf_b3y_gfb .section}

由于DataHub同步的是增量数据，因此您必须在数据库中增加一条或多条数据，才能同步到DataHub中。此案例采用手动插入数据的方式，仅作为参考，在实际应用中，您表中的数据应该是实时写入的。

1.  登录您的数据库，在表中插入一条数据，如下图所示。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/21843/153802936312952_zh-CN.png)

2.  回到[阿里云Datahub控制台](https://datahub.console.aliyun.com/datahub)，查看刚才的项目，单击topic右侧的**查看**，选择Shards页签。
3.  单击某个shard右侧的**数据抽样**。
4.  在Shard数据抽样页面，指定一个时间，单击**抽样**，查看数据同步结果。

    **说明：** Shard数据抽样的时间要小于等于**最新数据时间**，否则无法抽取数据。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/21843/153802936312953_zh-CN.png)


## 常见问题 {#section_a3d_y3y_gfb .section}

1.  DTS 数据同步失败，如何处理？

    可能原因：同步链路规格配置不合适导致。

    解决方法：参考[数据同步规格说明](https://help.aliyun.com/document_detail/26605.html)，选择合适的规格，重新创建同步作业。

2.  Datahub 中单击数据抽样，抽样数据为空，如何处理？

    可能原因：

    -   指定的时间大于**最新数据时间**。
    -   数据库中不存在增量数据。
    解决方法：

    1.  在进行数据抽样时，设置指定的时间小于等于**最新数据时间**，再次单击**抽样**，若数据不为空，问题解决，若数据为空，执行下一步。
    2.  在您的数据库中插入一条或多条数据，重新回到DataHub控制台，对数据进行抽样。

        如果问题仍然无法解决，请在控制台上提交工单，或者直接联系阿里云技术支持工程师。


