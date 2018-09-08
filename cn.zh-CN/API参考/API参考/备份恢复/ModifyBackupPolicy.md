# ModifyBackupPolicy {#reference_uch_vsl_12b .reference}

修改备份策略，RDS根据用户设置的系统配置，定期做实例备份。

实例需满足以下条件，否则操作将失效：

-   实例为非只读实例。
-   实例状态为运行中。

## 请求参数 {#section_qzx_w32_12b .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是| 要执行的操作。取值：

 ModifyBackupPolicy。

 |
|DBInstanceId|String|是| 实例ID。

 |
|BackupPolicyMode|String|是| 备份策略模式：

 -   DataBackupPolicy：数据备份策略；
-   DuplicationPolicy：转储策略；
-   LogBackupPolicy：日志备份策略。

 |
|PreferredBackupTime|String|是| 备份时间。

 格式：HH:mmZ-HH:mmZ。

 BackupPolicyMode为DataBackupPolicy时，该参数必传。

 |
|PreferredBackupPeriod|String|是| 备份周期：

 -   Monday：周一；
-   Tuesday：周二；
-   Wednesday：周三；
-   Thursday：周四；
-   Friday：周五；
-   Saturday：周六；
-   Sunday：周日。

 如果传递多个参数，参数间用英文逗号（,）分割。

 BackupPolicyMode为DataBackupPolicy时，该参数必传。

 |
|BackupRetentionPeriod|String|否| 数据备份保留天数（7天到730天），默认为：7天。

 BackupPolicyMode为LogBackupPolicy时，该参数必传。

 |
|BackupLog|String|否| 日志是否可用：

 -   Enable：可用；
-   Disabled：不可用。

 默认为Enable。

 BackupPolicyMode为DataBackupPolicy时，该参数必传。

 |
|EnableBackupLog|String|否| 是否开启日志备份：

 -   True：开启；
-   False：关闭。

 BackupPolicyMode为LogBackupPolicy时，该参数必传。

 |
|LogBackupFrequency|String|否|日志备份频率：-   为空：表示与数据备份频率一致。默认值。
-   LogInterval：目前表示每30分钟备份一次。

该参数仅适用于SQL Server。

|
|LocalLogRetentionHours|String|否| 日志备份本地保留小时数。

 取值为0~7\*24，0表示不保留，默认为18。

 BackupPolicyMode为LogBackupPolicy时，该参数必传。

 |
|LocalLogRetentionSpace|String|否| 本地日志最大空间使用率。

 取值为0~50，此为循环空间，默认为30。

 BackupPolicyMode为LogBackupPolicy时，该参数必传。

 |
|HighSpaceUsageProtection|String|否| 实例使用空间\>= 90%，或者剩余空间< 5GB时，是否无条件清理Binlog：

 -   Disable：不清理；
-   Enable：清理。

 默认为Enable。

 BackupPolicyMode为LogBackupPolicy时，该参数必传。

 |
|Duplication|String|否| 是否开启备份文件转储至OSS。

 -   Disable：关闭；
-   Enable：开启。

 默认为Disable。

 |
|DuplicationContent|String|否| 数据备份或日志备份。

-   DATA：数据备份；
-   LOG：日志备份；
-   DATA&LOG：数据和日志同时备份。

 Duplication=Enable时，该参数必填。

 |
|DuplicationLocation|String|否| RAM授权RDS访问您的OSS，日志文件才能转储至OSS。

 授权方法如下：

 ```
{"Storage":"OSS","Location": {"Bucket": 'xxx', "Location":'cn-hangzhou',"OSSEndPoint":"oss-test","Object":"obje1"}
```

 如果Duplication=Enable，该参数必填。

 |

## 返回参数 {#section_a5x_zlh_12b .section}

|参数|类型|描述|
|--|--|--|
|requestId|String|请求ID。|

## 示例 {#section_l4g_pj2_12b .section}

**请求示例**

```
https://rds.aliyuncs.com/?Action=ModifyBackupPolicy
        &DBInstanceId=riauvjz6zajfiq6ba1370329449201
        &PreferredBackupTime=00:00Z—01:00Z
        &PreferredBackupPeriod=Monday
        &<公共请求参数>
```

**返回示例**

-   XML格式

    ```
    <CreateBackupResponse>
                <RequestId>DA147739-AEAD-4417-9089-65E9B1D8240D</RequestId>
                </CreateBackupResponse>
    ```

-   JSON格式

    ```
    {
                "RequestId":"DA147739-AEAD-4417-9089-65E9B1D8240D"
                }
    ```


