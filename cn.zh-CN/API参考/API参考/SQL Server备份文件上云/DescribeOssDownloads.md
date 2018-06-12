# DescribeOssDownloads {#reference_dj4_pwl_12b .reference}

## 描述 {#section_l21_v32_12b .section}

查询数据上云任务详情，包括具体迁移文件详情。限制条件如下：

-   目前，仅支持SQL Server实例。

-   源文件必须是源数据库全量备份（FULL）文件。


## 请求参数 {#section_qzx_w32_12b .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是|系统规定参数，取值：DescribeOssDownloads。|
|DBInstanceId|String|是|实例ID。|
|MigrateTaskId|String|是|迁移任务的ID。|

## 返回参数 {#section_a5x_zlh_12b .section}

|名称|类型|说明|
|--|--|--|
|DBInstanceId|String|实例ID。|
|MigrateTaskId|String|迁移任务的ID。|
|Items|List|导入记录项。|

## Items数据集合参数 {#section_rjp_cwl_12b .section}

|参数|类型|说明|
|--|--|--|
|FileName|String|备份文件在OSS上的名字。|
|CreateTime|String|备份文件在下载列表中的创建时间。|
|BackupMode|String|迁移上云任务类型，目前只取FULL值。可选值如下：-   FULL：全量备份文件一次性迁入
-   DIFF：增量备份文件一次性迁入
-   LOG：增量备份文件多次迁入

|
|FileSize|String|备份文件大小，单位MB。|
|Status|String|文件状态，可选值如下：-   NoStart：未开始
-   Downloading：下载中
-   Finished：下载完成
-   DownloadFailed：下载失败
-   VerifyFailed：MD5校验失败
-   Deleted：已删除
-   DeleteFailed：删除失败
-   CheckSuccess：检查成功
-   CheckFailed：CheckFailed
-   Restoring：还原中
-   Restored：还原成功
-   RestoreFailed：还原失败

|
|IsAvailable|String|是否可用，可选值如下：-   False：否
-   True：是

|
|Description|String|文件描述信息。|

