# Apply for an Internet IP address {#concept_nsl_hff_vdb .concept}

The RDS supports two kinds of addresses: the internal network address and the external network address. Specific instructions are described in the following table.

## Intranet and Internet addresses {#section_x5z_5ff_vdb .section}

|Type|Remarks|
|----|-------|
|Intranet IP address| -   The intranet network address is provided by default.

-   If your application is deployed in an ECS instance that is in the same region as the RDS instance, and the ECS and RDS instances have the same [network type](../intl.en-US/User Guide/Connection management/Set network type.md), the RDS instance and the ECS instances can communicate through the intranet without the need for an Internet IP address.

-   You can achieve optimal RDS security and performance by accessing the RDS instance through the intranet.

 |
|Internet IP address| -   The Internet IP address can only be applied manually and can be released.

-   You need to apply for an Internet IP address if you cannot access an RDS instance through the intranet. Scenarios are as follows:

-   An ECS instance that needs to access the RDS instance and the two instances are in different regions.
-   An ECS instance that needs to access the RDS instance and the two instances have different [network types](../intl.en-US/User Guide/Connection management/Set network type.md).
-   A server or computer outside Alibaba Cloud needs to access the RDS instance.

 **Note:** 

-   Application of the outer network address and subsequent public network traffic will not be charged.
-   Connecting to the RDS instance with an Internet IP address may reduce the instance security. Please exercise caution.
-   For faster speed and greater security, it is recommended that you migrate your ECS instance to the region where your RDS instance is located, or make sure that the ECS and RDS instances have the same network type, and then use the intranet IP address.

 |

## Apply for outer address { .section}

1.  Login[RDS Management Console](https://rds.console.aliyun.com/).
2.  In the upper-left corner, select the region where the target instance is located from the region list.

    ![Select a region.](../DNMYSQ1820581/images/36543_en-US.png)

3.  Locate the target instance and click its ID.
4.  In the left-side navigation pane, select **Connection Options**.
5.  Click**Application for outer network address**.

    ![](../DNMYSQ1820581/images/32665_en-US.png)

6.  In the displayed message , click **OK**.

    The outer network address was generated successfully.

7.  \(Optional\) If you want to modify the outer network address or port number, click**Modify connection address**, Set the outer network address and port number in the pop-up dialog box, and then click**Determine**.

    **Note:** 

    -   Under a proprietary network, the port of the inside and outside network address cannot be modified.
    -   Under the classic network, the ports of the inner and outer network addresses are supported for modification.
    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7817/15476306641805_en-US.png)


## Related APIs {#section_s3y_jcc_kgb .section}

|API|中国站|
|---|---|
|[AllocateInstancePublicConnection](../intl.en-US/API Reference/Network management/Apply for an Internet connection string.md#)|中国站|

