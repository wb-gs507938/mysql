# RestoreDBInstance {#reference_jzj_4tl_12b .reference}

## 描述 {#section_l21_v32_12b .section}

将备份集覆盖性恢复到实例。实例必须满足以下条件，否则将操作失败：

-   运行中。

-   没有迁移任务。

-   没有被锁定。

-   当前实例备份集的状态是：完成备份。


## 请求参数 {#section_qzx_w32_12b .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是|系统规定参数，取值：RestoreDBInstance。|
|DBInstanceId|String|是|实例名。|
|BackupId|Integer|是|备份集ID。|

## 返回参数 {#section_a5x_zlh_12b .section}

|参数|类型|说明|
|--|--|--|
|<公共返回参数\>|-|详见[公共参数](cn.zh-CN/API参考/使用API/公共参数.md#)。|

## 请求示例 {#section_l4g_pj2_12b .section}

```
https://rds.aliyuncs.com/?Action=RestoreDBInstance
&BackupId=103916160
&DBInstanceId=rds91e395totd54461k3
&<公共请求参数>
```

## 返回示例 {#section_xtg_rj2_12b .section}

**XML格式**

```
<RestoreDBInstanceResponse>
     <RequestId>37441409-FFD1-40AA-8EC5-9ECF5E2F7C29</RequestId>
</RestoreDBInstanceResponse>
```

**JSON格式**

```
{"RequestId":"37441409-FFD1-40AA-8EC5-9ECF5E2F7C29"}
```

