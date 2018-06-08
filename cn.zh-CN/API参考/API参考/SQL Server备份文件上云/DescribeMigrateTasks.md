# DescribeMigrateTasks {#reference_dpx_xvl_12b .reference}

## 描述 {#section_l21_v32_12b .section}

获取用户某个实例在一段时间内的迁移上云任务记录，限制条件如下：

-   目前，仅支持SQL Server 2008 R2版本的实例。

-   源文件必须是源数据库全量备份（FULL）文件。


## 请求参数 {#section_qzx_w32_12b .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是|系统规定参数，取值：DescribeMigrateTasks。|
|DBInstanceId|String|是|RDS实例名，例如：rm-xetesting。|
|StartTime|String|否|查询开始时间，格式如：2017-10-20T01:00Z。|
|EndTime|String|否|查询结束时间，必须大于开始时间，格式如：2017-10-25T01:00Z。|
|PageSize|Interger|否|每页记录数，可选值为30、50、100，默认值为30。|
|PageNumber|Interger|否|获取第几页的数据。|

## 返回参数 {#section_a5x_zlh_12b .section}

|参数|类型|说明|
|--|--|--|
|DBInstanceId|String|实例ID。|
|PageRecordCount|Integer|数据文件导入记录个数。|
|PageNumber|Integer|获取第几页的数据。|
|TotalRecordCount|Integer|满足条件的总的记录数。|
|Items|List|数据集合。|

## Items数据集合参数 {#section_rjp_cwl_12b .section}

|参数|类型|说明|
|--|--|--|
|MigrateTaskId|String|迁移任务的ID。|
|DBName|String|数据库名称。|
|CreateTime|String|迁移任务创建时间，格式为```
YYYY-MM-DD'T'HH:mm:ssZ
```

，例如2017-05-30 T12:11:4Z。|
|EndTime|String|迁移任务结束时间，格式为```
YYYY-MM-DD'T'HH:mm:ssZ
```

，例如2017-05-30 T12:11:4Z。|
|IsDBReplaced|String|是否是覆盖性导入，目前始终取True值。取值如下：-   False：否
-   True：是

|
|Status|String|迁移任务的状态，取值如下：-   NoStart：未开始
-   Running：运行中
-   Success：成功
-   Failed：失败
-   Waiting：等待 \(等待增量备份文件导入\)

|
|BackupMode|String|迁移上云任务类型，目前只取FULL值。可选值如下：-   FULL：全量备份文件一次性迁入
-   DIFF：增量备份文件一次性迁入
-   LOG：增量备份文件多次迁入

|
|Description|String|迁移任务的描述信息。|

