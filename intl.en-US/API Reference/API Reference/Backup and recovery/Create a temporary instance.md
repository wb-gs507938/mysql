# Create a temporary instance {#reference_d4d_wrl_12b .reference}

## Description {#section_l21_v32_12b .section}

Create a temporary instance based on a backup set or a time point within the last 7 days. When a temporary instance is created, accounts and databases inherit the backup set data. The following conditions must be met, otherwise creation will fail:

-   The instance status is Running.
-   No migration tasks exist.
-   The instance is not locked.
-   The current status of the instance backup set is Success.

## Request parameters {#section_qzx_w32_12b .section}

|Name|Type|Required?|Description|
|----|----|---------|-----------|
|Action|String|Yes|Required parameter. Value: CreateTempDBInstance.|
|DBInstanceId|String|Yes|Instance ID.|
|BackupId|Integer|Yes|ID of the backup.|
|RestoreTime|String|No|Any time in the past 7 days and more than 30 minutes earlier than the current time can be used as the restoration time. The default time zone is UTC. For example, 2011-06-11T16:00:00Z.|

## Return parameters {#section_a5x_zlh_12b .section}

|Name|Type|Description|
|----|----|-----------|
|<Public Return Parameters\>| |For more information, see [Public parameters](intl.en-US/API Reference/Use APIs/Public parameters.md#).|
|TempDBInstanceId|String|ID of a sub-instance.|

## Request example {#section_l4g_pj2_12b .section}

```
https://rds.aliyuncs.com/?Action=CreateTempDBInstance
&BackupId=90262
&DBInstanceId=riauvjz6zajfiq6ba1370329449201
&<Public Request Parameters>
```

## Response example {#section_xtg_rj2_12b .section}

**XML format:**

```
<CreateChildDBInstanceResponse>
     <RequestId>248DE93F-8647-4B9D-8287-4A4A0FE56AD5</RequestId>
<TempDBInstanceId>sub1385954257106_junjunzhaasadsd</TempDBInstanceId>
</CreateChildDBInstanceResponse>
```

**JSON format:**

```

       "RequestId":"248DE93F-8647-4B9D-8287-4A4A0FE56AD5",
       "TempDBInstanceId":"sub1385954257106_junjunzhaasadsd"

```

