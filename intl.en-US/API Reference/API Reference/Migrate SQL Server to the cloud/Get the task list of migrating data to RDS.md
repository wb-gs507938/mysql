# Get the task list of migrating data to RDS {#reference_dpx_xvl_12b .reference}

## Description {#section_l21_v32_12b .section}

This API gets the task records of migrating data to an RDS instance over a period of time. It has the following constraints:

-   Currently only SQL Server 2008 R2 instances are supported.

-   The source file must be the full backup file of the source database.


## Request parameters {#section_qzx_w32_12b .section}

|Name|Type|Required|Description|
|----|----|--------|-----------|
|Action|String|Yes|Name of the interface. Value: DescribeMigrateTasks.|
|DBInstanceId|String|Yes|Name of an RDS instance, for example, rm-xetesting.|
|StartTime|String|No|Start time, for example, 2017-10-20T01:00Z.|
|EndTime|String|No|End time, for example, 2017-10-25T01:00Z. It must be later than the start time.|
|PageSize|Integer|No|Number of records per page. Optional values: 30, 50, and 100. The default value is 30.|
|PageNumber|Integer|No|Number of the page containing the expected data.|

## Response parameters {#section_a5x_zlh_12b .section}

|Parameter|Type|Description|
|---------|----|-----------|
|DBInstanceId|String|Instance ID.|
|PageRecordCount|Integer|Number of data file import records.|
|PageNumber|Integer|Number of the page containing the expected data.|
|TotalRecordCount|Integer|Total number of matching records.|
|Items|List|Data set.|

## Parameters for Items {#section_rjp_cwl_12b .section}

|Parameter|Type|Description|
|---------|----|-----------|
|MigrateTaskId|String|ID of the migration task.|
|DBName|String|Database name.|
|CreateTime|String| Creation time of the migration task, in the format of```
YYYY-MM-DD'T'HH:mm:ssZ,
```

for example, 2017-05-30 T12:11:4Z .|
|EndTime|String|End time of the migration task, in the format of```
YYYY-MM-DD'T'HH:mm:ssZ,
```

for example, 2017-05-30 T12:11:4Z .|
|IsDBReplaced|String|Whether the migration overwrites existing data. Currently, only the value True can be returned. Optional values:-   False: Existing data is not overwritten.
-   True: Existing data is overwritten.

|
|Status|String|Migration status. Optional values:-   NoStart: Migration not started.
-   Running: Migration in progress.
-   Success: Migration successful.
-   Failed: Migration failed.
-   Waiting: Waiting to migrate incremental backup files.

|
|BackupMode|String|Data migration task type. Currently, only the value FULL can be returned.  Optional values:-   FULL: One-time full backup file migration.
-   DIFF: One-time incremental backup file migration.
-   LOG: Multiple migration tasks of incremental backup files.

|
|Description|String|Description about the migration task.|

##   {#section_l4g_pj2_12b .section}

##   {#section_xtg_rj2_12b .section}

