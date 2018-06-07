# CreateDatabase {#reference_px5_g2g_12b .reference}

## 描述 {#section_l21_v32_12b .section}

该接口用于在某个实例下创建数据库，接口必须满足以下条件，否则将调用失败：

-   实例状态为运行中。

-   实例没有被锁定。

-   没有超出实例最大数据库数量。

-   实例类型是主实例。


**说明：** PostgreSQL及PPAS实例中用户有权限通过SQL做CREATE DATABASE操作，该接口不支持PostgreSQL和PPAS。

## 请求参数 {#section_qzx_w32_12b .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是|系统规定参数，取值为CreateDatabase。|
|DBInstanceId|String|是|实例名。|
|DBName|String|是|数据库名：-   由小写字母，数字、下划线组成，字母开头；
-   长度不超过64个字符；
-   其他非法字符，详见[禁用关键字表](cn.zh-CN/API参考/API参考/附表/禁用关键字表.md#)

|
|CharacterSetName|String|是|字符集，取值范围限定如下字符集：-   MySQL类型：
    -   utf8
    -   gbk
    -   latin1
    -   utf8mb4（MySQL 5.5和5.6有）
-   SQLServer类型：
    -   ChinesePRC\_CI\_AS
    -   Chinese\_PRC\_CS\_AS
    -   SQL\_Latin1\_General\_CP1\_CI\_AS
    -   SQL\_Latin1\_General\_CP1\_CS\_AS
    -   Chinese\_PRC\_BIN

|
|DBDescription|String|否|数据库描述：-   长度为2~256个字符；
-   不能以

    ```

    ```

或

    ```
https://开头
    ```

；

-   以中文、英文字母开头，包含中文、英文字符“”、“-”和数字。

|

## 返回参数 {#section_rpk_z32_12b .section}

|参数|类型|说明|
|--|--|--|
|<公共返回参数\>|-|详见[公共参数](cn.zh-CN/API参考/使用API/公共参数.md#)。|

## 请求示例 {#section_l4g_pj2_12b .section}

```
https://rds.aliyuncs.com/?Action=CreateDatabase
&CharacterSetName=gbk
&DBName=testdb02
&DBInstanceId=riauvjz6zajfiq6ba1370329449201
&<[公共请求参数]>
```

## 返回示例 {#section_xtg_rj2_12b .section}

**XML格式**

```
<CreateDatabaseResponse>
         <RequestId>5A77D650-27A1-4E08-AD9E-59008EDB6927</RequestId>
</CreateDatabaseResponse>
```

**JSON格式**

```
{
    "RequestID":"5A77D650-27A1-4E08-AD9E-59008EDB6927"
  }
```

