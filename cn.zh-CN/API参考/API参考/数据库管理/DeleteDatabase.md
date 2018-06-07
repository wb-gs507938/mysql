# DeleteDatabase {#reference_pml_l2g_12b .reference}

## 描述 {#section_l21_v32_12b .section}

该接口用于删除实例下的的某个数据库。接口必须满足以下条件，否则将调用失败：

-   实例状态运行中。

-   实例类型为主实例。


**说明：** PostgreSQL及PPAS实例中用户有权限通过SQL做DROP DATABASE操作，故此接口不支持PostgreSQL和PPAS。

## 请求参数 {#section_qzx_w32_12b .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是|系统规定参数，取值为DeleteDatabase。|
|DBInstanceId|String|是|实例名。|
|DBName|String|是|数据库名。|

## 返回参数 {#section_rpk_z32_12b .section}

|参数|类型|说明|
|--|--|--|
|<公共返回参数\>|-|详见[公共参数](cn.zh-CN/API参考/使用API/公共参数.md#)。|

## 请求示例 {#section_l4g_pj2_12b .section}

```
https://rds.aliyuncs.com/?Action=DeleteDatabase
&DBName=testdb02
&DBInstanceId=riauvjz6zajfiq6ba1370329449201
&<[公共请求参数]>
```

## 返回示例 {#section_xtg_rj2_12b .section}

**XML格式**

```
<DeleteDatabaseResponse>
         <RequestId>5A77D650-27A1-4E08-AD9E-59008EDB6927</RequestId>
</DeleteDatabaseResponse>
```

**JSON格式**

```
 {
      "RequestId":"07F6177E-6DE4-408A-BB4F-0723301340F3"
  }
```

