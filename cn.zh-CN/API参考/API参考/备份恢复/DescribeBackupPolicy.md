# DescribeBackupPolicy {#reference_lh1_ksl_12b .reference}

## 描述 {#section_l21_v32_12b .section}

查看系统设置的备份策略，RDS系统将根据用户设置的系统配置，定期做实例备份。

## 请求参数 {#section_qzx_w32_12b .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是|系统规定参数，取值：DescribeBackupPolicy。|
|DBInstanceId|String|是|实例名。|

## 返回参数 {#section_a5x_zlh_12b .section}

|名称|类型|描述|
|--|--|--|
|<公共返回参数\>|无|详见[公共参数](cn.zh-CN/API参考/使用API/公共参数.md#)。|
|BackupRetentionPeriod|String|数据备份保留天数（7到730天）。|
|PreferredBackupTime|String|数据备份时间，格式：HH:mmZ- HH:mm Z。|
|PreferredBackupPeriod|String|数据备份周期。-   Monday：周一
-   Tuesday：周二
-   Wednesday：周三
-   Thursday：周四
-   Friday：周五
-   Saturday：周六
-   Sunday：周日

|
|BackupLog|String|日志备份状态：-   Enabled：开启
-   Disabled：关闭

|
|LogBackupRetentionPeriod|String|日志备份保留天数（7到730天）。|

