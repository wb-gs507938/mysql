# Modify SSL links of an instance {#reference_krn_wkh_12b .reference}

## Description {#section_l21_v32_12b .section}

This interface only supports MySQL 5.5, MySQL 5.6, and SQL Server 2008 R2.

## Request parameters {#section_qzx_w32_12b .section}

|Name|Type|Required?|Description|
|----|----|---------|-----------|
|Action|String|Yes|Required parameter. Value: ModifyDBInstanceSSL.|
|DBInstanceId|String|Yes|Instance ID.|
|ConnectionString|String|Yes|Each instance can only have one connected address protected by the SSL certificate. Create or upgrade the SSL certificate for the target connection address.|

## Return parameters {#section_qdm_tf3_12b .section}

|Name|Type|Description|
|----|----|-----------|
|<Public Return Parameters\>| |For more information, see [Public parameters](intl.en-US/API Reference/Use APIs/Public parameters.md#).|
|SSLExpireTime|String|SSL expiration time.|

##   {#section_l4g_pj2_12b .section}

##   {#section_xtg_rj2_12b .section}

