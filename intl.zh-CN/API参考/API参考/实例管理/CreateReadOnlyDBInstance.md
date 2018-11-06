# CreateReadOnlyDBInstance {#reference_ljz_xdf_12b .reference}

## 描述 {#section_l21_v32_12b .section}

该接口用于为某个实例创建一个只读实例。

只读实例数量：

-   如果主实例内存大于等于64GB，则最多允许创建10个只读实例。
-   如果主实例内存小于64GB，则最多允许创建5个只读实例。

-   主实例的版本必须为以下其中一种：
    -   MySQL 5.5
    -   MySQL 5.6
    -   MySQL 5.7高可用版（本地SSD盘）

## 请求参数 {#section_qzx_w32_12b .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是|系统规定参数，取值为CreateReadOnlyDBInstance。|
|RegionId|String|是|地域。只读实例的地域必须和主实例相同。通过DescribeRegions这个API可以查看地域列表。|
|ZoneId|String|是|可用区ID。通过DescribeRegions这个API可以查看可用区列表。|
|DBInstanceId|String|是|主实例ID。|
|EngineVersion|String|是|数据库版本号。必须与主实例相同。取值：-   5.6
-   5.7

|
|DBInstanceClass|String|是|实例规格，详见[实例规格表](../../../../intl.zh-CN/产品简介/实例规格/实例规格表.md)。建议只读实例规格不小于主实例规格，否则易导致只读实例延迟高、负载高等现象。|
|DBInstanceStorage|Integer|是|自定义存储空间，取值范围：\[5,1000\]，每5GB进行递增，单位：GB。|
|DBInstanceDescription|String|否| -   实例的描述或备注信息，不超过256个字节
-   不能以或https://开头，以中文、英文字母开头。可以包含中文、英文字符、“\_”、“-”，数字，长度为2~256个字符

 |
|PayType|String|是|取值为：Postpaid。|
|ClientToken|String|否|用于保证幂等性。|
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

