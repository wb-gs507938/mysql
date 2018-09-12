# View the backup policy {#reference_lh1_ksl_12b .reference}

## Description {#section_l21_v32_12b .section}

This API is used to view the backup policy set for the system. The RDS system periodically backs up an instance based on the user-defined system configuration.

## Request parameters {#section_qzx_w32_12b .section}

|Name|Type|Required or not|Description|
|----|----|---------------|-----------|
|Action|String|Yes|Required parameter. Value: DescribeBackupPolicy.|
|DBInstanceId|String|String|Instance ID|
|BackupPolicyMode|String|String| Backup mode

 -   DataBackupPolicy: data backup
-   LogBackupPolicy: log backup

 |

## Return parameters {#section_a5x_zlh_12b .section}

|Name|Type|Description|
|----|----|-----------|
|<Public Return Parameters\>|None|For more information, see [Public parameters](intl.en-US/API Reference/Use APIs/Public parameters.md#).|
|BackupRetentionPeriod|String|Retention days of the backup \(7 to 730 days\). The default value is 7 days.|
|PreferredBackupTime|String|Backup time, in the format of HH:mmZ- HH:mm Z.|
|PreferredBackupPeriod|String|Backup period. Value range:-   Monday
-   Tuesday
-   Wednesday
-   Thursday
-   Friday
-   Saturday
-   Sunday

|
|BackupLog|String|The default value is Enable. You can change it to Disabled.-   Enabled
-   Disabled

|
|LogBackupFrequency|String|Log backup interval:-   Null: The interval is the same as the data backup interval. This is the default value.
-   LogInterval: The interval is 30 minutes.

This parameter applies only to SQL Server.

|
|LogBackupRetentionPeriod|String|Retention days of the backup \(7 to 730 days\). The default value is 7 days.|
|EnableBackupLog|String| Whether to enable log backup:

 -   True: enable
-   False: disable

 |
|LocalLogRetentionHours|String| Retention hours of local log backups

 |
|LocalLogRetentionSpace|String| Maximum cycle space usage of local logs

 |
|HighSpaceUsageProtection|String| Whether to clear binlogs without any consideration in the case of high disk occupation

 |

