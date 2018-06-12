# View SSL information {#reference_b4t_3ch_12b .reference}

## Description {#section_l21_v32_12b .section}

This interface only supports MySQL 5.5, MySQL 5.6, and SQL Server 2008R2.

## Request parameters {#section_qzx_w32_12b .section}

|Name|Type|Required?|Description|
|----|----|---------|-----------|
|Action|String|Yes|Required parameter. Value: DescribeDBInstanceSSL.|
|DBInstanceId|String|Yes|Instance ID.|

## Return parameters {#section_rpk_z32_12b .section}

|Name|Type|Description|
|----|----|-----------|
|<Public Return Parameters\>|-|For more information, see [Public parameters](intl.en-US/API Reference/Use APIs/Public parameters.md#).|
|ConnectionString|String|Connection address protected by the SSL certificate.|
|SSLExpireTime|String|Expiration time of the SSL certificate.|
|RequireUpdate|String| -   Yes: Immediate upgrade is recommended.
-   No: Immediate upgrade is not recommended.

 |
|RequireUpdateReason|String|Reasons why upgrade is recommended.|

##   {#section_l4g_pj2_12b .section}

##   {#section_xtg_rj2_12b .section}

