# DescribeInstanceAutoRenewalAttribute {#reference_pz2_5lf_vdb .reference}

## 描述 {#section_by5_ytf_vdb .section}

创建RDS实例，关于实例规格，请参见[实例规格表](../cn.zh-CN/产品简介/实例规格/实例规格表.md#)。**示例****示例**

## 请求参数 {#section_ol5_15f_vdb .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是|系统规定参数，取值为CreateDBInstance。|
|RegionId|String|是|数据中心，长度不超过50个字符，通过函数DescribeRegions查看可用的数据中心。|
|ZoneId|String|否|可用区ID，通过函数DescribeRegions查看可用的可用区。|
|Engine|String|是|数据库类型，取值范围为MySQL/SQLServer/PostgreSQL/PPAS。|
|EngineVersion|String|是|数据库版本号，取值如下：MySQL：5.5/5.6/5.7；SQLServer：2008r2/2012/2012*web/2016\_web/2012\_std\_ha/2012\_ent\_ha/2016\_std\_ha/2016\_ent\_ha；PostgreSQL：9.4；PPAS：9.3。*|
|DBInstanceClass|String|是|实例规格，详见[实例规格表](../cn.zh-CN/产品简介/实例规格/实例规格表.md#)。|
|DBInstanceStorage|Integer|是|自定义存储空间，取值范围：MySQL/PostgreSQL/PPAS 双机高可用版为 \[5,2000\]；MySQL 5.7 单机基础版为 \[20,1000\]；SQL Server 2008R2 为 \[10,2000\]；SQL Server 2012/2016 单机基础版为 \[20,2000\]; SQL Server 2012/2016 双机高可用版为 \[20,5000\]; 每5G进行递增。单位：GB。详见[实例规格表](../cn.zh-CN/产品简介/实例规格/实例规格表.md#)。|
|DBInstanceNetType|String|是|实例的网络连接类型：Internet表示公网，Intranet表示私网。|
|DBInstanceDescription|String|否| -   实例的描述或备注信息，不超过256个字节。
-   不能以http:\>实例的描述或备注信息，不超过256个字节。
-   不能以http:// , https:// 开头。
-   以中文、英文字母开头。
-   可以包含中文、英文字符、””，” -”，数字字符长度2~256。

 |
|SecurityIPList|String|是| -   该实例下所有数据库的IP名单，以逗号隔开，不可重复，最多1000个。
-   支持格式：%，0.0.0.0/0，10.23.12.24（IP），或者10.23.12.24/24（CIDR模式，无类域间路由，/24表示了地址中前缀的长度，范围\[1,32\]）其中，0.0.0.0/0，表示不限制。

 |
|PayType|String|是|付费类型。Postpaid：后付费实例；Prepaid：预付费实例。|
|Period|String|否|若付费类型为Prepaid时该参数为必传参数。指定预付费实例为包年或者包月类型，Year：包年；Month：包月。|
|UsedTime|String|否| -   当参数Period为Year时，UsedTime可取值为\[1,9\]。
-   当参数Period为Month时，UsedTime可取值为1、2、3。

 |
|ClientToken|String|是|用于保证幂等性。|
|InstanceNetworkType|String|否|VPC：创建VPC实例；Classic：创建Classic实例；不填，默认创建Classic实例。|
|ConnectionMode|String|否|Performance为标准访问模式；Safty为高安全访问模式；默认为RDS系统分配。|
|VPCId|String|否|VPC ID。|
|VSwitchId|String|否|VSwitch ID，多个值用英文逗号“,”隔开。|
|PrivateIpAddress|String|否|用户可以指定VSwitchId下的vpcIp，如果不输入，系统自动分配。|

## 返回参数 {#section_t13_r5f_vdb .section}

|名称|类型|描述|
|--|--|--|
|<公共返回参数\>|-|详见[公共参数](https://help.aliyun.com/document_detail/26224.html)。|
|DBInstanceId|String|实例名。|
|OrderId|String|订单ID。|
|ConnectionString|String|数据库连接地址。|
|Port|String|数据库连接端口。|

## 示例 { .section}

-   请求示例

    ```
    
    https://rds.aliyuncs.com/?Action=CreateDBInstance
    &RegionId=cn-hangzhou
    &Engine=MySQL
    &EngineVersion=5.6
    &DBInstanceClass=rds.mys2.small
    &DBInstanceStorage=5
    &DBInstanceNetType=Internet
    &SecurityIPList=11.11.11.11
    &PayType=Postpaid
    &ClientToken=ETnLKlblzczshOTUbOCziJZNwHlYBQ
    &<[公共请求参数]>
    ```


