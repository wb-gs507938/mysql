# Modify the instance data replication mode and high availability switching rules {#reference_gx3_2cf_12b .reference}

## Description {#section_l21_v32_12b .section}

Modify the instance data replication mode and high availability switching rules.

## Request parameters {#section_qzx_w32_12b .section}

|Name|Type|Required?|Description|
|----|----|---------|-----------|
|Action|String|Yes|Required parameter. Value: ModifyDBInstanceHAConfig.|
|DBInstanceId|String|Yes|Instance ID.|
|SyncMode|String|String|Sync: synchronous. Semi-sync: semi-synchronous. Async: asynchronous.|
|HAMode|String|String|RPO: data persistence of top priority. RTO: instance availability of top priority.|

## Return parameters {#section_rpk_z32_12b .section}

|Name|Type|Description|
|----|----|-----------|
|<Public Return Parameters\>|-|For more information, see [Public parameters](intl.en-US/API Reference/Use APIs/Public parameters.md#).|

