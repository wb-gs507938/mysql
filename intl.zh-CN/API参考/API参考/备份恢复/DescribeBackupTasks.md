# DescribeBackupTasks {#reference_w3d_xvj_n2b .reference}

## 描述 {#section_w1r_gwj_n2b .section}

该接口用于查询实例的备份任务列表。

## 请求参数 {#section_bvb_kwj_n2b .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是|系统规定参数，取值：DescribeBackupTasks|
|DBInstanceId|String|是|实例ID|
|BackupJobId|String|否|备份任务ID。|

## 返回参数 {#section_ugq_nwj_n2b .section}

|参数|类型|描述|
|--|--|--|
|<公共返回参数\>|String|详见[公共参数](cn.zh-CN/API参考/使用API/公共参数.md#)。|
|Items|List|备份任务详情。|

## Item参数 {#section_tcl_pwj_n2b .section}

|参数|类型|描述|
|--|--|--|
|BackupStatus|String|备份运行状态：-   NoStart：关闭备份；
-   Preparing：准备备份；
-   Waiting：等待备份；
-   Uploading：上传备份；
-   Checking：检查备份；
-   Finished：完成备份。

|
|BackupJobId|String|备份任务ID。|

