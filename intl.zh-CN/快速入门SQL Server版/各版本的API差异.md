# 各版本的API差异 {#concept_g41_hlb_wdb .concept}

## 实例管理 {#section_q3l_vlb_wdb .section}

|API|API 描述|高可用版|基础版|
|2016 标准版、企业版2012 标准版、企业版|2008 R2 企业版|2016 Web版2012 Web版2012 企业版|
|---|------|----|---|
|------------------------|-----------|--------------------------|
|CreateDBInstance|创建RDS实例|支持|支持|支持|
|RestartDBInstance|重启RDS实例|支持|支持|支持|
|DeleteDBInstance|释放RDS实例|支持|支持|支持|
|DescribeDBInstanceAttribute|查看RDS实例详情|支持|支持|支持|
|DescribeDBInstances|查看RDS实例列表|支持|支持|支持|
|ModifyDBInstancePayType|变更实例计费方式|支持|支持|支持|
|ModifyInstanceAutoRenewalAttribute|实例自动续费|支持|支持|支持|
|ModifyDBInstanceSpec|变更RDS实例规格|支持|支持|支持|
|ModifyDBInstanceDescription|修改RDS实例备注|支持|支持|支持|
|ModifySecurityIps|修改RDS实例IP白名单|支持|支持|支持|
|DescribeDBInstanceIPArrayList|查看RDS实例IP白名单|支持|支持|支持|
|PurgeDBInstanceLog|清理RDS实例日志|支持|支持|支持|
|ModifyDBInstanceMaintainTime|修改RDS实例可维护时间|支持|支持|支持|
|AllocateInstancePublicConnection|申请外网连接串|支持|支持|支持|
|ReleaseInstancePublicConnection|释放外网连接串|支持|支持|支持|
|ModifyDBInstanceConnectionString|修改连接串|支持|支持|支持|
|DescribeDBInstanceNetInfo|查看所有连接串|支持|支持|支持|
|DescribeRegions|查询RDS地域和可用区信息|支持|支持|支持|
|SwitchDBInstanceHA|切换RDS实例的主备|支持|支持|不支持|
|ModifyDBInstanceHAConfig|修改RDS实例数据复制和高可用策略|支持|支持|不支持|
|DescribeDBInstanceHAConfig|查询RDS可用区信息和数据复制状态|支持|支持|不支持|
|ModifyDBInstanceNetworkType|修改RDS实例网络类型|不支持|支持|支持|
|DescribeDBInstanceTDE|查询实例数据加密状态|不支持|支持|不支持|
|ModifyDBInstanceTDE|修改实例数据加密状态|不支持|支持|不支持|
|DescribeDBInstanceSSL|查询实例SSL链路|不支持|支持|不支持|
|ModifyDBInstanceSSL|修改实例SSL链路|不支持|支持|不支持|
|ModifyDBInstanceConnectionMode|修改RDS实例访问模式|不支持|支持|不支持|
|MigrateToOtherZone|迁移RDS实例可用区|不支持|支持|不支持|
|CreateReadOnlyDBInstance|创建RDS只读实例|不支持|不支持|不支持|
|SwitchDBInstanceNetType|申请内网连接串（原内外网切换）|不支持|不支持|不支持|
|UpgradeDBInstanceEngineVersion|升级RDS实例版本|不支持|不支持|不支持|

## 数据库管理 { .section}

|API|API 描述|高可用版|基础版|
|2016 标准版、企业版2012 标准版、企业版|2008 R2 企业版|2016 Web版2012 Web版2012 企业版|
|---|------|----|---|
|------------------------|-----------|--------------------------|
|CreateDatabase|创建数据库|不支持|支持|不支持|
|DeleteDatabase|删除数据库|不支持|支持|不支持|
|DescribeDatabases|查看数据库列表|不支持|支持|不支持|
|ModifyDBDescription|修改数据库备注|不支持|支持|不支持|

## 账号管理 { .section}

|API|API 描述|高可用版|基础版|
|2016 标准版、企业版2012 标准版、企业版|2008 R2 企业版|2016 Web版2012 Web版2012 企业版|
|---|------|----|---|
|------------------------|-----------|--------------------------|
|CreateAccount|创建账号|支持|支持|支持|
|DescribeAccounts|查看账号列表|支持|支持|支持|
|ModifyAccountDescription|修改账号备注|支持|支持|支持|
|ResetAccountPassword|重置账号|支持|不支持|支持|
|DeleteAccount|删除账号|不支持|支持|不支持|
|GrantAccountPrivilege|授权账号权限|不支持|支持|不支持|
|RevokeAccountPrivilege|撤销账号权限|不支持|支持|不支持|
|ResetAccountPassword|重置密码|不支持|支持|不支持|

## 备份与恢复 { .section}

|API|API 描述|高可用版|基础版|
|2016 标准版、企业版2012 标准版、企业版|2008 R2 企业版|2016 Web版2012 Web版2012 企业版|
|---|------|----|---|
|------------------------|-----------|--------------------------|
|CreateBackup|创建备份|支持|支持|支持|
|DescribeBackups|查看备份列表|支持|支持|支持|
|DescribeBackupPolicy|查看备份策略|支持|支持|支持|
|ModifyBackupPolicy|修改备份策略|支持|支持|支持|
|RestoreDBInstance|恢复备份集到实例|不支持|支持|支持|
|CreateTempDBInstance|创建临时实例|不支持|支持|支持|
|DeleteBackup|删除数据备份文件|不支持|不支持|不支持|
|CloneDBInstance|克隆RDS实例|不支持|不支持|不支持|

## 监控 { .section}

|API|API 描述|高可用版|基础版|
|2016 标准版、企业版2012 标准版、企业版|2008 R2 企业版|2016 Web版2012 Web版2012 企业版|
|---|------|----|---|
|------------------------|-----------|--------------------------|
|DescribeResourceUsage|查看实例资源使用情况|支持|支持|支持|
|DescribeDBInstancePerformance|查看实例性能数据|支持|支持|支持|
|DescribeDBInstanceMonitor|查询监控行为|支持|支持|支持|
|ModifyDBInstanceMonitor|修改监控行为|支持|支持|支持|

## 参数设置 {#section_g2v_dmb_wdb .section}

|API|API 描述|高可用版|基础版|
|2016 标准版、企业版2012 标准版、企业版|2008 R2 企业版|2016 Web版2012 Web版2012 企业版|
|---|------|----|---|
|------------------------|-----------|--------------------------|
|DescribeParameterTemplates|查看数据库参数模板|不支持|支持|不支持|
|DescribeParameters|查看当前实例数据库参数运行列表|不支持|支持|不支持|
|ModifyParameter|修改数据库参数列表|不支持|支持|不支持|

## 性能优化 { .section}

|API|API 描述|高可用版|基础版|
|2016 标准版、企业版2012 标准版、企业版|2008 R2 企业版|2016 Web版2012 Web版2012 企业版|
|---|------|----|---|
|------------------------|-----------|--------------------------|
|DescribeSQLLogReports|查看SQL日志运行报告|不支持|不支持|不支持|
|DescribeOptimizeAdviceOnMissIndex|缺失索引建议|不支持|不支持|不支持|

## 标签管理 { .section}

|API|API 描述|高可用版|基础版|
|2016 标准版、企业版2012 标准版、企业版|2008 R2 企业版|2016 Web版2012 Web版2012 企业版|
|---|------|----|---|
|------------------------|-----------|--------------------------|
|AddTagsToResource|绑定标签|支持|支持|支持|
|DescribeTags|查询标签|支持|支持|支持|
|RemoveTagsFromResource|解绑标签|支持|支持|支持|

## 数据迁移 { .section}

|API|API 描述|高可用版|基础版|
|2016 标准版、企业版2012 标准版、企业版|2008 R2 企业版|2016 Web版2012 Web版2012 企业版|
|---|------|----|---|
|------------------------|-----------|--------------------------|
|CreateUploadPathForSQLServer|获取文件上传地址|不支持|支持|不支持|
|DescribeFilesForSQLServer|查看数据文件列表|不支持|支持|不支持|
|DescribeImportsForSQLServer|查看导入列表|不支持|支持|不支持|
|ImportDatabaseBetweenInstances|其他实例迁入|不支持|支持|不支持|
|CancelImport|取消迁移|不支持|支持|不支持|
|DescribeOssDownloads|查看数据上云任务文件详情|不支持|不支持|支持|
|CreateMigrateTask|创建数据上云任务|不支持|不支持|支持|
|DescribeMigrateTasks|查询数据上云任务列表|不支持|不支持|支持|

## 日志审计 { .section}

|API|API 描述|高可用版|基础版|
|2016 标准版、企业版2012 标准版、企业版|2008 R2 企业版|2016 Web版2012 Web版2012 企业版|
|---|------|----|---|
|------------------------|-----------|--------------------------|
|DescribeSlowLogs|查看慢日志列表|不支持|支持|不支持|
|DescribeSlowLogRecords|查看慢日志明细|不支持|支持|不支持|
|DescribeErrorLogs|查看错误日志|不支持|支持|不支持|
|DescribeSQLLogFiles|查询SQL审计文件列表|不支持|支持|不支持|
|DescribeSQLCollectorPolicy|查询SQL审计功能是否开启|不支持|支持|不支持|
|ModifySQLCollectorPolicy|切换SQL采集状态|不支持|支持|不支持|
|DescribeSQLLogRecords|查询SQL审计日志|不支持|支持|不支持|
|DescribeBinlogFiles|查看BINLOG日志|不支持|不支持|不支持|

