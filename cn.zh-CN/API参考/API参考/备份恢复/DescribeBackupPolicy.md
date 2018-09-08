# DescribeBackupPolicy {#reference_lh1_ksl_12b .reference}

查看系统设置的备份策略。

## 请求参数 {#section_qzx_w32_12b .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是| 要执行的操作。取值：

 DescribeBackupPolicy。

 |
|DBInstanceId|String|是| 实例ID。

 |
|BackupPolicyMode|String|是| 备份模式：

 -   DataBackupPolicy：数据备份；
-   LogBackupPolicy：日志备份。

 |

## 返回参数 {#section_a5x_zlh_12b .section}

|名称|类型|描述|
|--|--|--|
|<公共返回参数\>|-| 详见[公共参数](cn.zh-CN/API参考/使用API/公共参数.md#)。

 |
|BackupRetentionPeriod|String| 数据备份保留天数（7到730天）。

 |
|PreferredBackupTime|String| 数据备份时间，格式：HH:mmZ- HH:mm Z。

 |
|PreferredBackupPeriod|String| 数据备份周期。

 -   Monday：周一；
-   Tuesday：周二；
-   Wednesday：周三；
-   Thursday：周四；
-   Friday：周五；
-   Saturday：周六；
-   Sunday：周日。

 |
|BackupLog|String| 日志备份状态：

 -   Enabled：开启；
-   Disabled：关闭。

 BackupType为FullBackup时，返回该字段。

 |
|LogBackupFrequency|String|日志备份频率：-   为空：表示与数据备份频率一致。默认值。
-   LogInterval：目前表示每30分钟备份一次。

该参数仅适用于SQL Server。

|
|LogBackupRetentionPeriod|String| 日志备份远端保留天数（7到730天）。

 |
|EnableBackupLog|String| 是否开启日志备份：

 -   True：开启；
-   False：关闭。

 |
|LocalLogRetentionHours|String| 日志备份本地保留小时数。

 |
|LocalLogRetentionSpace|String| 本地日志最大循环空间使用率

 |
|HighSpaceUsageProtection|String| 高磁盘占用，是否无条件清理Binlog。

 |

