# CreateTempDBInstance {#reference_d4d_wrl_12b .reference}

基于备份集或者7天内的一个时间点创建临时实例。

临时实例创建成功后，账号和数据库将继承备份集数据。实例必须满足以下条件，否则操作将失败：

-   实例为RDS for SQL Server 2012/2016基础版或RDS for SQL Server 2008 R2高可用版。
-   实例状态为运行中。
-   当前实例中没有正在执行的迁移任务。
-   最近一次创建备份集任务已经完成。

## 请求参数 {#section_qzx_w32_12b .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是| 系统规定参数，取值：CreateTempDBInstance

 |
|DBInstanceId|String|是| 实例ID。

 |
|BackupId|Integer|是| 备份ID。

 |
|RestoreTime|String|否| 用户指定备份保留时间内的任意时间点。

 可以设置为7天之内并且早于当前时间半小时以上的任意时间点，默认时区为UTC。例如：2011-06-11T16:00:00Z。

 |

## 返回参数 {#section_a5x_zlh_12b .section}

|名称|类型|描述|
|--|--|--|
|<公共返回参数\>| | 详见[公共参数](intl.zh-CN/API参考/使用API/公共参数.md#)。

 |
|TempDBInstanceId|String|子实例ID。|

## 示例 {#section_l4g_pj2_12b .section}

**请求示例**

```
https://rds.aliyuncs.com/?Action=CreateTempDBInstance
        &BackupId=90262
        &DBInstanceId=riauvjz6zajfiq6ba1370329449201
        &<公共请求参数>
```

**返回示例**

-   **XML格式**

    ```
    <CreateChildDBInstanceResponse>
            <RequestId>248DE93F-8647-4B9D-8287-4A4A0FE56AD5</RequestId>
            <TempDBInstanceId>sub1385954257106_junjunzhaasadsd</TempDBInstanceId>
            </CreateChildDBInstanceResponse>
    ```

-   **JSON格式**

    ```
    {
            "RequestId":"248DE93F-8647-4B9D-8287-4A4A0FE56AD5",
            "TempDBInstanceId":"sub1385954257106_junjunzhaasadsd"
            }
    ```


