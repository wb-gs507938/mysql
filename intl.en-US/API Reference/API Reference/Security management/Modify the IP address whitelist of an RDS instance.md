# Modify the IP address whitelist of an RDS instance {#reference_qfq_dmh_12b .reference}

## Description {#section_l21_v32_12b .section}

Modify the list of IP addresses that are allowed to access an instance. The operation is successful only if, the following conditions are fulfilled:

-   The instance is running.
-   The instance is not locked.

## Request parameters {#section_qzx_w32_12b .section}

|Name|Type|Required?|Description|
|----|----|---------|-----------|
|Action|String|Yes|Required parameter. Value: ModifySecurityIps.|
|DBInstanceId|String|Yes|Instance ID.|
|SecurityIps|String|No|List of IP addresses under the IP address whitelist array. The list contains up to 1,000 IP addresses, separated by commas. Supported formats include-   0.0.0.0/0, 10.23.12.24 \(IP\),
-   and 10.23.12.24/24 \(Classless Inter-Domain Routing \(CIDR\) mode. /24 represents the length of the prefix in an IP address. The range of the prefix length is \[1,32\]\).

|
|DBInstanceIPArrayName|String|No|Name of an IP address whitelist array. If no value is specified, the “Default” array is used. Note: One instance supports 50 whitelist arrays at most.|
|DBInstanceIPArrayAttribute|String|No|This parameter is left blank by default. This parameter differentiates attribute values. The console does not display arrays labeled as “hidden”.|
|Modifymode|String|No|Modification method. Optional values are as follows:-   Cover: Overwrite the original whitelist.
-   Append: Append the whitelist.
-   Delete: Delete the whitelist.

|

## Return parameters {#section_a5x_zlh_12b .section}

|Name|Type|Description|
|----|----|-----------|
|RequestId|String|For more information, see [Public parameters](intl.en-US/API Reference/Use APIs/Public parameters.md#).|
|TaskId|String|Task ID.|

## Request example {#section_l4g_pj2_12b .section}

```
https://rds.aliyuncs.com/?Action=ModifySecurityIps
&DBInstanceId=rdsaiiabnaiiabn
&SecurityIps=192.168.1.2
&<Public Request Parameters>
```

## Return example {#section_xtg_rj2_12b .section}

**XML format:**

```
<ModifySecurityIpsResponse>
         <RequestId>65BDA532-28AF-4122-AA39-B382721EEE64</RequestId>
</ModifySecurityIpsResponse>
```

**JSON format:**

```

    "RequestId": " 65BDA532-28AF-4122-AA39-B382721EEE64"

```

