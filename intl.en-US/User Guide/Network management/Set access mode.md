# Set access mode {#concept_jlf_hpq_wdb .concept}

RDS supports two access modes: standard mode and safe connection mode. This article describes their differences and how to switch between them.

## Differences between standard mode and safe connection mode {#section_cf2_jxx_wdb .section}

-   Standard mode: RDS uses [Sever Load Balancer](https://www.alibabacloud.com/help/doc-detail/27539.htm) to eliminate the impact of database engine HA switching on the application layer. This shortens the response time, but may slightly increase the probability of transient disconnections. This mode supports only one connection address. If the instance has both an intranet address and an Internet address, release one of them before switching to the standard mode.

-   Safe connection mode: This mode prevents 90% of transient disconnections, but increases the response time by 20% or more. This mode supports coexistence of an intranet address and an Internet address.


## Attention {#section_tty_jxx_wdb .section}

-   MySQL 5.7, SQL Server 2012, and SQL Server 2016 instances support only the standard mode.

-   In a [VPC](https://www.alibabacloud.com/help/doc-detail/26194.htm) network, the access mode of MySQL 5.5/5.6 and SQL Server 2008 R2 must be the safe connection mode and cannot be switched.

    **Note:** MySQL 5.5/5.6 and SQL Server 2008 R2 instances in the China North 1 \(Qingdao\), China North 2 \(Beijing\), China East 1 \(Hangzhou\), and Hong Kong regions do not have this limit.

-   Switching the access mode may result in a disconnection of 30 seconds. To avoid the impact, perform the switching during off-peak hours, or make sure that your application has the automatic reconnection mechanism.


## Procedure {#section_vdj_lxx_wdb .section}

1.  Log on to the [RDS console](https://rdsnew.console.aliyun.com/console/index#/rdsList/).
2.  Select the region where the target instance is located.
3.  Click the ID of the target instance to enter the **Basic Information** page.
4.  Select **Connection Options** in the left-side navigation pane.
5.  On the Instance Connection tab page, click **Switch Access Mode**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7942/3256_en-US.png)

6.  Click **Confirm** on the dialog box to switch the access mode.

