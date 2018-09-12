# Modify the backup policy {#reference_uch_vsl_12b .reference}

## Description {#section_l21_v32_12b .section}

This API is used to modify the backup policy. The RDS system periodically backs up instances according to the user-defined system configuration.

To modify the backup policy, the following conditions must be met:

-   The instance is not a read-only policy.
-   The instance is running.

## Request parameters {#section_qzx_w32_12b .section}

|Name|Type|Required or not|Description|
|----|----|---------------|-----------|
|Action|String|Yes|Required parameter. Value: ModifyBackupPolicy.|
|DBInstanceId|String|Yes|Instance ID|
|BackupPolicyMode|String|Yes| Backup policy mode. Value range:

 -   DataBackupPolicy: data backup policy
-   DuplicationPolicy: dumping policy
-   LogBackupPolicy: log backup policy

 |
|PreferredBackupTime|String|Yes|Backup time, in the format ofHH:mmZ- HH:mm Z.This parameter is mandatory when BackupPolicyMode is set to DataBackupPolicy.

|
|PreferredBackupPeriod|String|Yes|Backup period. Value range:-   Monday
-   Tuesday
-   Wednesday
-   Thursday
-   Friday
-   Saturday
-   Sunday

If multiple parameters are required, separate them with commas \(,\).

This parameter is mandatory when BackupPolicyMode is set to DataBackupPolicy.

|
|BackupRetentionPeriod|String|No|Retention days of the backup \(7 to 730 days\). The default value is 7 days.This parameter is mandatory when BackupPolicyMode is set to LogBackupPolicy.

|
|BackupLog|String|No|Whether log backup is available

-   Enable: available
-   Disabled: unavailable

The default value is Enable. This parameter is mandatory when BackupPolicyMode is set to DataBackupPolicy.

|
|EnableBackupLog|String|No| Whether to enable log backup:

 -   True: enable
-   False: disable

 This parameter is mandatory when BackupPolicyMode is set to LogBackupPolicy.

 |
|LogBackupFrequency|String|No|Log backup interval:-   Null: The interval is the same as the data backup interval. This is the default value.
-   LogInterval: The interval is 30 minutes.

This parameter applies only to SQL Server.

|
|LocalLogRetentionHours|String|No| Retention hours of local log backups

 Value range: 0 to 7x24. 0 indicates that local log backups are not reserved. The default value is 18.

 This parameter is mandatory when BackupPolicyMode is set to LogBackupPolicy.

 |
|LocalLogRetentionSpace|String|No| Maximum cycle space usage of local logs

 Value range: 0 to 50. This parameter indicates cycle space, and the default value is 30.

 This parameter is mandatory when BackupPolicyMode is set to LogBackupPolicy.

 |
|HighSpaceUsageProtection|String|No| When the instance space usage is higher than or equal to 90% or the residual space is smaller than 5 GB, whether to clear binlogs without any consideration in the case of high disk occupation:

 -   Disable: clear
-   Enable: not clear

 The default value is Enable.

 This parameter is mandatory when BackupPolicyMode is set to LogBackupPolicy.

 |
|Duplication|String|No| Whether to enable backup files to be dumped to OSS:

 -   Disable: disable
-   Enable: enable

 The default value is Disable.

 |
|DuplicationContent|String|No| Data backup or log backup:

-   DATA: data backup
-   LOG: log backup
-   DATA&LOG: both data and log backup

 This parameter is mandatory when Duplication is set to Enable.

 |
|LogBackupRetentionPeriod|String|No|Log backup retention days \(it can be 7 to 730 days, and cannot be greater than the data backup retention days\). When you enable log backup, you can set the number of days that the log backup files are retained. Currently, only MySQL, PostgreSQL, and PPAS instances support this parameter.|

## Return parameters {#section_a5x_zlh_12b .section}

|Name|Type|Description|
|----|----|-----------|
|<Public Return Parameters\>|-|For more information, see [Public parameters](intl.en-US/API Reference/Use APIs/Public parameters.md#).|

## Request example {#section_l4g_pj2_12b .section}

```
https://rds.aliyuncs.com/?Action=ModifyBackupPolicy
&DBInstanceId=riauvjz6zajfiq6ba1370329449201
&PreferredBackupTime=00:00Z—01:00Z
&PreferredBackupPeriod=Monday
&<Public Request Parameters>
```

## Return example {#section_xtg_rj2_12b .section}

**XML format**

```
<CreateBackupResponse>
         <RequestId>DA147739-AEAD-4417-9089-65E9B1D8240D</RequestId>
</CreateBackupResponse>
```

**JSON format**

```
{
         "RequestId":"DA147739-AEAD-4417-9089-65E9B1D8240D"
}
```

