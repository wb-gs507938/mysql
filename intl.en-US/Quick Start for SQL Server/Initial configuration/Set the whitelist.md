# Set the whitelist {#concept_jvp_nwz_vdb .concept}

A whitelist is used to restrict access to specified IP addresses and specified IP segments. You cannot access a database unless a whitelist is set. We recommend that you periodically check and adjust your whitelists according to your requirements to maintain RDS security. This document provides the necessary information and procedure to set the whitelist.

## Precautions {#section_wyv_ws4_ydb .section}

-   The system automatically creates a **default** whitelist group for each newly created RDS instance. This **default** whitelist group can only be modified or cleared, but cannot be deleted.
-   For each newly created RDS instance, the local loopback IP address 127.0.0.1 is added to the **default** whitelist group by default. This means that all the IP addresses or IP segments are prohibited to access this RDS instance. Therefore, you must delete 127.0.0.1 from the **default** whitelist group first, before you add other IP addresses or IP segments to the RDS whitelist.
-   % or 0.0.0.0/0 indicates any IP address is allowed to access the RDS instance. This configuration greatly reduces the security of the database and is not recommended.

## Procedure {#section_ktk_r4f_52b .section}

1.  Log on to the [RDS console](https://rds.console.aliyun.com/).
2.  Select the region where the target instance is located.
3.  Click the name of the target instance to go to the **Basic Information** page.
4.  Select **Security** in the left-side navigation pane to enter the **Security** page.
5.  On the **Whitelist Settings** tab page, click **Modify** of the **default** whitelist group, as shown in the following figure.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7835/15431617582754_en-US.png)

6.  On the **Modify Group** page, add the IP addresses or IP segments to access the RDS instance to **Whitelist** field. If you want to add the ECS intranet IP addresses, click **Upload ECS Intranet IP Address** and select the IP addresses according to the prompt, as shown in the following picture.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7835/15431617582752_en-US.png)

    -   Group Name: It can contain 2 to 32 characters including lowercase letters, digits, or underscores. The group name must start with a lowercase letter and end with a letter or digit. This name cannot be modified once the whitelist group is successfully created.

    -   Whitelist: Enter the custom IP addresses or IP segments that can access the RDS instance.
        -   If you enter an IP segment, such as 10.10.10.0/24, it indicates that any IP address in the format of 10.10.10.X can access the RDS instance.
        -   If you want to enter multiple IP addresses or IP segments, separate them by commas \(,\) \(do not add blank spaces\), such as 192.168.0.1,172.16.213.9.
    -   Upload ECS intranet IP Address: By clicking this button, you can select the intranet IP addresses of the ECS instances under the same account with the RDS instance, which is a quick method to add ECS intranet IP addresses.
7.  Click **OK**.

## **Modify or delete the whitelist group** {#section_wft_m1p_xfb .section}

You can modify or delete the whitelist group according your business requirements. The detailed procedure is as follows:

1.  Log on to the [RDS console](https://rds.console.aliyun.com/).
2.  Select the region where the target instance is located.
3.  Click the name of the target instance to go to the **Basic Information** page.
4.  Select **Security** in the left-side navigation pane to enter the **Security** page.
5.  On the **Whitelist Settings** tab page, click **Modify** or **Delete** button of the target whitelist group.
6.  Click **OK** after you modify the IP addresses or IP segments.

