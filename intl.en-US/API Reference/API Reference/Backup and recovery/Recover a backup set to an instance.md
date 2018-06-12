# Recover a backup set to an instance {#reference_jzj_4tl_12b .reference}

## Description {#section_l21_v32_12b .section}

Restore the backup set to an instance by overwriting the instance. The following conditions must be met, otherwise operation will fail:

-   The instance status is Running.

-   No migration tasks exist.

-   The instance is not locked.

-   The current status of the instance backup set is Success.


## Request parameters {#section_qzx_w32_12b .section}

|Name|Type|Required|Description|
|----|----|--------|-----------|
|Action|String|Yes|Required parameter. Value: RestoreDBInstance.|
|DBInstanceId|String|Yes|Instance ID.|
|BackupId|Integer|Yes|ID of the backup set.|

## Return parameters {#section_a5x_zlh_12b .section}

|Name|Type|Description|
|----|----|-----------|
|<Public Return Parameters\>|-|For more information, see [Public parameters](intl.en-US/API Reference/Use APIs/Public parameters.md#).|

## Request example {#section_l4g_pj2_12b .section}

```
https://rds.aliyuncs.com/?Action=RestoreDBInstance
&BackupId=103916160
&DBInstanceId=rds91e395totd54461k3
&<Public Request Parameters>
```

## Response example {#section_xtg_rj2_12b .section}

**XML format**

```
<RestoreDBInstanceResponse>
     <RequestId>37441409-FFD1-40AA-8EC5-9ECF5E2F7C29</RequestId>
</RestoreDBInstanceResponse>
```

**JSON format**

```
{"RequestId":"37441409-FFD1-40AA-8EC5-9ECF5E2F7C29"}
```

