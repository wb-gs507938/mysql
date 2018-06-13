# Apply for a read/write splitting address {#reference_nzs_lhf_12b .reference}

## Description {#section_l21_v32_12b .section}

You can apply for a read/write splitting address in the high security mode for a master instance that has read-only instances. The read/write splitting address does not affect the addresses of the master instance and its read-only instances, nor does it affect the application for intranet and Internet addresses.

The following conditions must be met, or the operation fails:

-   The master instance is running.

-   No migration tasks is ongoing.

-   The master instance has read-only instances.

-   The instance link is in the high security mode.


## Request parameters {#section_qzx_w32_12b .section}

|Name|Type|Required|Description|
|----|----|--------|-----------|
|Action|String|Yes|Required parameter. Set this parameter to AllocateReadWriteSplittingConnection.|
|DBInstanceId|String|Yes|Name of a master instance.|
|ConnectionStringPrefix|String|No| -   Prefix of the read/write splitting connection string. It must be globally unique.
-   The prefix must be a string of up to 30 characters including lowercase letters and hyphens \(-\). It must start with a letter.
-   The default prefix is in the format of “instance name + rw”.

 |
|Port|Int|No|Port number, ranging from 3001 to 3999. The default value is 3306.|
|MaxDelayTime|Int|No| -   Delay threshold, in seconds. The value range is 0 to 7200. If this parameter is not set, the default value is 30.
-   Read requests are not routed to the read-only instances with a delay greater than the threshold.

 |
|NetType|String|No|Network type of the read/write splitting connection string. Values are as follows:-   Internet
-   Intranet. This is the default value. The Intranet type must be consistent with that of the master instance.

|
|PrivateIpAddress|String|No| -   If the master instance uses the VPC network, and the network type of the read/write splitting link is set to Intranet, you can set this parameter to the VPC IP address of the read/write splitting link.
-   If this parameter is not set, the VPC IP address of the read/write splitting link is automatically allocated.

 |
|DistributionType|String|Yes|Read weight distribution mode. Values are as follows:-   Standard: indicates automatic weight distribution based on types.
-   Custom: indicates custom weight distribution.

|
|Weight|JSON/String|No| -   Read weight distribution. Enter the read weights for the master instance and its read-only instances.
-   Read weights increase at a step of 100 up to 10,000.
-   Enter weights in the following format: \{“Instanceid“:”Weight”,”Instanceid”:”Weight”\}
-   This parameter must be set when DistributionType is set to Custom.
-   This parameter is invalid when DistributionType is set to Standard.

 |

## Response parameters {#section_rpk_z32_12b .section}

|Name|Type|Description|
|----|----|-----------|
|<Common response parameters\>|-|For more information, see [Public parameters](intl.en-US/API Reference/Use APIs/Public parameters.md#).|

##   {#section_l4g_pj2_12b .section}

##   {#section_xtg_rj2_12b .section}

