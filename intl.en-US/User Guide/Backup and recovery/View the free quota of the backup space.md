# View the free quota of the backup space {#concept_ipg_lm4_ydb .concept}

Backup files of an instance occupy the backup space. Each ApsaraDB for RDS instance provides the backup space with a certain free quota. Additional charges can be incurred for the backup space exceeding the free quota. For information on the billing standard for backup space usage, see [RDS pricing](https://www.alibabacloud.com/product/apsaradb-for-rds?spm=a3c0i.7938564.220486.8.10521d15yetoaN#pricing). Different types of instances have different free backup space quotas. This document describes how to view and calculate the free quota of the instance backup space.

## Formula for calculating the free quota of the backup space {#section_idj_2m4_ydb .section}

If the total volume of your backup data \(OSS and Archive Storage\) and backup log \(OSS\) is less than or equal to 50% of storage space bought for the instance, the space is within the free quota.

The excess backup space beyond the free quota is billed by hour. \(Unit: GB, rounded up only\)

```
Costs per hour = data backup volume + Log backup volume - Instance storage space x 50% 
```

## View the free quota of the backup space on the ApsaraDB for RDS console {#section_lyn_fm4_ydb .section}

1.  Log on to the [RDS console](https://rds.console.aliyun.com/).
2.  Select the region where the target instance is located.
3.  Click the ID of the target instance to go to the **Basic Information** page.
4.  In the **Resource Information** area at the bottom of the page, check the remarks next to **Backup Size**, which shows the free quota as in the following figure.

    **Note:** Instances of different types support different free quotas. The following figure is only an example.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7965/4106_en-US.png)


