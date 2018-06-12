# RestartDBInstance {#reference_glw_r32_12b .reference}

## Description {#section_l21_v32_12b .section}

Generally an RDS instance can be restarted within 10s. If a large number of transactions must be submitted or rolled back, the restart may be extended by about one minute. The operation must meet the following conditions, otherwise the call will fail:

-   The instance is running.
-   The instance is not currently performing a backup task.

## Request parameters {#section_qzx_w32_12b .section}

|Name|Type|Required?|Description|
|----|----|---------|-----------|
|Action|String|Yes|Required parameter. Value: RestartDBInstance.|
|DBInstanceId|String|Yes|Instance ID.|

## Return parameters {#section_rpk_z32_12b .section}

|Name|Type|Description|
|----|----|-----------|
|<Public Return Parameters\>|-|For more information, see [Public parameters](intl.en-US/API Reference/Use APIs/Public parameters.md#).|

## Request example {#section_l4g_pj2_12b .section}

```
https://rds.aliyuncs.com/?Action=RestartDBInstance
&DBInstanceId=rdsaiiabnaiiabn
&<Public Request Parameters>
```

## Response example {#section_xtg_rj2_12b .section}

**XML format**

```
<RestartDBInstanceResponse>
         <RequestId>65BDA532-28AF-4122-AA39-B382721EEE64</RequestId>
</RestartDBInstanceResponse>
```

**JSON format**

```

    "RequestId": " 65BDA532-28AF-4122-AA39-B382721EEE64"

```

