# Disable read/write splitting {#concept_bwy_hpp_wdb .concept}

If the read/write splitting function is no longer needed, you can disable it. The read/write splitting function can only be used when at least one read-only instance is available, so you must disable the read/write splitting function before you can delete the last read-only instance. Otherwise, the deletion does not succeed.

This article explains how to disable the read/write splitting function.

**Note:** After the read/write splitting function is disabled, your application cannot connect to the read/write splitting address any longer. Make sure that your database connection configuration does not include this connection address.

## Prerequisite {#section_u1d_lpp_wdb .section}

The instance is a MySQL 5.6 High-Availability Edition or Finance Edition, or MySQL 5.7 High-Availability Edition, with read/write splitting enabled.

## Procedure {#section_df3_mpp_wdb .section}

1.  Log on to the [RDS console](https://rdsnew.console.aliyun.com/console/index#/rdsList/) .
2.  Select the region where the target instance is located.
3.  Click the target instance ID to enter the Basic Information page.
4.  Select **Connection Options** in the left-side navigation pane to enter the Connection Options page.
5.  Select the **Read/Write Splitting** tab.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7918/3101_en-US.png)

6.  Click **Disable Read/Write Splitting**.
7.  In the dialog box, click **Confirm**.

