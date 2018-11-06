# CreateReadOnlyDBInstance {#reference_ljz_xdf_12b .reference}

## 描述 {#section_l21_v32_12b .section}

该接口用于为某个实例创建一个只读实例。实例必须满足如下条件，否则操作将失败：

-   实例类型为MySQL。
-   主实例状态为运行中，且未处于容灾切换状态。
-   只读实例与主实例必须处于相同的地域。
-   只读实例数据库版本必须大于等于主实例版本，主实例最低为版本MySQL 5.6。
-   只读实例最低版本为MySQL 5.6。
-   一个RDS实例，最多只能有5个只读实例。

## 请求参数 {#section_qzx_w32_12b .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是|系统规定参数，取值为CreateReadOnlyDBInstance。|
|RegionId|String|是|数据中心，长度不超过50个字符。通过DescribeRegions查看可用的数据中心。|
|ZoneId|String|是|可用区id，通过DescribeRegions查看可用的可用区。|
|DBInstanceId|String|是|主实例ID。|
|EngineVersion|String|是|数据库版本号。取值：-   5.6
-   5.7

|
|DBInstanceClass|String|是|实例规格，详见附录。|
|DBInstanceStorage|Integer|是|自定义存储空间，取值范围：\[5,1000\]，每5G进行递增，单位：GB。|
|DBInstanceDescription|String|否| -   实例的描述或备注信息，不超过256个字节

-   不能以或https://开头，以中文、英文字母开头。可以包含中文、英文字符、“\_”、“-”，数字，长度为2~256个字符


 |
|PayType|String|是|取值为：Postpaid。|
|ClientToken|String|是|用于保证幂等性。|
|InstanceNetworkType|String|否| -   Classic：经典网络，不填时创建Classic实例；
-   VPC：VPC网络。

 |
|VPCId|String|否|VPC ID。|
|VSwitchId|String|否|VSwitch ID。|
|PrivateIpAddress|String|否|用户可以指定VSwitchId下的vpcIp。如果不输入，系统通过vpcId和VSwitchId自动分配。|

## 返回参数 {#section_rpk_z32_12b .section}

|名称|类型|描述|
|--|--|--|
|<公共返回参数\>|-|详见[公共参数](intl.zh-CN/API参考/使用API/公共参数.md#)。|
|DBInstanceId|String|实例名。|
|OrderId|String|订单ID。|
|ConnectionString|String|数据库连接地址。|
|Port|String|数据库连接端口。|

## 请求示例 {#section_l4g_pj2_12b .section}

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
        &<[公共请求参数]>
```

## 返回示例 {#section_xtg_rj2_12b .section}

**XML格式**

```
<CreateDBInstanceResponse>
        <OrderId>100789370230206</OrderId>
        <ConnectionString>rdsaiiabnaiiabn.mysql.rds.aliyuncs.com </ConnectionString>
        <DBInstanceId>rdsaiiabnaiiabn</DBInstanceId>
        <port>3306</port>
        <RequestId>1E43AAE0-BEE8-43DA-860D-EAF2AA0724DC</RequestId>
        </CreateDBInstanceResponse>
```

**JSON格式**

```
{
        "OrderId": "100789370230206", 
        "ConnectionString": "rdsaiiabnaiiabn.mysql.rds.aliyuncs.com", 
        "DBInstanceId": "rdsaiiabnaiiabn", 
        "Port": "3306", 
        "RequestId": "1E43AAE0-BEE8-43DA-860D-EAF2AA0724DC"
        }
```

