# Authorize a service account {#concept_lwz_jcp_ydb .concept}

If you are seeking for technical supports from Alibaba Cloud and if it is necessary to operate your database instance during technical support, you must authorize a service account that is used by the technical support staff to provide technical support services.

## Background information {#section_kr4_tcp_ydb .section}

When you authorize the service account to **view and modify configuration** or **view table structure, index, and SQL**, the system generates a temporary service account and the corresponding permissions are given to this account according to your authorization information.

This temporary service account is automatically deleted after the validity period of authorization expires.

## Procedure {#section_wct_wcp_ydb .section}

1.  Log on to the [RDS console](https://rds.console.aliyun.com/) and select the target instance.
2.  Select **Account management** in the left-side navigation pane to go to the Account Management page. Select the **Privilege account** tab page.
3.  Select the permission to be authorized to the service account and click the button in the **Privilege status** column, as shown in the following figure.

    -   For troubleshooting of the IP white lists, database parameters and other problems, you must authorize **Control privilege** only.
    -   For the database performance problems caused by your application, you must authorize **Data privilege**.
    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7930/4170_en-US.png)

4.  After setting the permission expiration time on the page of Setting expired time, click **OK** as shown in the following figure.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7930/4171_en-US.png)


## Subsequent operations {#section_emx_cdp_ydb .section}

After a service account is authorized, you may cancel the authorization \(as shown in Fig.1\) or change the authorization validity period \(as shown in Fig.2\) on the Privilege account tab page.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7930/4172_en-US.png)

