# View instance resource usage {#reference_qlz_4xl_12b .reference}

## Description {#section_l21_v32_12b .section}

View the resource usage information of an instance. After the interface is called, the system returns the size of the space occupied by a certain instance to the user. DBInstanceId is used to retrieve instance resource usage information.

## Request parameters {#section_qzx_w32_12b .section}

|Name|Type|Required?|Description|
|----|----|---------|-----------|
|Action|String|Yes|Required parameter. Value: DescribeResourceUsage.|
|DBInstanceId|String|Yes|Instance ID.|

## Return parameters {#section_a5x_zlh_12b .section}

|Name|Type|Description|
|----|----|-----------|
|<Public return parameter\>|None|For more information, see [Public parameters](intl.en-US//Public parameters.md#).|
|DBInstanceId|String|Instance ID.|
|Engine|String|Database type.|
|DiskUsed|Integer|Space used \(DataSize+ LogSize\). Unit: byte. -1 indicates no data.|
|DataSize|Integer|Space occupied by data files. Unit: byte. -1 indicates no data.|
|LogSize|Integer|Space occupied by logs. Unit: byte. -1 indicates no data.|
|BackupSize|Integer|Space occupied by backups. Unit: byte. -1 indicates no data.|
|ColdBackupSize|Integer|Size of the cold backup. Unit: byte. -1 indicates no data.|
|SQLSize|Integer|SQL size. Unit: byte. -1 indicates no data.|

## Request example {#section_l4g_pj2_12b .section}

## Response example {#section_xtg_rj2_12b .section}

