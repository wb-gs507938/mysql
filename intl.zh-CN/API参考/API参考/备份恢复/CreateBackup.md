# CreateBackup {#reference_ryg_rg3_12b .reference}

## 描述 {#section_xzk_krv_d2b .section}

该接口用于为实例创建一个备份集，一天之内一个实例可创建的备份集数量不超过10个。实例须满足以下条件，否则将导致创建备份集失败：

-   实例状态为运行中；
-   上一次创建备份集任务已经完成。

## 输入参数 {#section_hmb_rrv_d2b .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是|系统规定参数，取值：CreateBackup。|
|DBInstanceId|String|是|实例ID。|
|BackupMethod|String|否|备份类型-   Logical：逻辑备份，且逻辑备份不支持没有数据库的实例；
-   Physical：物理备份，默认值为Physical。SQL Server仅支持物理备份。

|
|BackupStrategy|String|否|BackupMethod取值为Logical时，份选择的围：-   db：单库备份；
-   instance：全实例备份。

|
|DBName|String|否|数据库列表，多个数据库之间用英文逗号隔开。-   数据库类型为 mysql，且BackupMethod=Logical&BackupStrategy=db时，该入参才有效；
-   数据库类型为 mssql，且BackupMethod=Physical 且BackupType=FullBackup 且BackupStrategy=db 时，该入参才有效。

|
|BackupType|String|否| -   Auto：自动计算是全量备份还是增量备份，默认值为Auto；
-   FullBackup：全量备份。

 |

## 返回参数 {#section_xbt_tsv_d2b .section}

|参数|类型|描述|
|--|--|--|
|RequestId|String|详见[公共参数](cn.zh-CN/API参考/使用API/公共参数.md#)。|
|BackupJobId|String|备份集ID。|

