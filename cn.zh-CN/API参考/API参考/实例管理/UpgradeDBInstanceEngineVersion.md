# UpgradeDBInstanceEngineVersion {#reference_t5m_dd2_12b .reference}

## 描述 {#section_l21_v32_12b .section}

该接口用于升级实例数据库版本，例如将数据库版本MySQL 5.1升级至MySQL 5.5版本。

如果主实例下挂载只读实例或者灾备实例，请先升级只读实例或者灾备实例的数据库版本。操作必须满足以下条件，否则操作将失败：

-   实例状态为运行中。
-   输入的数据库版本号必须大于当前实例的版本号。

## 请求参数 {#section_qzx_w32_12b .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是|系统规定参数，取值为UpgradeDBInstanceEngineVersion。|
|DBInstanceId|String|是|待升降级的实例。|
|EngineVersion|String|是|待升级到的数据库版本。|

## 返回参数 {#section_rpk_z32_12b .section}

|名称|类型|描述|
|--|--|--|
|<公共返回参数\>|-|详见[公共参数](cn.zh-CN/API参考/使用API/公共参数.md#)。|
|TaskId|Integer|任务ID。|

## 请求示例 {#section_l4g_pj2_12b .section}

```
https://rds.aliyuncs.com/?Action=UpgradeDBInstanceEngineVersion
&DBInstanceId=rdsaiiabnaiiabn
&EngineVersion=5.6
&<公共请求参数>
```

## 返回示例 {#section_xtg_rj2_12b .section}

**XML格式**

```
<UpgradeDBInstanceEngineVersionResponse>
         <RequestId>65BDA532-28AF-4122-AA39-B382721EEE64</RequestId>
           <TaskId>124378</Taskid>
</UpgradeDBInstanceEngineVersionResponse>
```

**JSON格式**

```
{
"RequestId": " 65BDA532-28AF-4122-AA39-B382721EEE64"
"TaskId":”124378”
  }
```

