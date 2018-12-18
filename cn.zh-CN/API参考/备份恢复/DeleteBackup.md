# DeleteBackup {#reference_bwt_vtl_12b .reference}

删除实例的备份集

## 注意事项 {#section_l21_v32_12b .section}

只删除实例自身的备份集，不会删除所关联实例（只读、灾备、克隆等）的备份集。

实例必须满足以下条件，否则将操作失败：

-   实例状态为运行中。
-   仅支持 MySQL、PostgreSQL、PPAS 的双机高可用版本。
-   当用户关闭日志备份时，即 RDS 实例不再支持按时间点恢复功能。此时用户可删除存储时长在 7 天以上的任意数据备份文件。
-   当用户开启日志备份时，只有超出日志备份保留时间的备份文件才能被删除。
    -   若日志备份保留时间和数据备份保留时间一致，则支持还原至存储周期内的任意时间点，但不支持删除备份文件。
    -   若日志备份保留时间小于数据备份保留时间，则数据备份保留时间大于日志备份保留时间的数据备份文件可以删除。

## 请求参数 {#section_qzx_w32_12b .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是| 要执行的操作，取值：

 DeleteBackup

 |
|DBInstanceId|String|是|实例ID。|
|BackupId|String|是| 备份集ID。

 可通过[DescribeBackups](intl.zh-CN/API参考/备份恢复/DescribeBackups.md#)获取。支持传入多组值，以英文逗号（,）隔开，单次最多传入100个。只支持删除[DescribeBackups](intl.zh-CN/API参考/备份恢复/DescribeBackups.md#)中存储状态为Enable的备份集。

 |

## 返回参数 {#section_a5x_zlh_12b .section}

|参数|类型|说明|
|--|--|--|
|<公共返回参数\>|-|详见[公共参数](intl.zh-CN/API参考/使用API/公共参数.md#)。|

