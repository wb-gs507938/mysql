# Manage read-only instances {#concept_nhh_ls5_vdb .concept}

You can manage the read-only instances through the RDS console. Read-only instances are managed similarly to the regular instances. The executable management operations are subject to the actual interface. This article describes how to enter the management interface for read-only instances and how to view the synchronization delay of read-only instances.

## Enter the management interface directly through the read-only instance {#section_b4j_v55_vdb .section}

1.  Log on to the [RDS console](https://rds.console.aliyun.com/).
2.  Select the region where the target read-only instance is located.
3.  Click the ID of the target read-only instance to enter its management interface.

    **Note:** On the Instances page, the instance ID marked with an R indicates a read-only instance, as shown in the following figure.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7828/2634_en-US.png)


## Enter the management interface through the master instance { .section}

1.  Log on to the [RDS console](https://rds.console.aliyun.com/).
2.  Select the region where the target master instance is located.
3.  Click the ID of the target master instance to enter the Basic Information page.
4.  In the Instance Distribution area, put the mouse over the number of the read-only instance, and then the instance IDs are displayed, as shown in the following figure:

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7828/2635_en-US.png)

5.  Click the ID of the target read-only instance to enter its management interface.

## View the data synchronization delay of read-only instance {#section_sww_dv5_vdb .section}

When synchronizing data from the master instance, the read-only instance may delay for some time. You can view the delay on the Basic Information page of the read-only instance, as shown in the following figure:

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7828/2636_en-US.png)

