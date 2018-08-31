# Create a database {#reference_px5_g2g_12b .reference}

## Description {#section_l21_v32_12b .section}

This API is used to create a new database in an instance. The instance must meet the following conditions:

-   The instance is running.
-   The instance is not locked.
-   The maximum number of databases in the instance is not exceeded.
-   The instance is primary instance.

**Note:** Users of PostgreSQL and PPAS instances are permitted to perform the CREATE DATABASE operation through SQL statements. Therefore, this API does not support PostgreSQL and PPAS.

## Request parameters {#section_qzx_w32_12b .section}

|Name|Type|Required or not|Description|
|----|----|---------------|-----------|
|Action|String|Yes|Required parameter. Value: CreateDatabase.|
|DBInstanceId|String|Yes|Instance name|
|DBName|String|Yes|Name of a database. The name must be unique and comply with the following rules:-   Consist of lower case letters, numbers, and underlines
-   Must start with a letter and have no more than 64 characters
-   For other invalid characters, see [Forbidden keywords table](intl.en-US/API Reference/API Reference/Appendix/Forbidden keywords table.md#).

|
|CharacterSetName|String|Yes|Character set. The value range is limited to the following:-   For MySQL:
    -   utf8
    -   gbk
    -   latin1
    -   utf8mb4 \(included in versions 5.5 and 5.6\)
-   For SQLServer:
    -   Chinese\_PRC\_CI\_AS
    -   Chinese\_PRC\_CS\_AS
    -   SQL\_Latin1\_General\_CP1\_CI\_AS
    -   SQL\_Latin1\_General\_CP1\_CS\_AS
    -   Chinese\_PRC\_BIN

|
|DBDescription|String|No|Database description, which must meet the following requirements:-   The length is 2 to 256 characters.
-   It cannot begin with

    ```

    ```

or

    ```
https://
    ```

.

-   It must start with a Chinese character or English letter. It can include Chinese and English characters, hyphens \(-\), and digits.

|

## Response parameters {#section_rpk_z32_12b .section}

|Name|Type|Description|
|----|----|-----------|
|<Public return parameters\>|-|For more information, see [Public parameters](intl.en-US/API Reference/Use APIs/Public parameters.md#).|

## Request example {#section_l4g_pj2_12b .section}

```
https://rds.aliyuncs.com/?Action=CreateDatabase
&CharacterSetName=gbk
&DBName=testdb02
&DBInstanceId=riauvjz6zajfiq6ba1370329449201
&<[Common request parameters]>
```

## Response example {#section_xtg_rj2_12b .section}

**XML format**

```
<CreateDatabaseResponse>
         <RequestId>5A77D650-27A1-4E08-AD9E-59008EDB6927</RequestId>
</CreateDatabaseResponse>
```

**JSON format**

```

    "RequestID":"5A77D650-27A1-4E08-AD9E-59008EDB6927"
  
```

