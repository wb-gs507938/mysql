# Modify the backup policy {#reference_uch_vsl_12b .reference}

## Description {#section_l21_v32_12b .section}

Modify the backup policy. The RDS system periodically backs up instances according to the user-defined system configuration.

## Request parameters {#section_qzx_w32_12b .section}

|Name|Type|Required|Description|
|----|----|--------|-----------|
|Action|String|Yes|Required parameter. Value: ModifyBackupPolicy.|
|DBInstanceId|String|Yes|Instance ID.|
|PreferredBackupTime|String|Yes|Backup time, in the format ofHH:mmZ- HH:mm Z.|
|PreferredBackupPeriod|String|Yes|Backup period. Values:-   Monday
-   Tuesday
-   Wednesday
-   Thursday
-   Friday
-   Saturday
-   Sunday

|
|BackupRetentionPeriod|String|No|Retention days of the backup \(7 to 730 days\). The default value is 7 days.|
|BackupLog|String|No|The default value is Enable. You can change it to Disabled.|
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

