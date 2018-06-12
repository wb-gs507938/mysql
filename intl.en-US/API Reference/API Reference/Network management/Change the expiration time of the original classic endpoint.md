# Change the expiration time of the original classic endpoint {#reference_iy5_n13_12b .reference}

## Description {#section_l21_v32_12b .section}

When the instance in in the hybrid access mode \(both the VPC and classic network endpoints are existing in the instance\), you can change the expiration time of the original classic endpoint.

## Request parameters {#section_qzx_w32_12b .section}

|Name|Type|Required or not|Description|
|----|----|---------------|-----------|
|Action|String|Yes|System parameter. Valid value: ModifyDBInstanceNetworkExpireTime.|
|DBInstanceId|String|Yes|ID of the target RDS instance.|
|ConnectionString|String|Yes|The connection string of the classic network to be extended. There are two types of classic network string:-   the classic network string of the current instance
-   and the classic network string of the read/write splitting.

|
|ClassicExpiredDays|Integer|Yes|The retention days of the classic network string: \[1-120\].|

## Return parameters {#section_a5x_zlh_12b .section}

|Name|Type|Description|
|Public return parameters|-|For more information, see [Public parameters](intl.en-US/API Reference/Use APIs/Public parameters.md#).|

##   {#section_l4g_pj2_12b .section}

##   {#section_xtg_rj2_12b .section}

