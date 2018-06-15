# CreateBackup {#reference_ryg_rg3_12b .reference}

## 描述 {#section_xzk_krv_d2b .section}

该接口用来创建一个备份，限制一天之内一个实例创建备份不超过10个。实例必须满足以下条件，否则将创建失败：

-   实例状态为运行中。
-   上一次备份已经完成。

## 输入参数 {#section_hmb_rrv_d2b .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是|系统规定参数，取值：CreateBackup。|
|DBInstanceId|String|是|实例名。|
|BackupMethod|String|否|备份类型-   Logical：逻辑备份；
-   Physical：物理备份，默认值为Physical，逻辑备份不支持没有数据库的实例；
-   SQL Server仅支持物理备份。

|
|BackupStrategy|String|否|逻辑备份可选备份范围：-   db：单库备份；
-   instance：全实例备份,只有在BackupMethod=Logical的情况下，该入参才有效。

|
|DBName|String|否| -   数据库列表，多个库之间用英文逗号隔开。
-   当数据库类型是 mysql时候，BackupMethod=Logical&BackupStrategy=db的情况下，该入参才有效。
-   当数据库类型是 mssql 时候，BackupMethod=Physical 且 BackupType=FullBackup 且BackupStrategy=db 情况下，该入参数有效。

 |
|BackupType|String|否| -   Auto：自动计算是全量备份还是增量备份，默认值为Auto；
-   FullBackup：全量备份。

 |

## 返回参数 {#section_xbt_tsv_d2b .section}

|参数|**类型**|**说明**|
|--|------|------|
|RequestId|String|详见[公共参数](cn.zh-CN/API参考/使用API/公共参数.md#)。|

