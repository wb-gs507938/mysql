# CreateBackup {#reference_ryg_rg3_12b .reference}

## 描述 {#section_l21_v32_12b .section}

可用来创建一个备份，限制一天之内一个实例创建备份不超过10个。实例必须满足以下条件，否则将创建失败：

-   使用中。
-   上一次备份已经完成。

## 请求参数 {#section_qzx_w32_12b .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是|系统规定参数，取值：CreateBackup。|
|DBInstanceId|String|是|实例名。|
|BackupMethod|String|否| -   Logical：逻辑备份
-   Physical：物理备份
-   默认值为Physical，逻辑备份不支持没有数据库的实例。
-   SQL Server仅支持物理备份。

 |
|BackupStrategy|String|否|逻辑备份可选备份范围。-   db：单库备份
-   instance：全实例备份
-   只有在BackupMethod=Logical的情况下，该入参才有效。

|
|DBName|String|否|逻辑单库备份，数据库名称。只有在BackupMethod=Logical&BackupStrategy=db的情况下，该入参才有效。|
|BackupType|String|否| -   Auto：自动计算是全量备份还是增量备份，默认值为Auto。
-   FullBackup：全量备份。

 |

## 返回参数 {#section_a5x_zlh_12b .section}

|名称|类型|描述|
|--|--|--|
|<公共返回参数\>| |详见[公共参数](cn.zh-CN/API参考/使用API/公共参数.md#)。|

## 请求示例 {#section_l4g_pj2_12b .section}

```
https://rds.aliyuncs.com/?Action= CreateBackup
&DBInstanceId=riauvjz6zajfiq6ba1370329449201
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

