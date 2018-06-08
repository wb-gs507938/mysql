# ModifyDBInstanceSpec {#reference_ddv_lp2_12b .reference}

## 描述 {#section_l21_v32_12b .section}

该接口用于对按时付费实例的规格或者存储空间变更配置，使用该接口时必须满足如下条件，否则实例规格会变更失败：

-   实例状态为运行中
-   实例当前无正在运行的备份
-   请求参数中必须至少指定实例规格（DBInstanceClass）或存储空间（DBInstanceStorage）。
-   若降低磁盘空间配置，输入的磁盘空间不能小于实际使用空间大小的1.1倍。
-   当前只支持对常规实例和只读实例变更配置，不支持灾备实例和临时实例。

## 请求参数 {#section_qzx_w32_12b .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是|系统规定参数，取值为ModifyDBInstanceSpec。|
|DBInstanceId|String|是|待升降级的实例。|
|PayType|String|是|计费方式，取值为Postpaid，按时付费。|
|DBInstanceClass|String|否|实例规格，详见[实例规格表](../cn.zh-CN/产品简介/实例规格/实例规格表.md#)。|
|DBInstanceStorage|Integer|否|自定义存储空间，取值范围如下且取值必须为5的整数倍：-   MySQL为\[5,2000\]
-   SQL Server为\[10,2000\]
-   PostgreSQL和PPAS为\[5,2000\]

|

## 返回参数 {#section_rpk_z32_12b .section}

|名称|类型|描述|
|<公共返回参数\>|-|详见[公共参数](cn.zh-CN/API参考/使用API/公共参数.md#)。|

## 请求示例 {#section_l4g_pj2_12b .section}

```
https://rds.aliyuncs.com/?Action=ModifyDBInstanceSpec
&DBInstanceId=rdsaiiabnaiiabn
&PayType=Postpaid
&DBInstanceStorage=10
&<公共请求参数>
```

## 返回示例 {#section_xtg_rj2_12b .section}

**XML格式**

```
<ModifyDBInstanceSpecResponse>
         <RequestId>3C5CFDEE-F774-4DED-89A2-1D76EC63C575</RequestId>
</ModifyDBInstanceSpecResponse>
```

**JSON格式**

```
{
    "RequestId": " 3C5CFDEE-F774-4DED-89A2-1D76EC63C575 "
  }
```

