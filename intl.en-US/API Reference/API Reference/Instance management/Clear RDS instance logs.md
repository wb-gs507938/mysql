# Clear RDS instance logs {#reference_ovn_l1f_12b .reference}

## Description {#section_l21_v32_12b .section}

For MySQL instances, all related Binlog logs are cleared. For SQL Server instances, a temporary backup is produced. When the temporary backup is finished, the RDS disk space is reduced.

## Request parameters {#section_qzx_w32_12b .section}

|Name|Type|Required|Description|
|----|----|--------|-----------|
|Action|String|Yes|Required parameter. Value: PurgeDBInstanceLog.|
|DBInstanceId|String|Yes|Instance with disk space to be reduced.|

## Return parameters {#section_rpk_z32_12b .section}

|Name|Type|Description|
|----|----|-----------|
|<Public Return Parameters\>|-|For more information, see [Public parameters](intl.en-US/API Reference/Use APIs/Public parameters.md#).|

## Request example {#section_l4g_pj2_12b .section}

```
https://rds.aliyuncs.com/?Action=PurgeDBInstanceLog
&DBInstanceId=rdsaiiabnaiiabn
&<Public Request Parameters>
```

## Return example {#section_xtg_rj2_12b .section}

**XML format**

```
<PurgeDBInstanceLogResponse>
           <RequestId>65BDA532-28AF-4122-AA39-B382721EEE64</RequestId>
         </PurgeDBInstanceLogResponse>
```

**JSON format**

```

     "RequestId": " 65BDA532-28AF-4122-AA39-B382721EEE64"

```

