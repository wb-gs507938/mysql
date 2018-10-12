# DescribeDBInstanceAttribute {#reference_ul2_zj2_12b .reference}

## 描述 {#section_l21_v32_12b .section}

该接口用于查看指定实例的详细属性。

## 请求参数 {#section_qzx_w32_12b .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是|系统规定参数，取值为DescribeDBInstanceAttribute。|
|DBInstanceId|String|是|实例ID，可以一次输入多个，以英文“,”分隔；最多传入30个。|
|ResourceGroupId|String|否|资源组ID。|

## 返回参数 {#section_rpk_z32_12b .section}

|名称|类型|描述|
|--|--|--|
|<公共返回参数\>|-|详情请参见[公共参数](intl.zh-CN/API参考/使用API/公共参数.md#)。|
|Items|List<DBInstanceAttribute\>|-|

**DBInstanceAttribute的参数**

|名称|类型|描述|
|--|--|--|
|DBInstanceId|String|实例ID。|
|PayType|String|实例付费方式：-   Postpaid：按量付费；
-   Prepaid：包年包月。

|
|DBInstanceType|String|实例类型：-   Primary：主实例；
-   Readonly：只读实例；
-   Guard：灾备实例；
-   Temp：临时实例。

|
|Category|String|实例系列：-   Basic：基础版；
-   HighAvailability：高可用版；
-   Finance：金融版。

|
|InstanceNetworkType|String|实例的网络类：-   Classic：经典网络；
-   VPC：VPC网络。

|
|ConnectionMode|String|实例的访问模式：-   Performance：标准访问模式；
-   Safty：高安全访问模式

|
|RegionId|String|地域。|
|ZoneId|String|可用区。|
|ConnectionString|String|连接地址。|
|Port|String|端口号。|
|Engine|String|数据库类型。|
|EngineVersion|String|数据库版本。|
|DBInstanceClassType|String|实例规格族：-   s：共享型；
-   x：通用型；
-   d：独享套餐；
-   h：独占物理机。

|
|DBInstanceMemory|Long|实例内存，单位：M。|
|DBInstanceStorage|Integer|实例存储空间，单位：GB。|
|DBInstanceNetType|String|网络连接方式：-   Internet：外网；
-   Intranet：内网。

|
|DBInstanceStatus|String|实例状态，详见[实例状态表](intl.zh-CN/API参考/API参考/附表/实例状态表.md#)。|
|DBInstanceDescription|String|实例备注。|
|LockMode|String|实例锁定模式：-   Unlock：正常；
-   ManualLock：手动触发锁定；
-   LockByExpiration：实例过期自动锁定；
-   LockByRestoration：实例回滚前的自动锁定；
-   LockByDiskQuota：实例空间满自动锁定。

|
|LockReason|String|实例被锁定的原因。|
|VpcId|String|VPC ID。|
|VSwitchId|String|VSwitch ID。|
|ResourceGroupId|String|资源组ID。|
|DBMaxQuantity|Integer|一个实例下可创建最大数据库数量。|
|AccountMaxQuantity|Integer|可创建账号的最大数量。|
|CreationTime|String|创建时间，格式：YYYY-MM-DD’T’hh:mm:ssZ，如2011-05-30T12:11:4Z。|
|ExpireTime|String|实例到期时间，按量付费实例无到期时间。|
|MaintainTime|String|实例可维护时间，如：00:00Z-02:00Z，表示0点到2点可进行例行维护。|
|AvailabilityValue|String|查询当年可用性实例可用性状态，单位：百分比。|
|MaxIOPS|Integer|最大IO请求次数，即IOPS。|
|MaxConnections|Integer|最大实例并发连接数。|
|DBInstanceCPU|String|实例CPU。|
|MasterInstanceId|String|主实例的ID，如果没有返回此参数（即为null）则该实例是主实例。|
|IncrementSourceDBInstanceId|String|增量数据来源的实例ID，如：-   灾备实例的增量数据来源是主实例。
-   只读实例的增量数据来源是主实例。
-   主实例的增量数据来源是NULL。

|
|GuardDBInstanceId|String|该实例如果挂载灾备实例，即为备实例的ID。|
|TempDBInstanceId|String|该实例如果挂载临时实例，即为临时实例ID。|
|ReadOnlyDBInstanceIds|List<OnlyDBInstanceId\>|主实例下挂载的只读实例ID列表。|
|SecurityIPList|String|已废弃，详情请参见[DescribeDBInstanceIPArrayList](intl.zh-CN/API参考/API参考/安全管理/DescribeDBInstanceIPArrayList.md#)接口。|
|DBInstanceDiskUsed|String|实例存储空间使用量，单位：B。|
|GuardDBInstanceName|String|灾备实例名称，NULL表示无灾备实例。|
|AdvancedFeatures|String|该参数目前只对SQL Server类型的实例有效，获取高级特性值，多个值之间用英文逗号“,”隔开，返回值如下：- LinkedServer - DistributeTransaction。|
|AccountType|String|账号类型：-   Normal：普通账号；
-   Super：超级账号；
-   Mix：混合账号。

|
|CanTempUpgrade|String|实例是否支持临时升级：-   true：支持；
-   false：不支持。

|
|TempUpgradeTimeStart|String|实例临时升级的开始时间，格式：YYYY-MM-DD’T’hh:mm:ssZ，如2011-05-30T12:11:4Z。|
|TempUpgradeTimeEnd|String|实例临时升级的结束时间，格式：YYYY-MM-DD’T’hh:mm:ssZ，如2011-05-30T12:11:4Z。|
|TempUpgradeRecoveryTime|String|实例恢复时间，格式：YYYY-MM-DD’T’hh:mm:ssZ，如2011-05-30T12:11:4Z。|
|TempUpgradeRecoveryClass|String|恢复规格。|
|TempUpgradeRecoveryCpu|String|恢复CPU。|
|TempUpgradeRecoveryMemory|String|恢复内存。|
|TempUpgradeRecoveryMaxIOPS|String|恢复最大IO请求次数。|
|TempUpgradeRecoveryMaxConnections|String|恢复并发连接数。|
|ReadDelayTime|String|只读实例对主实例的延迟时间，该参数仅对只读实例有效，单位为S。**说明：** 实例刚创建或实例异常时该值可能为NULL

|
|ReplicateId|String|灾备通道。|
|SupportUpgradeAccountType|String|账号是否支持临时升级：-   Yes：支持；
-   No：不支持。

 |
|SupportCreateSuperAccount|String|账号是否支持创建超级账号：-   Yes：支持；
-   No：不支持。

|
|ReadonlyInstanceSQLDelayedTime|String|只读实例延迟复制时间，只读实例延迟ReadonlyInstanceSQLDelayedTime的时间后再同步主实例数据，单位：秒。|

**ReadOnlyDBInstanceId**

|名称|类型|描述|
|--|--|--|
|<公共返回参数\>| |详见[公共参数](intl.zh-CN/API参考/使用API/公共参数.md#)。|
|DBInstanceId|String|只读实例ID。|

## 请求示例 {#section_l4g_pj2_12b .section}

```
https://rds.aliyuncs.com/?Action=DescribeDBInstanceAttribute
&DBInstanceId=rdsaiiabnaiiabn
&<公共请求参数>
```

## 返回示例 {#section_xtg_rj2_12b .section}

**XML格式**

```
<CreateDBInstanceResponse>
  <RequestId>3C5CFDEE-F774-4DED-89A2-1D76EC63C575</RequestId>
  <Items>
    <DBInstanceAttribute>
    <LockMode>Unlock</LockMode>
    <ConnectionString>rdsfnjfqu7vjnuj.mysql.rds.aliyuncs.com    </ConnectionString>
    <CreationTime>2014-10-10T10:28:48Z</CreationTime>
    <DBInstanceNetType>Internet</DBInstanceNetType>
    <MaxConnections>60</MaxConnections>
    <LockReason></LockReason>
    <Engine>MySQL</Engine>
    <AvailabilityValue>100.0%</AvailabilityValue>
    <AccountMaxQuantity>50</AccountMaxQuantity>
    <DBMaxQuantity>200</DBMaxQuantity>
    <RegionId>cn-hangzhou </RegionId>
    <ZoneId>cn-hangzhou-a</ZoneId>
    <ReadOnlyDBInstanceIds>
    <ReadOnlyDBInstanceId></ReadOnlyDBInstanceId>
    </ReadOnlyDBInstanceIds> 
    <TempDBInstanceId></TempDBInstanceId>
    <DBInstanceMemory>240</DBInstanceMemory>
    <MaxIOPS>150</MaxIOPS>
    <DBInstanceType>Primary</DBInstanceType>
    <DBInstanceStatus>Running</DBInstanceStatus>
    <MasterInstanceId></MasterInstanceId>
    <EngineVersion>5.5</EngineVersion>
    <IncrementSourceDBInstanceId></IncrementSourceDBInstanceId>
    <GuardDBInstanceId></GuardDBInstanceId>
    <DBInstanceStorage>10</DBInstanceStorage>
    <DBInstanceDescription></DBInstanceDescription>
    <DBInstanceId>rdsfnjfqu7vjnuj</DBInstanceId>
    <PayType>Postpaid</PayType>
    <ExpireTime></ExpireTime>
    <MaintainTime></MaintainTime>
    <DBInstanceClass>rds.mys2.small</DBInstanceClass>
    <SecurityIPList>11.11.11.11</SecurityIPList>
    <Port>3306</Port>
    <AdvancedFeatures>LinkedServer,DistributeTransaction</AdvancedFeatures>
    </DBInstanceAttribute>
</CreateDBInstanceResponse>
```

**JSON格式**

```
{
  "Items": {
    "DBInstanceAttribute": [
      {
        "LockMode": "Unlock", 
        "ConnectionString": "rdsfnjfqu7vjnuj.mysql.rds.aliyuncs.com", 
        "CreationTime": "2014-10-10T10:28:48Z", 
        "DBInstanceNetType": "Internet", 
        "ReadOnlyDBInstanceIds": {
          "ReadOnlyDBInstanceId": []
        }, 
        "MaxConnections": 60, 
        "LockReason": "", 
        "Engine": "MySQL", 
        "AvailabilityValue": "100.0%", 
        "AccountMaxQuantity": 50, 
        "DBMaxQuantity": 200, 
        "RegionId": "cn-hangzhou", 
        "TempDBInstanceId": "", 
        "DBInstanceMemory": 240, 
        "MaxIOPS": 150, 
        "DBInstanceType": "Primary", 
        "DBInstanceStatus": "Running", 
        "MasterInstanceId": "", 
        "EngineVersion": "5.5", 
        "IncrementSourceDBInstanceId": "", 
        "GuardDBInstanceId": "", 
        "DBInstanceStorage": 10, 
        "DBInstanceDescription": "", 
        "DBInstanceId": "rdsfnjfqu7vjnuj", 
        "PayType": "Postpaid", 
        "ExpireTime": "", 
        "MaintainTime": "", 
        "DBInstanceClass": "rds.mys2.small", 
        "SecurityIPList": "11.11.11.11", 
        "Port": "3306",
        "AdvancedFeatures": "LinkedServer,DistributeTransaction"
      }
    ]
  }, 
  "RequestId": "27BB49FA-DA47-4162-B39D-FC001E35C1C1"
}
```

