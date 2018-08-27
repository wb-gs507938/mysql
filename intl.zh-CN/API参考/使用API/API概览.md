# API概览 {#reference_t1c_3hl_zdb .reference}

本文汇总了云数据库RDS所有可调用的API，各API的具体信息请参见相关文档。

## 实例管理 {#section_hp4_jhl_zdb .section}

|API|描述|
|---|--|
|[CreateDBInstance](intl.zh-CN/API参考/API参考/实例管理/CreateDBInstance.md#)|创建RDS实例|
|[DeleteDBInstance](intl.zh-CN/API参考/API参考/实例管理/DeleteDBInstance.md#)|释放RDS实例|
|[RestartDBInstance](intl.zh-CN/API参考/API参考/实例管理/RestartDBInstance.md#)|重启RDS实例|
|[DescribeDBInstanceAttribute](intl.zh-CN/API参考/API参考/实例管理/DescribeDBInstanceAttribute.md#)|查看RDS实例详情|
|[DescribeDBInstances](intl.zh-CN/API参考/API参考/实例管理/DescribeDBInstances.md#)|查看RDS实例列表|
|[ModifyDBInstanceSpec](intl.zh-CN/API参考/API参考/实例管理/ModifyDBInstanceSpec.md#)|变更RDS实例规格|
|[DescribeRegions](intl.zh-CN/API参考/API参考/实例管理/DescribeRegions.md#)|查询RDS地域和可用区信息|
|[DescribeDBInstanceHAConfig](intl.zh-CN/API参考/API参考/实例管理/DescribeDBInstanceHAConfig.md#)|查询RDS可用区信息和数据复制状态|
|[MigrateToOtherZone](intl.zh-CN/API参考/API参考/实例管理/MigrateToOtherZone.md#)|迁移RDS实例可用区|
|[PurgeDBInstanceLog](intl.zh-CN/API参考/API参考/实例管理/PurgeDBInstanceLog.md#)|清理RDS实例日志|
|[UpgradeDBInstanceEngineVersion](intl.zh-CN/API参考/API参考/实例管理/UpgradeDBInstanceEngineVersion.md#)|升级RDS实例版本|
|[ModifyDBInstanceDescription](https://help.aliyun.com/document_detail/26248.html)|修改RDS实例备注|
|[ModifyDBInstanceMaintainTime](intl.zh-CN/API参考/API参考/实例管理/ModifyDBInstanceMaintainTime.md#)|修改RDS实例可维护时间|
|[ModifyDBInstanceHAConfig](intl.zh-CN/API参考/API参考/实例管理/ModifyDBInstanceHAConfig.md#)|修改实例的数据复制模式和高可用策略|
|[SwitchDBInstanceHA](intl.zh-CN/API参考/API参考/实例管理/SwitchDBInstanceHA.md#)|切换RDS实例的主备|
|[DescribeDBInstanceSwitchLog](intl.zh-CN/API参考/API参考/实例管理/DescribeDBInstanceSwitchLog.md#)|查看实例的主备切换日志|
|[CreateReadOnlyDBInstance](intl.zh-CN/API参考/API参考/实例管理/CreateReadOnlyDBInstance.md#)|创建RDS只读实例|
|[DestroyDBInstance](intl.zh-CN/API参考/API参考/实例管理/DestroyDBInstance.md#)|销毁RDS实例|
|[ModifyDBInstanceDelayReplicationTime](intl.zh-CN/API参考/API参考/实例管理/ModifyDBInstanceDelayReplicationTime.md#)|修改只读实例延迟时间|

## 数据库代理 {#section_ptl_4hl_zdb .section}

|API|描述|
|---|--|
|[AllocateReadWriteSplittingConnection](intl.zh-CN/API参考/API参考/数据库代理/AllocateReadWriteSplittingConnection.md#)|申请读写分离地址|
|[CalculateDBInstanceWeight](intl.zh-CN/API参考/API参考/数据库代理/CalculateDBInstanceWeight.md#)|查询系统权重分配值|
|[ModifyReadWriteSplittingConnection](intl.zh-CN/API参考/API参考/数据库代理/ModifyReadWriteSplittingConnection.md#)|修改读写分离基本信息|
|[ReleaseReadWriteSplittingConnection](intl.zh-CN/API参考/API参考/数据库代理/ReleaseReadWriteSplittingConnection.md#)|释放读写分离地址|
|[ModifyDBInstanceConnectionMode](intl.zh-CN/API参考/API参考/数据库代理/ModifyDBInstanceConnectionMode.md#)|开启或关闭数据库代理|
|[ModifyDBInstanceProxyConfiguration](intl.zh-CN/API参考/API参考/数据库代理/ModifyDBInstanceProxyConfiguration.md#)|设置数据库代理|
|[ModifyDBInstanceProxyConfiguration](intl.zh-CN/API参考/API参考/数据库代理/ModifyDBInstanceProxyConfiguration.md#)|查看数据库代理|

## 数据库管理 {#section_btg_phl_zdb .section}

|API|描述|
|---|--|
|[CreateDatabase](intl.zh-CN/API参考/API参考/数据库管理/CreateDatabase.md#)|创建数据库|
|[DeleteDatabase](intl.zh-CN/API参考/API参考/数据库管理/DeleteDatabase.md#)|删除数据库|
|[DescribeDatabases](intl.zh-CN/API参考/API参考/数据库管理/DescribeDatabases.md#)|查看数据库列表|
|[ModifyDBDescription](intl.zh-CN/API参考/API参考/数据库管理/ModifyDBDescription.md#)|修改数据库备注|
|[CopyDatabase](intl.zh-CN/API参考/API参考/数据库管理/CopyDatabase.md#)|复制数据库SQL Server 2008 R2版|
|[CopyDatabaseBetweenInstances](intl.zh-CN/API参考/API参考/数据库管理/CopyDatabaseBetweenInstances.md)|在SQL Server 2012/2016实例间复制数据库|

## 账号管理 {#section_nbc_qhl_zdb .section}

|API|描述|
|---|--|
|[CreateAccount](intl.zh-CN/API参考/API参考/账号管理/CreateAccount.md#)|创建账号|
|[DeleteAccount](intl.zh-CN/API参考/API参考/账号管理/DeleteAccount.md#)|删除账号|
|[DescribeAccounts](intl.zh-CN/API参考/API参考/账号管理/DescribeAccounts.md#)|查看账号列表|
|[GrantAccountPrivilege](intl.zh-CN/API参考/API参考/账号管理/GrantAccountPrivilege.md#)|授权账号访问数据库|
|[RevokeAccountPrivilege](intl.zh-CN/API参考/API参考/账号管理/RevokeAccountPrivilege.md#)|撤销账号权限|
|[ModifyAccountDescription](intl.zh-CN/API参考/API参考/账号管理/ModifyAccountDescription.md#)|修改账号备注|
|[ResetAccountPassword](intl.zh-CN/API参考/API参考/账号管理/ResetAccountPassword.md#)|重置密码|
|[ResetAccount](intl.zh-CN/API参考/API参考/账号管理/ResetAccount.md#)|重置账号|

## 安全管理 {#section_stz_qhl_zdb .section}

|API|描述|
|---|--|
|[DescribeDBInstanceIPArrayList](intl.zh-CN/API参考/API参考/安全管理/DescribeDBInstanceIPArrayList.md#)|查看RDS实例IP白名单|
|[DescribeDBInstanceSSL](intl.zh-CN/API参考/API参考/安全管理/DescribeDBInstanceSSL.md#)|查询实例SSL链路|
|[DescribeDBInstanceTDE](intl.zh-CN/API参考/API参考/安全管理/DescribeDBInstanceTDE.md#)|查询实例数据加密状态|
|[ModifyDBInstanceSSL](intl.zh-CN/API参考/API参考/安全管理/ModifyDBInstanceSSL.md#)|修改实例SSL链路|
|[ModifyDBInstanceTDE](intl.zh-CN/API参考/API参考/安全管理/ModifyDBInstanceTDE.md#)|修改实例数据加密状态|
|[ModifySecurityIps](intl.zh-CN/API参考/API参考/安全管理/ModifySecurityIps.md#)|修改RDS实例IP白名单|

## 网络管理 {#section_wxx_rhl_zdb .section}

|API|描述|
|---|--|
|[AllocateInstancePublicConnection](intl.zh-CN/API参考/API参考/网络管理/AllocateInstancePublicConnection.md#)|申请实例的外网连接串|
|[DescribeDBInstanceNetInfo](intl.zh-CN/API参考/API参考/网络管理/DescribeDBInstanceNetInfo.md#)|查看所有连接串|
|[ModifyDBInstanceNetworkExpireTime](intl.zh-CN/API参考/API参考/网络管理/ModifyDBInstanceNetworkExpireTime.md#)|修改连接地址过期时间|
|[ModifyDBInstanceConnectionString](intl.zh-CN/API参考/API参考/网络管理/ModifyDBInstanceConnectionString.md#)|修改实例连接串的端口和名字|
|[ModifyDBInstanceNetworkType](intl.zh-CN/API参考/API参考/网络管理/ModifyDBInstanceNetworkType.md#)|修改RDS实例网络类型|
|[ReleaseInstancePublicConnection](intl.zh-CN/API参考/API参考/网络管理/ReleaseInstancePublicConnection.md#)|释放实例的外网连接串。|
|[SwitchDBInstanceNetType](intl.zh-CN/API参考/API参考/网络管理/SwitchDBInstanceNetType.md#)|申请内网连接串（原内外网切换）|

## 日志管理 {#section_xnx_shl_zdb .section}

|API|描述|
|---|--|
|[DescribeSlowLogs](intl.zh-CN/API参考/API参考/日志管理/DescribeSlowLogs.md#)|查看慢日志列表|
|[DescribeSlowLogRecords](intl.zh-CN/API参考/API参考/日志管理/DescribeSlowLogRecords.md#)|查看慢日志明细|
|[DescribeErrorLogs](intl.zh-CN/API参考/API参考/日志管理/DescribeErrorLogs.md#)|查看错误日志|
|[DescribeBinlogFiles](intl.zh-CN/API参考/API参考/日志管理/DescribeBinlogFiles.md#)|查看BINLOG日志|
|[DescribeSQLCollectorPolicy](intl.zh-CN/API参考/API参考/日志管理/DescribeSQLCollectorPolicy.md#)|查询SQL审计功能是否开启|
|[ModifySQLCollectorPolicy](intl.zh-CN/API参考/API参考/日志管理/ModifySQLCollectorPolicy.md#)|切换SQL采集状态|
|[DescribeSQLLogRecords](intl.zh-CN/API参考/API参考/日志管理/DescribeSQLLogRecords.md#)|查询SQL审计日志|
|[DescribeSQLLogFiles](intl.zh-CN/API参考/API参考/日志管理/DescribeSQLLogFiles.md#)|查询SQL审计文件列表|

## 备份恢复 {#section_nqs_thl_zdb .section}

|API|描述|
|---|--|
|[CreateBackup](intl.zh-CN/API参考/API参考/备份恢复/CreateBackup.md#)|创建备份|
|[CloneDBInstance](intl.zh-CN/API参考/API参考/备份恢复/CloneDBInstance.md#)|克隆RDS实例|
|[DescribeBackups](intl.zh-CN/API参考/API参考/备份恢复/DescribeBackups.md#)|查看备份列表|
|[CreateTempDBInstance](intl.zh-CN/API参考/API参考/备份恢复/CreateTempDBInstance.md#)|创建临时实例|
|[DescribeBackupPolicy](intl.zh-CN/API参考/API参考/备份恢复/DescribeBackupPolicy.md#)|查看备份策略|
|[ModifyBackupPolicy](intl.zh-CN/API参考/API参考/备份恢复/ModifyBackupPolicy.md#)|修改备份策略|
|[RestoreDBInstance](intl.zh-CN/API参考/API参考/备份恢复/RestoreDBInstance.md#)|恢复备份集到实例|
|[DeleteBackup](intl.zh-CN/API参考/API参考/备份恢复/DeleteBackup.md#)|删除数据备份文件|
|[DescribeBackupTasks](intl.zh-CN/API参考/API参考/备份恢复/DescribeBackupTasks.md#)|查询实例的备份任务列表|
|[RecoveryDBInstance](intl.zh-CN/API参考/API参考/备份恢复/RecoveryDBInstance.md#)|恢复数据库|

## SQL Server备份文件上云 {#section_kr4_5hl_zdb .section}

|API|描述|
|---|--|
|[CreateMigrateTask](intl.zh-CN/API参考/API参考/SQL Server备份文件上云/CreateMigrateTask.md#)|创建数据上云任务|
|[CreateOnlineDatabaseTask](intl.zh-CN/API参考/API参考/SQL Server备份文件上云/CreateOnlineDatabaseTask.md#)|打开数据库|
|[DescribeMigrateTasks](intl.zh-CN/API参考/API参考/SQL Server备份文件上云/DescribeMigrateTasks.md#)|查询数据上云任务列表|
|[DescribeOssDownloads](intl.zh-CN/API参考/API参考/SQL Server备份文件上云/DescribeOssDownloads.md#)|查看数据上云任务文件详情|

## 监控管理 {#section_phj_vhl_zdb .section}

|API|描述|
|---|--|
|[DescribeResourceUsage](intl.zh-CN/API参考/API参考/监控管理/DescribeResourceUsage.md#)|查看实例资源使用情况|
|[DescribeDBInstancePerformance](intl.zh-CN/API参考/API参考/监控管理/DescribeDBInstancePerformance.md#)|查看实例性能数据|
|[DescribeDBInstanceMonitor](intl.zh-CN/API参考/API参考/监控管理/DescribeDBInstanceMonitor.md#)|查询监控行为|
|[ModifyDBInstanceMonitor](intl.zh-CN/API参考/API参考/监控管理/ModifyDBInstanceMonitor.md#)|修改监控行为|

## 参数管理 {#section_zcd_whl_zdb .section}

|API|描述|
|---|--|
|[DescribeParameterTemplates](intl.zh-CN/API参考/API参考/参数管理/DescribeParameterTemplates.md#)|查看数据库参数模板|
|[DescribeParameters](intl.zh-CN/API参考/API参考/参数管理/DescribeParameters.md#)|查看当前实例数据库参数运行列表|
|[ModifyParameter](intl.zh-CN/API参考/API参考/参数管理/ModifyParameter.md#)|修改数据库参数列表|

## 数据迁移 {#section_k3w_whl_zdb .section}

|API|描述|
|---|--|
|[CreateUploadPathForSQLServer](intl.zh-CN/API参考/API参考/数据迁移/CreateUploadPathForSQLServer.md#)|获取文件上传地址|
|[DescribeFilesForSQLServer](intl.zh-CN/API参考/API参考/数据迁移/DescribeFilesForSQLServer.md#)|查看数据文件列表|
|[DescribeImportsForSQLServer](intl.zh-CN/API参考/API参考/数据迁移/DescribeImportsForSQLServer.md#)|查看导入列表|
|[ImportDatabaseBetweenInstances](intl.zh-CN/API参考/API参考/数据迁移/ImportDatabaseBetweenInstances.md#)|其它实例迁入|
|[CancelImport](intl.zh-CN/API参考/API参考/数据迁移/CancelImport.md#)|取消迁移|

## 标签管理 { .section}

|API|描述|
|---|--|
|[AddTagsToResource](intl.zh-CN/API参考/API参考/标签管理/AddTagsToResource.md#)|绑定标签|
|[DescribeTags](intl.zh-CN/API参考/API参考/标签管理/DescribeTags.md#)|查询标签|
|[RemoveTagsFromResource](intl.zh-CN/API参考/API参考/标签管理/RemoveTagsFromResource.md#)|解绑标签|

