# Migrate RDS instance zone {#reference_t5m_4dd2_12b .reference}

## Description {#section_l21_v32_12b .section}

Migrate an instance to another zone.  For example, if Instance 1 is currently located in the “cn-hangzhou-a” zone of East China 1 \(Hangzhou\), you can call this interface to migrate the instance to the “cn-hangzhou-b” zone of Hangzhou.

**Note:** In cross-zone migration, instances must be migrated within the same physical location. For example, instances in a zone of East China 1 \(Hangzhou\) cannot be migrated to zones of North China 1 \(Qingdao\).

## Request parameters {#section_qzx_w32_12b .section}

|Name|Type|Required|Description|
|----|----|--------|-----------|
|Action|String|Yes|Required parameter. Value: MigrateToOtherZone.|
|DBInstanceId|String|Yes| Instance ID.|
|ZoneId|String|Yes|TheDescribeRegionsfunction can be used to view available zones.|

## Return parameters {#section_rpk_z32_12b .section}

|Name|Type|Description|
|----|----|-----------|
|&<Public Request Parameters\>|-|For more information, see [Public parameters](intl.en-US/API Reference/Use APIs/Public parameters.md#).|

## Request example {#section_l4g_pj2_12b .section}

```
https://rds.aliyuncs.com/?Action=MigrateToOtherZone
&DBInstanceId=rdsaiiabnaiiabn
&ZoneId=cn-hangzhou-b
&<Public Request Parameters>
```

## Return example {#section_xtg_rj2_12b .section}

**XML format**

```
<MigrateToOtherZoneResponse>
         <RequestId>65BDA532-28AF-4122-AA39-B382721EEE64</RequestId>
         </MigrateToOtherZoneResponse>
```

**JSON format**

```

    "RequestId": " 65BDA532-28AF-4122-AA39-B382721EEE64"

```

