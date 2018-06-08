# ImportDatabaseBetweenInstances {#reference_kmq_42m_12b .reference}

## 描述 {#section_l21_v32_12b .section}

从其它RDS实例迁入，支持MySQL和SQL Server的独享型实例，关于实例规格详情，请参见[实例规格表](../cn.zh-CN/产品简介/实例规格/实例规格表.md#)。

对于MySQL实例，支持批量数据库迁入。迁移过程中，源实例的状态处于“迁移中”，目标实例的状态处于“数据导入中”。实例需要满足如下条件，否则操作会失败：

-   适用于不同实例间（实例都属于同一个用户）的数据库迁移。

-   实例状态：运行中。

-   实例数据库状态：运行中。

-   目标实例锁定模式：正常。

-   目标实例的存储空间 \> 目标实例的使用空间－目标实例DB的空间 + 源实例数据库的空间。

-   待迁移数据库在源实例和目标实例都必须存在，而且是激活状态。


对于SQL Server实例，支持批量数据库迁入。迁移过程中，源实例的状态处于“迁移中”，目标实例的状态处于“数据导入中”。实例需要满足如下条件，否则操作会失败：

-   适用于不同实例间（实例都属于同一个用户）的数据库迁移。

-   实例状态：运行中。

-   实例数据库状态：运行中。

-   目标实例锁定模式：正常。

-   目标实例的存储空间 \> 目标实例的使用空间－目标实例数据库的空间 + 源实例数据库的空间。


## 请求参数 {#section_qzx_w32_12b .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是|系统规定参数，取值：ImportDatabaseBetweenInstances。|
|DBInstanceId|String|是|实例名。|
|SourceDBInstanceId|String|是|源实例名，不能与待迁移实例相同。|
|DBInfo|String|是|待迁移实例的数据库信息，JSON串格式。-   对于MySQL实例，值为数组，示例：\{“DBNames”:\[“mydb”,”mydb2”\]\}，MySQL类型要求源数据库和目的数据库名称必须一致，示例中的意思是两个数据库（mydb和mydb2）进行数据迁入，源实例和目的实例都有这两个数据库。
-   对于SQL Server实例，值为key-value对，key为原数据库，目标为迁移目标数据库，示例\{“DBNames”:\{“srcdb”:”destdb”,”srcdb2”:”destmydb2”\}\}，SQL Server允许源数据库和目标数据库名称可以不一致，示例的意思是将srcdb迁入至destdb，将srcdb2迁入至destmydb2。但是多个源数据库名称不允许一样，多个目标数据库名称也不允许一样。

|

## DBInfo参数 {#section_yx5_gfm_12b .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|DBNames|List|是|待迁移的数据库名称列表，如\[“mydb”,”mydb2”\]。|

## 返回参数 {#section_a5x_zlh_12b .section}

|名称|类型|描述|
|--|--|--|
|<公共返回参数\>| |详见[公共参数](cn.zh-CN/API参考/使用API/公共参数.md#)。|
|ImportId|Integer|导入实例ID。|

## 请求示例 {#section_l4g_pj2_12b .section}

```
https://rds.aliyuncs.com/?Action=ImportDatabaseBetweenInstances
&DBInstanceId=riauvjz6zajfiq6ba1370329449201
&SourceDBInstanceId=rdsmn6nqimn6nqi
&{"DBNames":["mydb","mydb2"]}
&<公共请求参数>
```

## 返回示例 {#section_xtg_rj2_12b .section}

**XML格式**

```
<ImportDatabaseBetweenInstancesResponse>
         <ImportId>2122321</ImportId>
       <RequestId>5A77D650-27A1-4E08-AD9E-59008EDB6927</RequestId>
</ImportDatabaseBetweenInstancesResponse>
```

**JSON格式**

```
{
       "ImportId":2122321
       "RequestId":"5A77D650-27A1-4E08-AD9E-59008EDB6927"
}
```

