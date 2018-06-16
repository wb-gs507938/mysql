# Release an instance {#concept_r1p_jgj_wdb .concept}

Depending on the business change, you can manually release Pay-As-You-Go instances, but not Subscription instances. This document describes how to release an instance manually.

## Attention {#section_xjf_ngj_wdb .section}

-   Subscription instances are released automatically when they are overdue.

-   The instance is in Running status.

-   If the master instance enabled the read/write splitting function, to release the last read-only instance, you must [Disable read/write splitting](intl.en-US/User Guide/Read/write splitting/Disable read/write splitting.md#) first.


## Procedure {#section_dsk_4gj_wdb .section}

1.  Log on to the [RDS console](https://rds.console.aliyun.com/).
2.  Select the region where the target instance is located.
3.  Click the ID of the target instance to visit the Basic Information page.
4.  In the Operating Status area, click **Release Instance**, as shown in the following figure.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7887/3024_en-US.png)

5.  In the dialog box, click **Confirm** to release the instance.

