# Set network types {#concept_zqv_gxx_wdb .concept}

RDS supports two network types: classic network and Virtual Private Cloud \(VPC\). We recommend VPC because it provides higher security. This chapter describes the differences between the two network types and the configuration method.

**Note:** To migrate an instance from a classic network to a VPC without stopping services, see [Hybrid access solution for the seamless migration from classic network to VPC](intl.en-US/User Guide/Network management/Hybrid access solution for the seamless migration from classic network to VPC.md#).

## Background information {#section_dxf_zxx_wdb .section}

On Alibaba Cloud platform, a classic network and a VPC have the following differences:

-   Classic network: The cloud services in a classic network are not isolated, and unauthorized access can be blocked only by the security group or whitelist policy of the cloud services.

-   VPC: It helps you build an isolated network environment in Alibaba Cloud. You can customize the routing table, IP address range and gateway on the VPC. In addition, you can combine your data center and cloud resources in the Alibaba Cloud VPC into a virtual data center through a leased line or VPN to migrate applications to the cloud seamlessly.


## Precautions {#section_q4c_1yx_wdb .section}

-   After switching the network type, the original intranet IP address is changed and the public IP address remains unchanged. Update the connection address on your applications if necessary. For example, after an RDS instance is switched from a classic network to a VPC, the intranet address of the classic network is released and a VPC IP address is generated. Therefore, ECS instances in classic networks cannot access the RDS instance through the intranet any more.

-   To switch MySQL 5.5, MySQL 5.6, or SQL Server 2008 R2 from a classic network to a VPC, the access mode must be safe connection mode. To switch the access mode, see [Set access mode](intl.en-US/User Guide/Network management/Set access mode.md#).

    **Note:** MySQL 5.5, MySQL 5.6, and SQL Server 2008 R2 instances in North China 1, North China 2, East China 1, and Hong Kong regions do not have this constraint.

-   During the network type switching, the RDS service may be interrupted for about 30 seconds. Therefore, perform the switching during off-peak hours or make sure that your applications have the automatic reconnection mechanism.


## Procedure {#section_ek4_byx_wdb .section}

1.  Log on to the [RDS console](https://rds.console.aliyun.com/).
2.  Select the region where the target instance is located.
3.  Click the ID of the target instance to enter the Basic Information page.
4.  Select **Connection Options** in the left-side navigation pane to open the Connection Options page.
5.  Do the following to switch the network type:
    -   Switch from a classic network to a VPC

        1.  Click **Switch to VPC**.
        2.  Select a VPC and virtual switch.

            **Note:** 

            -   If the drop-down lists do not have VPCs or virtual switches or if the VPCs and virtual switches are not what you need, create a VPC and virtual switch that are in the same region as the RDS instance. To create a VPC, see [Create a VPC](https://www.alibabacloud.com/help/doc-detail/53604.htm). To create a virtual switch, see [Create a switch](https://www.alibabacloud.com/help/doc-detail/53670.htm).

            -   For MySQL 5.5, MySQL 5.6, and SQL Server 2008 instances, their access mode must be safe connection mode if you want to switch from a classic network to a VPC. To switch the access mode, see [Set access mode](intl.en-US/User Guide/Network management/Set access mode.md#).

            ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7943/3260_en-US.png)

        3.  Click **OK**.
    -   Switch from a VPC to a classic network
        1.  Click **Switch to Classic Network**.
        2.  Click **OK**.

