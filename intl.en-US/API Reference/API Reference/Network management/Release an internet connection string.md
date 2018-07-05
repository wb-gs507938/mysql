# Release an Internet connection string {#reference_vlq_hb3_12b .reference}

## Description {#section_l21_v32_12b .section}

Release an Internet connection string of an instance.

## Request parameters {#section_qzx_w32_12b .section}

|Name|Type|Required|Description|
|----|----|--------|-----------|
|Action|String|Yes|Required parameter. Value: ReleaseInstancePublicConnection.|
|DBInstanceId|String|Yes|Instance ID.|
|CurrentConnectionString|String|Yes|Internet connection string.|

## Return parameters {#section_a5x_zlh_12b .section}

|Name|Type|Description|
|----|----|-----------|
|<Public Return Parameters\>|-|For more information, see [Public parameters](intl.en-US/API Reference/Use APIs/Public parameters.md#).|

## Request example {#section_l4g_pj2_12b .section}

```
https://rds.aliyuncs.com/?Action=DeleteDBInstance
&DBInstanceId=rdsaiiabnaiiabn
&<[Public request parameters]>
```

## Response example {#section_xtg_rj2_12b .section}

**XML format**

```
<DeleteDBInstanceResponse>  
         <RequestId>65BDA532-28AF-4122-AA39-B382721EEE64</RequestId>
</DeleteDBInstanceResponse>
```

**JSON format**

```
{
    "RequestId": " 65BDA532-28AF-4122-AA39-B382721EEE64"
  }
```

