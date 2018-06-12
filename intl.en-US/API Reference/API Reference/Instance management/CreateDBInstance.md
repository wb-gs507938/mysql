# CreateDBInstance {#reference_bh1_4c2_12b .reference}

## Description {#section_btq_bd2_12b .section}

Create an RDS instance. For the detailed information of instance type, see Instance type table.

## Request parameters {#section_kcp_bd2_12b .section}

|Name|Type|Required?|Description|
|----|----|---------|-----------|
|Action|String|Yes|Required parameter. Value: CreateDBInstance.|
|RegionId|String|Yes| Data center. The length cannot exceed 50 characters. The DescribeRegions function can be used to view available data centers.|
|ZoneId|String|No|Zone ID. The DescribeRegions function can be used to view available zones.|
|Engine|String|Yes|Database type. Value options: MySQL/SQLServer/PostgreSQL/PPAS|
|EngineVersion|String|Yes| Database version. Value options:

 -   MySQL: 5.5/5.6/5.7
-   SQLServer: 2008r2/2012/2012/web/2016\_web/2012\_std\_ha/2012\_ent\_ha/2016\_std\_ha/2016\_ent\_ha
-   PostgreSQL: 9.4
-   PPAS: 9.3

 |
|DBInstanceClass|String|Yes|Instance type. For more information, see [Instance type list](../intl.en-US/Product Introduction/Instance types/Instance type list.md#).|
|DBInstanceStorage|Integer|Yes| User-defined storage space. Value range:

 -   \[5, 2000\] for MySQL/PostgreSQL/PPAS HA dual node edition;
-   \[20,1000\] for MySQL 5.7 basic single node edition;
-   \[10, 2000\] for SQL Server 2008R2;
-   \[20,2000\] for SQL Server 2012 basic single node edition.
-   \[20,5000\] for SQL Server 2012 basic double node edition.
-   Increase progressively at a rate of 5 GB. The unit is GB. For more information, see [Instance type list](../intl.en-US/Product Introduction/Instance types/Instance type list.md#).

 |
|DBInstanceNetType|String|Yes|Network connection type of an instance.-   Internet: public network;
-   Intranet: private network.

|
|DBInstanceDescription|String|No| -   Instance description or remarks, no more than 256 bytes.
-   It cannot contain http:\> instance descriptions or remarks. No more than 256 bytes.
-   It cannot begin with http:// or https://.
-   It must start with a Chinese character or an English letter.
-   It may contain Chinese and English characters/letters, “\_”, “-“, and numbers. The length may be 2-256 characters.

 |
|SecurityIPList|String|Yes| -   List of IP addresses allowed to access all databases of an instance. The IP addresses are separated by commas and cannot be repeated. The list contains up to 1,000 IP addresses.
-   Supported formats include 0.0.0.0/0, 10.23.12.24 \(IP\), and 10.23.12.24/24 \(Classless Inter-Domain Routing \(CIDR\) mode. /24 represents the length of the prefix in an IP address. The range of the prefix length is \[1,32\].\) 0.0.0.0/0 indicates unrestricted.

 |
|PayType|String|Yes|Billing method. Postpaid:-   Postpaid: Pay-As-You-Go; 
-   Prepaid: Subscription.

|
|Period|String|No|This input parameter is required if PayType is set to Prepaid. The prepayment consists of two types: Year \(yearly\) and Month \(monthly\).|
|UsedTime|String|No| -   When the value of parameter Period is Year, the optional values of UsedTime is \[1,9\].
-   When the value of parameter Period is Month, the optional values of UsedTime is 1, 2, 3.

 |
|ClientToken|String|Yes|Used to guarantee idempotence.|
|InstanceNetworkType|String|No| -   VPC: VPC instance;
-   Classic: classic instance.
-   If no value is specified, a classic instance is created by default.

 |
|ConnectionMode|String|No|Performance: standard access mode; Safty: high security access mode. The RDS system assigns an access mode by default.|
|VPCId|String|No|VPC ID.|
|VSwitchId|String|No|VSwitch ID.|
|PrivateIpAddress|String|No|IP address of an VPC under VSwitchId. If no value is specified, the system automatically assigns a VPC IP address.|

## Return parameters {#section_ebr_jh2_12b .section}

|Name|Type|Description|
|<Public Return Parameters\>|-|For more information, see [Public parameters](intl.en-US/API Reference/Use APIs/Public parameters.md#).|
|DBInstanceId|String|Instance ID.|
|OrderId|String|Order ID.|
|ConnectionString|String|Database connection address.|
|Port|String|Port connecting to the database.|

## Request example {#section_ypj_nh2_12b .section}

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
&<[Public Request Parameters]>
```

## Response example {#section_ljc_qh2_12b .section}

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

