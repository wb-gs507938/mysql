# DescribeBackupDatabase {#reference_xct_2z2_sfb .reference}

查询备份集下的数据库列表。

## 请求参数 {#section_qzx_w32_12b .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是| 系统规定参数，取值：

 DescribeBackupDatabase。

 |
|DBInstanceId|String|是|实例ID。|
|BackupId|String|否|备份集ID。|
|RestoreTime|String|否|用户指定备份保留周期内的任意时间点，例如2011-06-11T16:00:00Z。**说明：** BackupId和RestoreTime两者至少传入一个。

|

## 返回参数 {#section_a5x_zlh_12b .section}

|参数|类型|描述|
|--|--|--|
|<公共返回参数\>|-|详见[公共参数](cn.zh-CN/API参考/使用API/公共参数.md#) 。|
|DatabaseNames|String|格式为"db1,db2"。|

## 示例 {#section_trc_4ks_c2b .section}

**请求示例**

```
https://rds.aliyuncs.com/?Action=DescribeBackupDatabase
&DBInstanceId=rm-xxxxxxx
&BackupId=90262
&RestoreTime=2011-06-11T16:00:00Z
&<公共请求参数>
```

**返回示例**

**JSON格式**

```
{ "DatabaseNames":"db1,db2", "RequestId":"08A3B71B-FE08-4B03-974F-CC7EA6DB1828" }
```

