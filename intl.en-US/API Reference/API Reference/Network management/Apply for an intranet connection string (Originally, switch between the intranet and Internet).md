# Apply for an intranet connection string \(Originally, switch between the intranet and Internet\) {#reference_mvb_pb3_12b .reference}

## Description {#section_l21_v32_12b .section}

You can switch between intranet and Internet when necessary. Specifically, an intranet instance can be switched to Internet, and vice versa. After switching, the connection address changes. You must modify the connection address in the code and restart the application.

The following conditions must be met, otherwise the modification will fail:

-   The instance is running.
-   There are less than 20 switching times within 24 hours.
-   The [Set access mode](../../../../intl.en-US/User Guide/Network management/Set access mode.md#) and [Instance type list](../../../../intl.en-US/Product Introduction/Instance types/Instance type list.md#) of an instance determine the address types.

    |Series|Version|Access mode|Connection address|
    |------|-------|-----------|------------------|
    |Basic Edition|     -   MySQL 5.7
    -   SQL Server 2012
 |Standard mode|     -   Intranet address
    -   Internet address
    -   Intranet and Internet addresses
 |
    |High-Availability Edition|     -   MySQL 5.5/5.6
    -   SQL Server 2008 R2
    -   PostgreSQL 9.4
    -   PPAS 9.3
 |Standard mode|     -   Intranet address
    -   Internet address
 |
    |Safe connection mode|     -   Intranet address
    -   Internet address
    -   Intranet and Internet addresses
 |
    |Finance Edition|MySQL 5.6|Standard mode|     -   Intranet address
    -   Internet address
 |
    |Safe connection mode|     -   Intranet address
    -   Internet address
    -   Intranet and Internet addresses
 |


## Request parameters {#section_qzx_w32_12b .section}

|Name|Type|Required|Description|
|----|----|--------|-----------|
|Action|String|Yes|Required parameter. Value: SwitchDBInstanceNetType.|
|DBInstanceId|String|Yes|Instance ID.|
|ConnectionStringPrefix|String|Yes|Prefix for new user connections to the database. It must be checked for uniqueness.-   It may consist of lowercase letters, numbers, and underlines,
-   and must start with a letter
-   and have no more than 30 characters.

|
|Port|Integer|No|Port ID. Value range: 3001-3999.|

## Return parameters {#section_a5x_zlh_12b .section}

|Name|Type|Description|
|----|----|-----------|
|<Public Return Parameters\>|-|For more information, see [Public parameters](intl.en-US/API Reference/Use APIs/Public parameters.md#).|

##   {#section_l4g_pj2_12b .section}

##   {#section_xtg_rj2_12b .section}

