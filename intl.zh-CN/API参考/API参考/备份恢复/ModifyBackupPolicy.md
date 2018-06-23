# ModifyBackupPolicy {#reference_uch_vsl_12b .reference}

## 描述 {#section_l21_v32_12b .section}

该接口用于修改备份策略，RDS根据用户设置的系统配置，定期做实例备份。

## 请求参数 {#section_qzx_w32_12b .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是|系统规定参数，取值为ModifyBackupPolicy。|
|DBInstanceId|String|是|实例名。|
|PreferredBackupTime|String|是|备份时间，格式：HH:mmZ-HH:mmZ。|
|PreferredBackupPeriod|String|是|备份周期，如果传递多个参数，参数间用英文逗号“,”分割。-   Monday：周一
-   Tuesday：周二
-   Wednesday：周三
-   Thursday：周四
-   Friday：周五
-   Saturday：周六
-   Sunday：周日

|
|BackupRetentionPeriod|String|否|数据备份保留天数（7天到730天），默认为7。|
|BackupLog|String|否|默认为Enable，可改为Disabled。|
|LogBackupRetentionPeriod|String|否| -   日志备份保留天数（7天到730天，且不大于数据备份保留天数）。当开启日志备份时，可设置日志备份文件的保留天数，目前仅支持MySQL/ PostgreSQL/ PPAS引擎设置该值。

 |

## 返回参数 {#section_a5x_zlh_12b .section}

|参数|类型|说明|
|--|--|--|
|<公共返回参数\>|-|详见[公共参数](intl.zh-CN/API参考/使用API/公共参数.md#)。|

## 请求示例 {#section_l4g_pj2_12b .section}

```
https://rds.aliyuncs.com/?Action=ModifyBackupPolicy
&DBInstanceId=riauvjz6zajfiq6ba1370329449201
&PreferredBackupTime=00:00Z—01:00Z
&PreferredBackupPeriod=Monday
&<公共请求参数>
```

## 返回示例 {#section_xtg_rj2_12b .section}

**XML格式**

```
<CreateBackupResponse>
         <RequestId>DA147739-AEAD-4417-9089-65E9B1D8240D</RequestId>
</CreateBackupResponse>
```

**JSON格式**

```
{
         "RequestId":"DA147739-AEAD-4417-9089-65E9B1D8240D"
}
```

