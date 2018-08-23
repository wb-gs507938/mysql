# View RDS instance list {#reference_pyz_mm2_12b .reference}

## Description {#section_l21_v32_12b .section}

This API is used to query the instance list or the instance list authorized by RAM.

## Request parameters {#section_qzx_w32_12b .section}

|Name|Type|Required or not|Description|
|----|----|---------------|-----------|
|Action|String|Yes|Required parameter. Value: DescribeDBInstances.|
|RegionId|String|Yes|Instance region, viewed through theDescribeRegions.|
|Engine|String|No|Database type. Value range: MySQL, SQLServer, PostgreSQL, and PPAS. If no value is specified, all types are returned.|
|DBInstanceType|String|No|Instance type. Value range:-   Primary: primary instance
-   Readonly: read-only instance
-   Guard: disaster recovery instance
-   Temp: temporary instance

If no value is specified, all types are returned.|
|InstanceNetworkType|String|No|Value range:-   VPC: VPC
-   Classic: classic network

If no value is specified, both types are returned.|
|ConnectionMode|String|No|-   Standard: standard access mode;
-   Safe: high security access mode.

If no value is specified, both modes are returned.|
|Tags|String|No|Used to query instances bound to a specified tag.-   The format is JSON string, including TagKey and TagValue.
-   TagKey cannot be empty but TagValue can, format example: \{"key1": "value1 "\}.

|
|PageSize|Integer|No|Number of records on each page. Value range: 30, 50, and 100. Default value: 30.|
|PageNumber|Integer|No|Page number, which must be greater than 0, but cannot exceed the maximum integer value. Default value: 1.|

## Return parameters {#section_rpk_z32_12b .section}

|Name|Type|Description|
|----|----|-----------|
|<Public Return Parameters\>|-|For more information, see [Public parameters](intl.en-US/API Reference/Use APIs/Public parameters.md#).|
|Databases|List<Database\>|Data composed of databases|
|PageNumber|Integer|Page number|
|TotalRecordCount|Integer|Total number of records|
|PageRecordCount|Integer|Number of DB instances on the current page|
|Items|List<DBInstance\>|Arrays composed of DB instances|

## Parameters for DBInstance {#section_ip3_142_12b .section}

|Name|Type|Description|
|----|----|-----------|
|DBInstanceId|String|Instance ID|
|DBInstanceDescription|String|Instance description|
|PayType|String|Billing method. Value options:-   Postpaid: Pay-As-You-Go
-   Prepaid: Subscription

|
|DBInstanceType|String| -   Primary: primary instance
-   Readonly: read-only instance
-   Guard: disaster recovery instance
-   Temp: temporary instance

 |
|InstanceNetworkType|String| -   VPC: VPC
-   Classic: classic network

 |
|ConnectionMode|String| -   Standard: standard access mode
-   Safe: high security access mode

 |
|RegionId|String|Region ID|
|Expiretime|String|Expiration time. Pay-As-You-Go instances never expire.|
|DBInstanceStatus|String| For more information, see [Instance status table](https://www.alibabacloud.com/help/doc-detail/26315.htm?spm=a2c63.p38356.b99.343.4b3e572aoiKZab).|
|Engine|String|Database type|
|DBInstanceNetType|String| -   Internet: public network
-   Intranet: private network

 |
|LockMode|String| -   Unlock: normal
-   ManualLock: locked when manually triggered
-   LockByExpiration: automatically locked upon expiration
-   LockByRestoration: automatically locked before instance rollback
-   LockByDiskQuota: automatically locked upon full instance space

 |
|LockReason|String|Reason why an instance is locked|
|MasterInstanceId|String|Primary instance ID. If this parameter is not returned \(that is, if it is null\), the current instance is a primary instance.|
|GuardDBInstanceId|String|ID of a disaster recovery instance if it is attached to the current instance|
|TempDBInstanceId|String|ID of a temporary instance if it is attached to the current instance|
|ReadOnlyDBInstanceId|List<ReadOnlyDBInstanceId\>|ID list of read-only instances attached to the primary instance|

## ReadOnlyDBInstanceId parameters {#section_jxc_bp2_12b .section}

|Name|Type|Description|
|----|----|-----------|
|ReadOnlyDBInstanceId|String| ID of a read-only instance|

## Request example {#section_l4g_pj2_12b .section}

```
https://rds.aliyuncs.com/?Action=DescribeDBInstances
&RegionId=cn-hangzhou
&Engine=MySQL
&<Public request parameters>
```

## Response example {#section_xtg_rj2_12b .section}

**XML format**

```
<DescribeDBInstancesResponse>
<PageRecordCount>2</PageRecordCount>
<Items>
<DBInstance>
<DBInstanceDescription>testforRemarks</DBInstanceDescription>
<ExpireTime>2014-10-10T16:00:00Z</ExpireTime>
<DBInstanceId>rdsmjfirvmjfirv</DBInstanceId>
<DBInstanceNetType>Internet</DBInstanceNetType>
<PayType>Prepaid</PayType>
<DBInstanceStatus>Running</DBInstanceStatus>
<DBInstanceType>Primary</DBInstanceType>
<Engine>MySQL</Engine>
<LockMode>Unlock</LockMode>
<LockReason></LockReason>
<RegionId>cn-hangzhou</RegionId>
<ZoneId>cn-hangzhou-a</ZoneId>
<MasterInstanceId></MasterInstanceId>
<GuardDBInstanceId></GuardDBInstanceId>
<TempDBInstanceId></TempDBInstanceId>
<ReadOnlyDBInstanceIds>
      <ReadOnlyDBInstanceId></ReadOnlyDBInstanceId>
   </ReadOnlyDBInstanceIds> 
</DBInstance>
<DBInstance>
<DBInstanceDescription>testforcreate</DBInstanceDescription>
<ExpireTime></ExpireTime>
<DBInstanceId>rdsabqumfabqumf</DBInstanceId>
<DBInstanceNetType>Intranet</DBInstanceNetType>
<PayType>Postpaid</PayType>
<DBInstanceStatus>Running</DBInstanceStatus>
<DBInstanceType>Primary</DBInstanceType>
<Engine>MySQL</Engine>
<LockMode>Unlock</LockMode>
<LockReason></LockReason>
<RegionId>cn-hangzhou</RegionId>
<MasterInstanceId></MasterInstanceId>
<GuardDBInstanceId></GuardDBInstanceId>
<TempDBInstanceId></TempDBInstanceId>
<ReadOnlyDBInstanceIds>
       <ReadOnlyDBInstanceId></ReadOnlyDBInstanceId>
    </ReadOnlyDBInstanceIds> 
</DBInstance>
</Items>
<PageNumber>1</PageNumber>
<TotalRecordCount>2</TotalRecordCount>
<RequestId>2553A660-E4EB-4AF4-A402-8AFF70A49143</RequestId>
</DescribeDBInstancesResponse>
```

**JSON format**

```
{
    "PageNumber": 1, 
    "Items": {
      "DBInstance": [
        {
          "Engine": "MySQL", 
          "DBInstanceType": "Primary", 
          "DBInstanceStatus": "Running", 
          "DBInstanceDescription": "testforRemarks", 
          "LockMode": "Unlock", 
          "RegionId": "cn-hangzhou", 
"ZoneId": "cn-hangzhou-a", 
          "DBInstanceId": "rdsmjfirvmjfirv", 
          "PayType": "Prepaid", 
          "ExpireTime": "2014-10-10T16:00:00Z", 
          "DBInstanceNetType": "Internet", 
          "LockReason": "",
          "MasterInstanceId": "",
          "GuardDBInstanceId ": "",
          "TempDBInstanceId": "",
"ReadOnlyDBInstanceIds": {
                 "ReadOnlyDBInstanceId": []
                }
        }, 
        {
          "Engine": "MySQL", 
          "DBInstanceType": "Primary", 
          "DBInstanceStatus": "Running", 
          "DBInstanceDescription": "testforcreate", 
          "LockMode": "Unlock", 
          "RegionId": "cn-hangzhou", 
          "DBInstanceId": "rdsabqumfabqumf", 
          "PayType": "Postpaid", 
          "ExpireTime": "", 
          "DBInstanceNetType": "Intranet", 
          "LockReason": "",
"MasterInstanceId": "",
          "GuardDBInstanceId ": "",
          "TempDBInstanceId": "",
"ReadOnlyDBInstanceIds": {
                 "ReadOnlyDBInstanceId": []
                }
        }
]
    } , 
    "TotalRecordCount": 2, 
    "PageRecordCount": 2, 
"RequestId": "2553A660-E4EB-4AF4-A402-8AFF70A49143"
}
```

