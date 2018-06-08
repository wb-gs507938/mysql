# ModifyDBInstanceDescription {#reference_bvb_hvt_12b .reference}

## 描述 {#section_ops_ghv_12b .section}

该接口用于修改实例的备注名，方便用户记录实例，比如为该实例修改备注名为“阿里云测试环境实例”。

## 请求参数 {#section_mpn_hhv_12b .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是|系统规定参数，取值为ModifyDBInstanceDescription。|
|DBInstanceId|String|是|实例名。|
|DBInstanceDescription|Sting|是|实例描述信息。|

## 返回参数 {#section_pbd_qhv_12b .section}

|名称|类型|描述|
|--|--|--|
|<公共返回参数\>|-|详见[公共参数](cn.zh-CN/API参考/使用API/公共参数.md#)。|

## 请求示例 {#section_qwj_rhv_12b .section}

```
https://rds.aliyuncs.com/?Action=ModifyDBInstanceDescription
&DBInstanceId=rdsaiiabnaiiabn
&DBInstanceDescription=testwangyichengdescribe
&<公共请求参数>
```

## 返回示例 {#section_umq_shv_12b .section}

**XML格式**

```
< ModifyDBInstanceDescriptionResponse>
         <RequestId>17F57FEE-EA4F-4337-8D2E-9C23CAA63D74</RequestId>
</ModifyDBInstanceDescriptionResponse>
```

**JSON格式**

```
{
    "RequestId": " 17F57FEE-EA4F-4337-8D2E-9C23CAA63D74"
}
```

