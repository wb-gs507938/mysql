# Create a read-only instancec {#reference_ljz_xdf_12b .reference}

## Description {#section_l21_v32_12b .section}

This API is used to create a read-only instance for an RDS instance. The instance must meet the following conditions:

-   The master instance is running and is not in switchover status.
-   The read-only instance and master instance must be in the same region.
-   The database version of the read-only instance must be the same as or later than that of the master instance. The master instance must be in a version of at least MySQL 5.6.
-   The read-only instance must be in a version of at least MySQL 5.6.
-   A single RDS instance can have up to five read-only instances.

## Request parameters {#section_qzx_w32_12b .section}

|Name|Type|Required or not|Description|
|----|----|---------------|-----------|
|Action|String|Yes|Required parameter. Value: CreateReadOnlyDBInstance.|
|RegionId|String|Yes|Data center. The length cannot exceed 50 characters.  DescribeRegionsfunction can be used to view available data centers.|
|ZoneId|String|Yes|Zone ID. TheDescribeRegions function can be used to view available zones.|
|DBInstanceId|String|Yes|ID of a master instance|
|EngineVersion|String|Yes|Database version. -   5.6
-   5.7

|
|DBInstanceClass|String|Yes|Instance type. For more information, see [Instance type list](../../../../intl.en-US/Product Introduction/Instance types/Instance type list.md#).|
|DBInstanceStorage|Integer|Yes|User-defined storage space. Value range: \[5, 1000\], 5 GB increments. Unit: GB.|
|DBInstanceDescription|String|No| -   Instance description or remarks, no more than 256 bytes. 
-   It cannot begin with http:// or https://. It must start with a Chinese character or an English letter.  It may contain Chinese and English characters/letters, “\_”, “-“, and numbers.The length may be 2-256 characters.

 |
|PayType|String|Yes|Postpaid|
|ClientToken|String|Yes|Used to guarantee idempotence|
|InstanceNetworkType|String|No|If no value is specified, a classic instance is created by default.-   VPC: VPC
-   Classic: classic network

|
|VPCId|String|No|VPC ID|
|VSwitchId|String|No|VSwitch ID|
|PrivateIpAddress|String|No|IP address of an VPC under VSwitchId. If no value is specified, the system automatically assigns a VPC IP address based on VPCId and VSwitchId.|

## Return parameters {#section_rpk_z32_12b .section}

|Name|Type|Description|
|----|----|-----------|
|<Public return parameters\>|-|For more information, see [Public parameters](intl.en-US/API Reference/Use APIs/Public parameters.md#).|
|DBInstanceId|String|DB instance ID|
|OrderId|String|Order ID|
|ConnectionString|String|Database connection address|
|Port|String|Port connecting to the database|

## Request example {#section_l4g_pj2_12b .section}

```
https://rds.aliyuncs.com/?Action=CreateReadOnlyDBInstance
&RegionId=cn-hangzhou
&ZoneId=cn-hangzhou-b
&DBInstanceId=rdsaiiabnaiiabn
&EngineVersion=5.6
&DBInstanceClass=rds.mys2.small
&DBInstanceStorage=10
&PayType=Postpaid
&ClientToken=ETnLKlblzczshOTUbOCziJZNwHlYBQ
&<[Public Request Parameters]>
```

## Return example {#section_xtg_rj2_12b .section}

**XML format**

```
<CreateDBInstanceResponse>
     <OrderId>100789370230206</OrderId>
     <ConnectionString>rdsaiiabnaiiabn.mysql.rds.aliyuncs.com </ConnectionString>
     <DBInstanceId>rdsaiiabnaiiabn</DBInstanceId>
     <port>3306</port>
     <RequestId>1E43AAE0-BEE8-43DA-860D-EAF2AA0724DC</RequestId>
</CreateDBInstanceResponse>
```

**JSON format**

```

    "OrderId": "100789370230206", 
    "ConnectionString": "rdsaiiabnaiiabn.mysql.rds.aliyuncs.com", 
    "DBInstanceId": "rdsaiiabnaiiabn", 
    "Port": "3306", 
    "RequestId": "1E43AAE0-BEE8-43DA-860D-EAF2AA0724DC"
   
```

