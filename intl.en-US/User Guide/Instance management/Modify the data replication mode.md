# Modify the data replication mode {#concept_dq5_xfj_wdb .concept}

For MySQL 5.5/5.6/5.7 instance, you can select its data replication mode based on your business characteristics to improve the availability of the RDS instance. This document introduces how to change the data replication mode.

## Background information {#section_m5d_cgj_wdb .section}

MySQL 5.5/5.6/5.7 instances support two replication modes: semi-sync and async. You can select an appropriate replication mode as your business needs. The differences and features of the replication modes are described as follows.

-   Semi-sync mode: Normally data is replicated in the sync mode. But if an exception occurs when the master node replicates data to the slave node, the data synchronization logic changes to the following:
    -   When the slave node is unavailable or any network exception occurs between the master and slave nodes, the master node suspends response to applications until the replication mode times out and degrades to the async mode.
    -   When data replication between the two nodes resumes normally \(the slave node or network connection is recovered\), async mode is changed to sync mode. The time period required for restoration to the sync mode depends on the implementation mode of the semi-sync mode. ApsaraDB for MySQL 5.5 differs from ApsaraDB for MySQL 5.6 in this regard.
-   Async mode: An application initiates an update \(including addition, deletion, and modification operations\) request. After completing the corresponding operation, the master node immediately responds to the application and then replicates data to the slave node asynchronously.  Therefore, in the async mode, unavailability of the slave node does not affect the operation on the slave database, and unavailability of the master node has a low probability to cause data inconsistency between the two nodes.

## Procedure {#section_gtn_dgj_wdb .section}

1.  Log on to the  [RDS console](https://rds.console.aliyun.com/).
2.  Select the region where the target instance is located.
3.  Click the ID of the target instance to visit the Basic Information page.
4.  In the left-side navigation pane, select **Instance Availability**.
5.  Click **Modify Data Replication Mode**, as shown in the following figure.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7886/15475420166107_en-US.png)

6.  In the Modify Data Replication Mode dialog box, select a data replication mode, as shown in the following figure.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7886/15475420166108_en-US.png)

7.  Click **OK**.

