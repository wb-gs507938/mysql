# Create a clone instance {#concept_vrh_qp4_ydb .concept}

To restore historical data of an instance \(such as Instance A\), you can restore the data to a clone instance, verify the data on the clone instance, and transfer the data you need from the clone instance to the master instance \(Instance A\). This article describes how to restore data to a clone instance by creating a clone instance. The restored data includes instance data and settings. Clone instances are managed and billed in the same way as the master instance. For information about the cost of instances For more information, see the Pricing page.

**Note:** Currently, the following RDS versions support clone instances:

-   MySQL 5.5, 5.6, 5.7 master instances \(except MySQL 5.7 Basic Edition instances\)
-   SQL Server 2016 High-availability Edition \(including Standard and Enterprise Editions\)
-   SQL Server 2012 High-availability Edition \(including Standard and Enterprise Editions\)

## Background information {#section_f1x_w44_ydb .section}

You can specify a backup set or any time point within the backup period to create a clone instance. Clone instances only copy the content of the master instance. They do not copy the content of read-only instances or disaster recovery instances under the master instance. The copied content includes information about databases, accounts, and instance settings \(such as whitelists, backup settings, parameters, and alarm thresholds\).

The database engine of a clone instance must be the same as that of the master instance. Other settings can be different, such as the billing method, instance series, zone, network type, instance specifications, and storage capacity. If a clone instance is used to recover data of the master instance, we recommend that the clone instance is configured with higher specifications and storage capacity than the master instance. Otherwise, the recovery may take a long time.

The accounts of the clone instance are the same as those of the master instance, but you can modify the account passwords. For example, if you create a clone instance for a master instance that uses a master account, the clone instance also uses the master account.

## Prerequisites {#section_o5q_1p4_ydb .section}

The master instance must meet the following conditions:

-   The instance status is running and unlocked.
-   No migration task is ongoing.
-   Data backup and log backup are enabled.
-   If the clone instance is to be created from a backup set, the master instance must have at least one backup set.

    **Note:** To use a sub-account to create a clone instance, ensure that the sub-account has added authorization policies for the clone instance. For details about how to authorize, see [Authorization for RDS instances](https://partners-intl.aliyun.com/help/doc-detail/58932.htm).


## Procedure {#section_est_dp4_ydb .section}

1.  Log on to the [RDS console](https://partners-intl.console.aliyun.com/#/rds).
2.  Select the region where the target instance is located.
3.  Click the ID of the target instance to go to the **Basic Information** page.
4.  In the left-size navigation pane, click **Backup and Recovery**.
5.  At the upper-right corner of the page, click **Restore Database**.
6.  Select a payment method: **Subscription** or **Pay-As-You-Go**.
7.  Configure the clone instance.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7967/15428894594137_en-US.png)

    Parameter descriptions:

    |Parameter Name|Description|
    |--------------|-----------|
    |Restore Type|Restore data by time or by backup set.|
    |Restored At|This parameter is available if **Restore Type** is set to **By Time**. You can set the parameter to any point in time.|
    |Backup ID|This parameter is available if **Restore Type** is set to **By Backup ID**. Select a backup set.|
    |Edition, Zone, Type, Capacity, Network Type, and Duration|For descriptions of these parameters, see [Create an instance](../../../../reseller.en-US/Quick Start for MySQL/Create an instance.md#).|
    |Quantity|You can create up to five clone instances in one order.|

8.  Click **Buy Now**.
9.  Select **Product Terms of Service and Service Level Notice and Terms of Use**, and click **Pay Now** to confirm the order information.

