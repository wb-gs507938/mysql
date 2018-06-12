# View the IP address whitelist of an RDS instance {#reference_jgc_wbh_12b .reference}

## Description {#section_l21_v32_12b .section}

Show the list of IP addresses that are allowed to access an instance.

## Request parameters {#section_qzx_w32_12b .section}

|Name|Type|Required?|Description|
|----|----|---------|-----------|
|Action|String|Yes|Required parameter. Value: DescribeDBInstanceIPArrayList.|
|DBInstanceId|String|Yes|Instance ID.|

## Return parameters {#section_rpk_z32_12b .section}

|Name|Type|Description|
|----|----|-----------|
|<Public Return Parameters\>| |For more information, see [Public parameters](intl.en-US/API Reference/Use APIs/Public parameters.md#).|
|Items|List<DBInstanceIPArray\>|List of IP address whitelist arrays of an instance.|

## DBInstanceIPArray parameters {#section_wzp_cch_12b .section}

|Name|Type|Description|
|----|----|-----------|
|DBInstanceIPArrayName|String|Name of an IP address whitelist array.|
|DBInstanceIPArrayAttribute|String|This parameter is left blank by default. This parameter differentiates attribute values. The console does not display arrays labeled with “hidden”.|
|SecurityIPList|String|List of IP addresses under the IP address whitelist array. The list contains up to 1,000 IP addresses, separated by commas. Supported formats include-   0.0.0.0/0,
-   10.23.12.24 \(IP\),
-   and 10.23.12.24/24 \(Classless Inter-Domain Routing \(CIDR\) mode. /24 represents the length of the prefix in an IP address. The range of the prefix length is \[1,32\]\).

|

##   {#section_l4g_pj2_12b .section}

##   {#section_xtg_rj2_12b .section}

