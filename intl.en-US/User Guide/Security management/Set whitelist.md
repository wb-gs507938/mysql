# Set whitelist {#concept_rpj_hs4_ydb .concept}

A whitelist is used to allow specified IP addresses and IP segments to access RDS. By default, the RDS whitelist contains only the default IP address 127.0.0.1 and has no security group. This means that no server can access the RDS instance.

After you set the whitelist, only the following servers can access RDS:

-   Servers whose IP addresses are in the whitelist
-   ECS instances that are in the security group specified in the whitelist

A security group is a virtual firewall that is used to set network access control for one or more ECS instances. For more information about ECS security groups, see [Create a security group](https://www.alibabacloud.com/help/doc-detail/25468.htm).

We recommend that you periodically check and adjust your whitelists according to your requirements to maintain RDS security. The whitelist only controls access to the RDS instance and does not affect its running. This document describes how to set the whitelist.

## Attentions {#section_wqz_5s4_ydb .section}

-   The default whitelist group can only be modified or cleared, but cannot be deleted.

-   % or 0.0.0.0/0 indicates any IP address is allowed to access the RDS instance. This configuration greatly reduces the security of the database and is not recommended.

-   When the whitelist is set, the system automatically generates the intranet address for the RDS instance. If you need an Internet address, see [Set intranet and Internet addresses](intl.en-US/User Guide/Network management/Set intranet and Internet addresses.md#).

-   If you cannot connect to the RDS instance after adding the application service IP address to the whitelist, you can obtain the actual IP address of the application by referring to [How to locate the local IP address using ApsaraDB for MySQL](https://www.alibabacloud.com/help/faq-detail/41754.htm).


## Procedure {#section_wyv_ws4_ydb .section}

1.  Log on to the [RDS console](https://rds.console.aliyun.com/).
2.  Select the region where the target instance is located.
3.  Click the name of the target instance to go to the Basic Information page.
4.  Select **Security** in the left-side navigation pane to visit the Security page.
5.  On the Whitelist Settings tab page, find the **default** whitelist group and click **Modify**.

    **Note:** To add a custom whitelist group to the RDS instance, locate the **default** whitelist group and click **Clear** to delete the IP address 127.0.0.1, and then click **Add a whitelist Group**. The subsequent steps for a custom whitelist are similar to the following steps.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7948/4139_en-US.png)

6.  On the Modify Group page, add the IP addresses or IP segments to access the RDS instance to whitelist field. If you want to add the ECS intranet IP addresses, click **Upload ECS intranet IP Address**, select IP addresses, and click **OK**, as shown in the following figure.

    **Note:** If you add an IP address or segment to the default group, the default IP address 127.0.0.1 Is automatically deleted.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7948/4140_en-US.png)

    Parameter descriptions:

    -   **Group Name**: it can contain 2 to 32 characters including lowercase letters, digits, or underscores. The group name must start with a lowercase letter and end with a letter or digit. This name cannot be modified once the whitelist group is successfully created.

    -   **Whitelist**: enter the custom IP addresses or IP segments that can access the RDS instance.

        -   If you enter an IP segment, such as 10.10.10.0/24, it indicates that any IP address in the format of 10.10.10.X can access the RDS instance.

        -   If you want to enter multiple IP addresses or IP segments, separate them by commas \(,\) \(do not add blank spaces\), such as 192.168.0.1,172.16.213.9.

        -   For each whitelist group, up to 1,000 IP addresses or IP segments can be set for MySQL, PostgreSQL, and PPAS instances; and up to 800 can be set for SQL Server instances.

    -   **Upload ECS intranet IP Address**: by clicking this button, you can select the intranet IP addresses of the ECS instances under the same account with the RDS instance, which is a quick method to add ECS intranet IP addresses.


## Precautions for adding ECS security groups {#section_tsz_lt4_ydb .section}

You can configure both the IP whitelist and the ECS security group. Your RDS instance allows access from servers whose IP addresses are in the IP whitelist and ECS instances that are in the security group.

-   Currently, only MySQL 5.6 and the Hangzhou, Qingdao, and Hong Kong regions support ECS security groups.

-   One RDS instance supports one security group.

-   Updates to the ECS security group are automatically applied to the whitelist.


## Add an ECS security group {#section_dsr_nt4_ydb .section}

1.  Log on to the [RDS console](https://rds.console.aliyun.com/).
2.  Select the region where the target instance is located.
3.  Click the ID of the target instance to go to the Basic Information page.
4.  Select **Security** in the left-side navigation pane to visit the Security page.
5.  On the Whitelist Settings tab page, click **Add to Security Group**.

    **Note:** The security groups marked with "VPC" are in VPCs.

6.  Select a security group and click **OK**.

