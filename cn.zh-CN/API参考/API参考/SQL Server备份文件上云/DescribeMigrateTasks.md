# DescribeMigrateTasks {#reference_dpx_xvl_12b .reference}

查询实例在最近一周内的迁移上云任务记录。

## 请求参数 {#section_qzx_w32_12b .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是| 系统规定参数，取值：

 DescribeMigrateTasks

 |
|DBInstanceId|String|是|实例ID。|
|StartTime|String|是|查询开始时间，格式如：2017-10-20T01:00Z。|
|EndTime|String|是|查询结束时间，必须大于开始时间，格式如：2017-10-25T01:00Z。|
|PageSize|Integer|否|每页记录数，可选值为30、50、100，默认值为30。|
|PageNumber|Integer|否|获取第几页的数据。值要大于0，默认值为1。|

## 返回参数 {#section_a5x_zlh_12b .section}

|参数|类型|描述|
|--|--|--|
|DBInstanceId|String|实例ID。|
|PageRecordCount|Integer|数据文件导入记录个数。|
|PageNumber|Integer|获取第几页的数据。|
|TotalRecordCount|Integer|满足条件的总的记录数。|
|Items|List|数据集合。|

**Items参数**

|参数|类型|描述|
|--|--|--|
|MigrateTaskId|String|迁移任务的ID。|
|DBName|String|数据库名称。|
|CreateTime|String|导入任务开始时间，格式为：YYYY-MM-DD'T'HH:mm:ssZ，例如2017-05-30 T12:11:4Z。|
|EndTime|String|导入任务结束时间，格式为：YYYY-MM-DD'T'HH:mm:ssZ，例如2017-05-30 T13:11:4Z。|
|IsDBReplaced|String|是否是覆盖性导入，取值如下：-   False：否
-   True：是

|
|Status|String|迁移任务的状态，取值如下：-   NoStart：未开始
-   Running：运行中
-   Success：成功
-   Failed：失败
-   Waiting：等待 \(等待增量备份文件导入\)

|
|BackupMode|String|迁移上云任务类型，取值如下：-   FULL：全量备份文件一次性迁入。
-   DIFF：增量备份文件一次性迁入。
-   LOG：增量备份文件多次迁入。

目前恒定值为FULL。

|
|Description|String|迁移任务的描述信息。|

