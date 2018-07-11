# DescribeDBInstances {#reference_pyz_mm2_12b .reference}

## 描述 {#section_l21_v32_12b .section}

该接口用于查看实例列表或被RAM授权的实例列表。

## 请求参数 {#section_qzx_w32_12b .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是|系统规定参数，取值为DescribeDBInstances。|
|RegionId|String|是|实例所属地域ID，通过函数DescribeRegions查看。|
|Engine|String|否|数据库类型，取值范围为-   MySQL；
-   SQLServer；
-   PostgreSQL；
-   PPAS；
-   不填，默认返回所有数据库类型。

|
|DBInstanceType|String|否|实例类型，取值范围如下：-   Primary：主实例；
-   Readonly：只读实例；
-   Guard：灾备实例；
-   Temp：临时实例；
-   不填，默认返回所有类型的实例。

|
|InstanceNetworkType|String|否|实例的网络类型，取值范围如下：-   VPC：VPC网络下的实例；
-   Classic：经典网络下的实例；
-   不填，默认返回所有网络类型下的实例。

|
|ConnectionMode|String|否|实例的访问模式：-   Standard：标准访问模式；
-   Safe：高安全访问模式；
-   不填，默认返回所有访问模式下的实例。

|
|Tags|Json string|否|查询绑定有该标签的实例：-   传入值格式为Json string，包括TagKey和TagValue；
-   TagKey不能为空，TagValue可以为空。
-   示例：\{“key1”:”value1”\}。

|
|PageSize|Integer|否|每页记录数，取值：-   30；
-   50；
-   100；
-   默认值：30。

|
|PageNumber|Integer|否|页码，取值为：大于0且不超过Integer数据类型的的最大值，默认值为1。|

## 返回参数 {#section_rpk_z32_12b .section}

|名称|类型|描述|
|--|--|--|
|<公共返回参数\>| |详见[公共参数](intl.zh-CN/API参考/使用API/公共参数.md#)。|
|Databases|List<Database\>|由Database组成的数据。|
|PageNumber|Integer|页码，取值为：大于0且不超过Integer数据类型的的最大值，默认值为1。|
|TotalRecordCount|Integer|总记录数。|
|PageRecordCount|Integer|当前页实例个数。|
|Items|List<DBInstance\>|由实例组成的数组。|
|ReleaseTime|String|实例释放时间：-   包年包月实例到期7天后将被释放。
-   按量付费实例，自欠费日起实例被锁定，锁定后24小时实例将被释放。

|
|DestroyTime |String|实例数据销毁时间：-   包年包月实例释放8天后，数据彻底销毁，且不可找回。
-   按量付费实例，自欠费日起，实例锁定24小时后将被释放，释放同时数据将全部销毁。

 |
|LockMode |String|实例的锁定状态。取值范围如下：-   Unlock：正常；
-   ManualLock：手动触发锁定；
-   LockByExpiration：实例过期自动锁定；
-   LockByRestoration：实例回滚前自动锁定；
-   LockByDiskQuota：实例空间满自动锁定；
-   Released：实例已释放。此时实例无法进行解锁，只能使用备份数据重新创建新实例，重建时间较长，请耐心等待。

|

## DBInstance的参数 {#section_ip3_142_12b .section}

|名称|类型|描述|
|--|--|--|
|DBInstanceId|String|实例名。|
|DBInstanceDescription|String|实例描述。|
|PayType|String|实例付费类型，取值如下：-   Postpaid：按量付费；
-   Prepaid：预付费（包年包月）。

|
|DBInstanceType|String|实例类型：-   Primary：主实例；
-   Readonly：只读实例；
-   Guard：灾备实例；
-   Temp：临时实例。

|
|InstanceNetworkType|String|实例的网络类型，取值范围如下：-   VPC：VPC网络下的实例；
-   Classic：经典网络下的实例；
-   不填，默认返回所有网络类型下的实例。

|
|ConnectionMode|String|实例的访问模式：-   Standard：标准访问模式；
-   Safe：高安全访问模式；
-   不填，默认返回所有访问模式下的实例。

|
|RegionId|String|实例所属地域ID。|
|ExpireTime|String|包年包月实例到期时间，按量付费实例无到期时间。|
|DBInstanceStatus|String|实例状态，详情请参见[实例状态表](intl.zh-CN/API参考/API参考/附表/实例状态表.md#)。|
|Engine|String|数据库类型。|
|DBInstanceNetType|String|实例的网络连接类型-   Internet：外网连接；
-   Intranet：内网连接。

|
|LockMode|String|实例的锁定状态。取值范围如下：-   Unlock：正常；
-   ManualLock：手动触发锁定；
-   LockByExpiration：实例过期自动锁定；
-   LockByRestoration：实例回滚前自动锁定；
-   LockByDiskQuota：实例空间满自动锁定；
-   Released：实例已释放。此时实例无法进行解锁，只能使用备份数据重新创建新实例，重建时间较长，请耐心等待。

|
|LockReason|String|实例被锁定的原因。|
|MasterInstanceId|String|主实例的ID，如果没有返回此参数（即为null）则表示该实例是主实例。|
|GuardDBInstanceId|String|主实例如果有灾备实例，该参数即为备实例的ID。|
|TempDBInstanceId|String|主实例如果有临时实例，该参数即为临时实例的ID。|
|ReadOnlyDBInstanceId|List<ReadOnlyDBInstanceId\>|主实例下如果有只读实例，该参数为只读实例的ID列表。|

## ReadOnlyDBInstanceId参数 {#section_jxc_bp2_12b .section}

|名称|类型|描述|
|--|--|--|
|ReadOnlyDBInstanceId|String|只读实例的ID。|

## 请求示例 {#section_l4g_pj2_12b .section}

```
https://rds.aliyuncs.com/?Action=DescribeDBInstances
&RegionId=cn-hangzhou
&Engine=MySQL
&<公共请求参数>
```

## 返回示例 {#section_xtg_rj2_12b .section}

**XML格式**

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

**JSON格式**

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

