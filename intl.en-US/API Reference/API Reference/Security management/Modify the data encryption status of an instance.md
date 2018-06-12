# Modify the data encryption status of an instance {#reference_urs_klh_12b .reference}

## Description {#section_l21_v32_12b .section}

This interface only supports MySQL 5.6 and SQL Server 2008 R2:

-   MySQL 5.6 supports only TDE enabling of instances, and does not accept the value of DBName. After activating TDE, if you want to recover data to a local server, decrypted the data through RDS first.

-   Before activating TDE, you need to activate KMS. If you have not activated KMS, you can activate it according to the guidance during the TDE activation.

-   SQL Server 2008R2 supports only TDE enabling and disabling of databases. When TDE is enabled on a database, the TDE status of the related instance is changed \(can only be enabled\).

-   For MySQL 5.6, you can enable TDE only for instances. Therefore, the value of DBName is not accepted.

-   After TDE is enabled, it cannot be disabled. TDE also results in considerable increase in CPU usage.


## Request parameters {#section_qzx_w32_12b .section}

|Name|Type|Required|Description|
|----|----|--------|-----------|
|Action|String|Yes|Required parameter. Value: ModifyDBInstanceTDE.|
|DBInstanceId|String|Yes|Instance ID.|
|TDEStatus|String|Yes| -   Enabled: TDE enabled.
-   Disabled: TDE disabled.

 |
|DBName|String|No|Database name. Up to 50 names can be entered at a time, which are separated by commas \(,\).|

## Return parameters {#section_a5x_zlh_12b .section}

|Name|Type|Description|
|----|----|-----------|
|<Public Return Parameters\>| |For more information, see [Public parameters](intl.en-US/API Reference/Use APIs/Public parameters.md#).|

##   {#section_l4g_pj2_12b .section}

##   {#section_xtg_rj2_12b .section}

