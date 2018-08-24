# CopyDatabaseBetweenInstances {#concept_ulw_zkm_x2b .concept}

## 描述 {#section_l21_v32_12b .section}

该接口用于在实例间复制数据库。

**说明：** 仅适用于RDS for SQL Server 2012/2016实例。

## 前提条件 {#section_vzv_4pm_x2b .section}

-   源实例和目标实例同属于一个账户。
-   源实例和目标实例的版本相同。
-   源实例和目标实例在同一地域，可用区可以不同，网络类型需相同。
-   目标实例中没有和源实例同名的数据库。
-   目标实例的可用存储空间 \> 源实例中待复制数据库占用的空间。

## 请求参数 {#section_qzx_w32_12b .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是|系统规定参数，取值为CopyDatabaseBetweenInstances。|
|SourceDBInstanceId|String|是|源实例ID。|
|TargetDBInstanceId|String|是|目标实例ID，不能与源实例ID相同。|
|DBNames|String|是|待复制的数据库名列表，用英文逗号隔开。|
|SyncUserPrivilege|String|是|是否复制用户和权限：-   YES：表示复制用户和权限。如果目标实例中有同名的用户，则该用户将叠加源实例的同名用户的权限。
-   NO：表示不复制用户和权限。默认值。

|

## 返回参数 {#section_rpk_z32_12b .section}

|名称|类型|描述|
|--|--|--|
|<公共返回参数\>|String|详见[公共参数](cn.zh-CN/API参考/使用API/公共参数.md#)。|
|RequestId|String|Request ID。|
|CopyTaskId|String|迁移任务ID。|
|CopyResult|String|迁移结果：-   SUCCESS：成功。
-   FAILED：失败。

|

