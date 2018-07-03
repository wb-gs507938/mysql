# Switch master/slave instance {#concept_ftz_42j_wdb .concept}

Once the RDS instance is created successfully, the system automatically creates a free slave instance for it. The slave instance is located in the same region, where the master instance is located, but in a different zone.

The data in the master instance synchronizes to the slave instance in real time. You can only access the master instance. The slave instance exists only as a backup. However, when the rack \(where the master instance is located\) encounters an error, the master and slave instances can be switched. After the handover, the original master instance becomes a backup instance, and the rack-level disaster tolerance can be realized.

This document describes how to switch the master/slave instance.

## Attention {#section_bwn_r2j_wdb .section}

-   Currently this operation is not applicable to the Basic Edition of MySQL 5.7 and SQL Server 2012/2016 instances. This is because Basic Edition instances do not have slave nodes.

-   Switching the master/slave instance may result in transient disconnection. Make sure that your application has a reconnection configuration.


## Procedure {#section_qjt_s2j_wdb .section}

1.  Log on to the  [RDS console](https://rds.console.aliyun.com/).
2.  Select the region where the target instance is located, and click the ID of a target instance.
3.  In the left-side navigation pane, select **Instance Availability**.
4.  In the Availability Information area, click **Switch Master/Slave Instance**.
5.  Select **Switch now** or **Switch within maintenance period**.

    **Note:** During the switching, many operations cannot be performed. Therefore, we recommend that you choose to switch within the maintenance period.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7885/3021_en-US.png)

6.  If necessary, you can change the maintenance period as follows:
    1.  Click **Modify** to open the Basic Information page.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7885/3022_en-US.png)

    2.  In the Configuration Information area at the lower left corner, select a maintenance period and click **Save**.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7885/3023_en-US.png)

    3.  Go back to the page for master/slave switchover.
7.  Click **OK**.

