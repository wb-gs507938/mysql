# Upgrade the database version of RDS instance {#reference_t5m_2dd2_12b .reference}

## Description {#section_l21_v32_12b .section}

Upgrade the database version of an instance, for example, from MySQL 5.1 to MySQL 5.5.

If the primary instance is attached with a read-only or disaster recovery instance, please first upgrade the database version of the read-only or disaster recovery instance. The operation must meet the following conditions, otherwise the call will fail:

-   The instance is Running.
-   The entered database version must be later than the current database version of the target instance.

## Request parameters {#section_qzx_w32_12b .section}

|Name|Type|Required?|Description|
|----|----|---------|-----------|
|Action|String|Yes|Required parameter. Value: UpgradeDBInstanceEngineVersion.|
|DBInstanceId|String|Yes|Instance to be upgraded/downgraded.|
|EngineVersion|String|Yes|Database version to be upgraded to.|

## Return parameters {#section_rpk_z32_12b .section}

|Name|Type|Description|
|----|----|-----------|
|<Public Return Parameters\>|-|For more information, see [Public parameters](intl.en-US/API Reference/Use APIs/Public parameters.md#).|
|TaskId|Integer|Task ID.|

## Request example {#section_l4g_pj2_12b .section}

```
https://rds.aliyuncs.com/?Action=UpgradeDBInstanceEngineVersion
&DBInstanceId=rdsaiiabnaiiabn
&EngineVersion=5.6
&<Public Request Parameters>
```

## Response example {#section_xtg_rj2_12b .section}

**XML format**

```
<UpgradeDBInstanceEngineVersionResponse>
         <RequestId>65BDA532-28AF-4122-AA39-B382721EEE64</RequestId>
           <TaskId>124378</Taskid>
</UpgradeDBInstanceEngineVersionResponse>
```

**JSON format**

```

"RequestId": " 65BDA532-28AF-4122-AA39-B382721EEE64"
"TaskId":”124378”
  
```

