# Upgrade the database {#concept_gnx_vgj_wdb .concept}

## Background information {#section_jqq_2hj_wdb .section}

RDS allows you to upgrade a database rather than downgrade it. See the console interface for upgradeable versions.

## Attention {#section_b5p_fhj_wdb .section}

-   Currently, this operation applies only to upgrades from MySQL 5.5 to MySQL 5.6 in the database.

-   We recommend that you firstly purchase an instance with the database version you want to upgrade to and test its compatibility before upgrading.

-   During the database upgrading process, the RDS service may flash off for about 30 seconds. To avoid the impacts on your production, we recommend that you upgrade the database at the low peak of the service, or make sure that your application has the automatic reconnection policy.


## Procedure {#section_or5_ghj_wdb .section}

1.  Log on to the  [RDS console](https://rds.console.aliyun.com/).
2.  Select the region where the target instance is located.
3.  Click the ID of the target instance to enter the Basic Information page.
4.  In the Configuration Information area, click **Upgrade Database**, as shown in the following figure.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7888/3026_en-US.png)

5.  On the Database Version Upgrade page, select the target database version and click **Start Upgrade**.

