# DescribeDBInstances {#reference_pyz_mm2_12b .reference}

## 描述 {#section_l21_v32_12b .section}

该接口用于查看实例列表或被RAM授权的实例列表。

## 请求参数 {#section_qzx_w32_12b .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是|系统规定参数，取值为DescribeDBInstances。|
|RegionId|String|是|实例的region，通过函数DescribeRegions查看。|
|Engine|String|否|数据库类型，取值范围为MySQL/SQLServer/PostgreSQL/PPAS，不填则返回所有数据库类型。|
|DBInstanceType|String|否|实例类型，取值范围如下：-   Primary：主实例
-   Readonly：只读实例
-   Guard：灾备实例
-   Temp：临时实例

不填，默认返回所有。|
|InstanceNetworkType|String|否|取值范围如下：-   VPC：返回VPC实例
-   Classic：返回Classic实例

不填，默认返回所有。|
|ConnectionMode|String|否|-   Performance：为标准访问模式
-   Safty：为高安全访问模式

不填，默认返回所有。|
|Tags|String|否|查询绑定该标签的实例，传入值格式为Json string，包括TagKey和TagValue，TagKey不能为空，TagValue可为空。格式示例：\{“key1”:”value1”\}。|
|PageSize|Integer|否|每页记录数，取值：30/50/100，默认值：30。|
|PageNumber|Integer|否|页码，大于0且不超过Integer的最大值，默认值：1。|

## 返回参数 {#section_rpk_z32_12b .section}

|名称|类型|描述|
|--|--|--|
|<公共返回参数\>| |详见[公共参数](cn.zh-CN/API参考/使用API/公共参数.md#)。|
|Databases|List<Database\>|由Database组成的数据。|
|PageNumber|Integer|页码。|
|TotalRecordCount|Integer|总记录数。|
|PageRecordCount|Integer|本页DBInstance个数。|
|Items|List<DBInstance\>|由DBInstance组成的数组。|

## DBInstance的参数 {#section_ip3_142_12b .section}

|名称|类型|描述|
|--|--|--|
|DBInstanceId|String|实例名。|
|DBInstanceDescription|String|实例描述。|
|PayType|String|付费类型，取值如下：-   Postpaid：按量付费
-   Prepaid：预付费

|
|DBInstanceType|String| -   Primary：主实例。
-   Readonly：只读实例。
-   Guard：灾备实例。
-   Temp：临时实例。

 |
|InstanceNetworkType|String| -   VPC：返回VPC实例
-   Classic：返回Classic实例

 |
|ConnectionMode|String| -   Performance：标准访问模式
-   ：高安全访问模式

 |
|RegionId|String|地域。|
|ExpireTime|String|到期时间，按量付费实例无到期时间。|
|DBInstanceStatus|String|详见附录|
|Engine|String|数据库类型。|
|DBInstanceNetType|String| -   Internet：外网
-   Intranet：内网

 |
|LockMode|String| -   Unlock：正常
-   ManualLock：手动触发锁定
-   LockByExpiration：实例过期自动锁定
-   LockByRestoration：实例回滚前的自动锁定
-   LockByDiskQuota：实例空间满自动锁定

 |
|LockReason|String|被锁定的原因。|
|MasterInstanceId|String|主实例的ID，如果没有返回此参数（即为null）则表示该实例是主实例。|
|GuardDBInstanceId|String|该实例如果挂载灾备实例，即为备实例的ID。|
|TempDBInstanceId|String|该实例如果挂载临时实例，即为临时实例的ID。|
|ReadOnlyDBInstanceId|List<ReadOnlyDBInstanceId\>|主实例下挂载的只读实例ID列表。|

## ReadOnlyDBInstanceId参数 {#section_jxc_bp2_12b .section}

|名称|类型|描述|
|--|--|--|
|ReadOnlyDBInstanceId|String|只读实例ID。|

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

