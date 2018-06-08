# DeleteBackup {#reference_bwt_vtl_12b .reference}

## 描述 {#section_l21_v32_12b .section}

删除存储时长大于日志备份保留周期且大于7天的数据备份文件。详情请参见[删除备份数据](../cn.zh-CN/用户指南/备份与恢复/删除备份数据.md#)。

只删除自身的备份集，不会删除所关联实例（只读、灾备、克隆等）的备份集。

实例必须满足以下条件，否则将操作失败：

-   实例状态为运行中。

-   实例引擎为MySQL、PostgreSQL或PPAS。


## 请求参数 {#section_qzx_w32_12b .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是|系统规定参数，取值：DeleteBackup。|
|DBInstanceId|String|是|实例名。|
|BackupId|String|是|备份集ID，可通过[DescribeBackups](cn.zh-CN/API参考/API参考/备份恢复/DescribeBackups.md#)获取。支持传入多组值，以逗号隔开，单次最多传入100个。只支持删除[DescribeBackups](cn.zh-CN/API参考/API参考/备份恢复/DescribeBackups.md#)中存储状态为Enable的备份集。|

## 返回参数 {#section_a5x_zlh_12b .section}

|参数|类型|说明|
|--|--|--|
|<公共返回参数\>|-|详见[公共参数](cn.zh-CN/API参考/使用API/公共参数.md#)。|

