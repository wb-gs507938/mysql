# Delete database {#reference_pml_l2g_12b .reference}

## Description {#section_l21_v32_12b .section}

You can delete databases from instances. To do this, the interface must meet the following conditions, otherwise the call will fail:

-   The instance status is Running.

-   The instance type is primary instance.


**Note:** Users of PostgreSQL and PPAS instances are permitted to perform the DROP DATABASE operation through SQL. Therefore, this interface does not support PostgreSQL and PPAS.

## Request parameters {#section_qzx_w32_12b .section}

|Name|Type|Required|Description|
|----|----|--------|-----------|
|Action|String|Yes|Required parameter. Value: DeleteDatabase.|
|DBInstanceId|String|Yes|Instance ID.|
|DBName|String|Yes|Name of a database.|

## Return parameters {#section_rpk_z32_12b .section}

|Name|Type|Description|
|----|----|-----------|
|<Public Return Parameters\>|-|For more information, see [Public parameters](intl.en-US/API Reference/Use APIs/Public parameters.md#).|

## Request example {#section_l4g_pj2_12b .section}

```
https://rds.aliyuncs.com/?Action=DeleteDatabase
&DBName=testdb02
&DBInstanceId=riauvjz6zajfiq6ba1370329449201
&<[Public Request Parameters]>
```

## Return example {#section_xtg_rj2_12b .section}

**XML format**

```
<DeleteDatabaseResponse>
         <RequestId>5A77D650-27A1-4E08-AD9E-59008EDB6927</RequestId>
</DeleteDatabaseResponse>
```

**JSON format**

```
 {
      "RequestId":"07F6177E-6DE4-408A-BB4F-0723301340F3"
  }
```

