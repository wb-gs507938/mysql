# Modify the network type of an RDS instance {#reference_p24_w13_12b .reference}

## Description {#section_l21_v32_12b .section}

Switches VPC RDS to Classic mode, or vice versa.

**Note:** Only the Classic instances with the ConnectionMode of **Safty** can be switched to VPC mode.

## Request parameters {#section_qzx_w32_12b .section}

|Name|Type|Required|Description|
|----|----|--------|-----------|
|Action|String|Yes|Required parameter. Value: ModifyDBInstanceNetworkType.|
|DBInstanceId|String|Yes|Instance ID.|
|InstanceNetworkType|String|Yes| -   VPC: VPC instance;
-   Classic: classic instance.

 |
|VPCId|String|No|VPC ID.|
|VSwitchId|String|No|VSwitch ID,This input parameter is required if VPCID is not null.|
|PrivateIpAddress|String|No|IP address of an VPC under VSwitchId. If no value is specified, the system automatically assigns a VPC IP address based on VPCId and VSwitchId.|
|ReadWriteSplittingPrivateIpAddres|String|No| -   If the instance has an intranet read/write splitting address, the network type of the address also changes.
-   When switching to a VPC, you can specify the VPC IP of the read/write splitting link for the instance under VSwitchId.
-   If no value is specified, the system automatically assigns a VPC IP address based on VPCId and VSwitchId.

 |

## Return parameters {#section_a5x_zlh_12b .section}

|Name|Type|Description|
|----|----|-----------|
|<Public Return Parameters\>|-|For more information, see [Public parameters](intl.en-US/API Reference/Use APIs/Public parameters.md#).|

##   {#section_l4g_pj2_12b .section}

##   {#section_xtg_rj2_12b .section}

