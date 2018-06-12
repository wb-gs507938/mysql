# DeleteDBInstance {#reference_yvz_xh2_12b .reference}

## Description {#section_awy_b32_12b .section}

Release an RDS instance. The following conditions must be met, otherwise the call will fail:

-   The current status of instance: running.
-   Not artificially locked.
-   The instance is a master instance \(Pay-As-You-Go type\), read-only instance, disaster recovery instance, or temporary instance.

## Request parameters {#section_zrb_232_12b .section}

|Name|Type|Required?|Description|
|----|----|---------|-----------|
|Action|String|Yes|Required parameter. Value: DeleteDBInstance.|
|DBInstanceId|String|Yes|Instance ID.|

## Return parameters {#section_y43_h32_12b .section}

|Name|Type|Description|
|----|----|-----------|
|<Public Return Parameters\>|-|For more information, see [Public parameters](intl.en-US/API Reference/Use APIs/Public parameters.md#).|

## Request example {#section_tt5_332_12b .section}

```
https://rds.aliyuncs.com/?Action=DeleteDBInstance
&DBInstanceId=rdsaiiabnaiiabn
&<[Public Request Parameters]>
```

## Response example {#section_frd_k32_12b .section}

**XML format**

```
<DeleteDBInstanceResponse>  
         <RequestId>65BDA532-28AF-4122-AA39-B382721EEE64</RequestId>
</DeleteDBInstanceResponse>
```

**JSON format**

```
 
    "RequestId": " 65BDA532-28AF-4122-AA39-B382721EEE64"
  
```

