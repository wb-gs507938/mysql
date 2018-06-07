# CreateTempDBInstance {#reference_d4d_wrl_12b .reference}

## 描述 {#section_l21_v32_12b .section}

基于备份集或者7天内的一个时间点创建临时实例。临时实例创建成功后，账号和数据库将继承备份集数据。实例必须满足以下条件，否则将操作失败：

-   运行中。
-   没有迁移任务。
-   没有被锁定。
-   当前实例备份集的状态是：完成备份。

## 请求参数 {#section_qzx_w32_12b .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是|系统规定参数，取值：CreateTempDBInstance。|
|DBInstanceId|String|是|实例名。|
|BackupId|Integer|是|备份ID。|
|RestoreTime|String|否|7天之内并且早于当前时间半小时以上的任意时间点，默认时区为UTC。例如：2011-06-11T16:00:00Z。|

## 返回参数 {#section_a5x_zlh_12b .section}

|名称|类型|描述|
|--|--|--|
|<公共返回参数\>| |详见[公共参数](cn.zh-CN/API参考/使用API/公共参数.md#)。|
|TempDBInstanceId|String|子实例ID。|

## 请求示例 {#section_l4g_pj2_12b .section}

```
https://rds.aliyuncs.com/?Action=CreateTempDBInstance
&BackupId=90262
&DBInstanceId=riauvjz6zajfiq6ba1370329449201
&<公共请求参数>
```

## 返回示例 {#section_xtg_rj2_12b .section}

**XML格式**

```
<CreateChildDBInstanceResponse>
     <RequestId>248DE93F-8647-4B9D-8287-4A4A0FE56AD5</RequestId>
<TempDBInstanceId>sub1385954257106_junjunzhaasadsd</TempDBInstanceId>
</CreateChildDBInstanceResponse>
```

**JSON格式**

```
{
       "RequestId":"248DE93F-8647-4B9D-8287-4A4A0FE56AD5",
       "TempDBInstanceId":"sub1385954257106_junjunzhaasadsd"
}
```

