# CreateOnlineDatabaseTask {#reference_bxn_r2s_c2b .reference}

## 描述 {#section_wyn_tfs_c2b .section}

该接口用于打开数据库。

## 请求参数 {#section_rrm_5fs_c2b .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是|系统规定参数，取值：CreateOnlineDatabaseTask|
|DBInstanceId|String|是|实例名|
|DBName|String|是|数据库名|
|MigrateTaskId|String|是|迁移任务ID|
|CheckDBMode|String|是|打开数据库后一致性检查方法：-   SyncExecuteDBCheck\(同步执行DB检查\)；
-   AsyncExecuteDBCheck\(异步执行DB检查\)；默认值为AsyncExecuteDBCheck（兼容2008r2版本）。

 |

## 请求示例 {#section_bzw_2ts_c2b .section}

```
https://rds.aliyuncs.com/?Action=CreateOnlineDatabaseTask
&DBInstanceId=rm-xxxxxxx
&DBName=testDB
$MigrateTaskId=xxxxx
&CheckDBMode=AsyncExecuteDBCheck
&<公共请求参数>
```

## 返回示例 {#section_sst_gts_c2b .section}

```
{"code":"200","data":{"RequestId":"1B2EBD14-36F6-4645-A3F9-DE19D321C18F"},"requestId":"1B2EBD14-36F6-4645-A3F9-DE19D321C18F","successResponse":true}
```

