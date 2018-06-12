# Migrate from other RDS instances {#reference_kmq_42m_12b .reference}

## Description {#section_l21_v32_12b .section}

Migrate data from other RDS instances. It supports MySQL and SQL Server instances whose type are Dedicated Instances. For more inforamtion about the instance type, see [Instance type list](../intl.en-US/Product Introduction/Instance types/Instance type list.md#).

MySQL instances support batch database migration. During migration, the source instance status is “Migrating” and the destination instance status is “Importing data”. The following conditions must be met:

-   Database migration is performed between different instances that belong to the same user.

-   The instance is running.

-   The instance database is running.

-   The destination instance lock mode is Normal.

-   Destination instance storage space \> Space occupied by the destination instance – Destination instance database space + Source instance database space.

-   Databases to be migrated exist in both the source and destination instances and are activated.


SQL Server instances support batch database migration. During migration, the source instance status is “Migrating” and the destination instance status is “Importing data”. The following conditions must be met:

-   Database migration is performed between different instances that belong to the same user.

-   The instance is running.

-   The instance database is running.

-   The destination instance lock mode is Normal.

-   Destination instance storage space \> Space occupied by the destination instance – Destination instance database space + Source instance database space.


## Request parameters {#section_qzx_w32_12b .section}

|Name|Type|Required?|Description|
|----|----|---------|-----------|
|Action|String|Yes|Required parameter. Value: ImportDatabaseBetweenInstances.|
|DBInstanceId|String|Yes|Instance ID.|
|SourceDBInstanceId|String|Yes|Name of the source instance, which cannot be the same as the name of the instance to which the data is migrated.|
|DBInfo|String|Yes|Database information \(in the JSON string format\) of the instance to which data is migrated.-   For MySQL instances, the parameter value is an array, for example, \{“DBNames”:\[“mydb”,”mydb2”\]\}. For the MySQL type, the names of the source database and destination database must be the same. In the example, data is migrated to two databases \(mydb and mydb2\), which must exist in the source and destination instances.
-   For SQL For SQL Server instances, the parameter value is in the format of key-value pair, where key indicates the source database, and the destination is the database to which data is migrated, for example, \{“DBNames”:\{“srcdb”:”destdb”,”srcdb2”:”destmydb2”\}\}. For the SQLServer type, the names of the source database and destination database may be different. In this example, the data of srcdb is migrated to destdb, and the data of srcdb2 is migrated to destmydb2. However, the names of multiple source databases must be different, and the names of multiple destination databases must be different too.

|

## DBInfo parameters {#section_yx5_gfm_12b .section}

|Name|Type|Required?|Description|
|----|----|---------|-----------|
|DBNames|List|Yes|Names of the databases to be migrated, for example, \[“mydb”,”mydb2”\].|

## Return parameters {#section_a5x_zlh_12b .section}

|Name|Type|Required?|
|----|----|---------|
|<Public Return Parameters\>| |For more information, see [Public parameters](intl.en-US/API Reference/Use APIs/Public parameters.md#).|
|ImportId|Integer|ID of the instance to which data is imported.|

## Request example {#section_l4g_pj2_12b .section}

```
https://rds.aliyuncs.com/?Action=ImportDatabaseBetweenInstances
&DBInstanceId=riauvjz6zajfiq6ba1370329449201
&SourceDBInstanceId=rdsmn6nqimn6nqi
&{"DBNames":["mydb","mydb2"]}
&<Public Request Parameters>
```

## Return example {#section_xtg_rj2_12b .section}

**XML format**

```
<ImportDatabaseBetweenInstancesResponse>
         <ImportId>2122321</ImportId>
       <RequestId>5A77D650-27A1-4E08-AD9E-59008EDB6927</RequestId>
</ImportDatabaseBetweenInstancesResponse>
```

**JSON format**

```

       "ImportId":2122321
       "RequestId":"5A77D650-27A1-4E08-AD9E-59008EDB6927"

```

