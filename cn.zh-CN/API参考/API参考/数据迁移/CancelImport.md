# CancelImport {#reference_t1q_mfm_12b .reference}

## 描述 {#section_l21_v32_12b .section}

支持取消SQL Server的自建入云和其它RDS迁入（MySQL类型）的迁移任务。SQL Server类型的其它RDS迁入任务暂不支持取消迁移。

## 请求参数 {#section_qzx_w32_12b .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是|系统规定参数，取值：CancelImport。|
|DBInstanceId|String|是|实例名。|
|ImportId|Integer|是|迁移ID。|

## 返回参数 {#section_a5x_zlh_12b .section}

|名称|类型|描述|
|--|--|--|
|<公共返回参数\>|无|详见[公共参数](cn.zh-CN/API参考/使用API/公共参数.md#)。|

## 请求示例 {#section_l4g_pj2_12b .section}

```
https://rds.aliyuncs.com/?Action=CancelImport
&DBInstanceId=rdsaiiabnaiiabn
&ImportId=12342323
&<公共请求参数>
```

## 返回示例 {#section_xtg_rj2_12b .section}

**XML格式**

```
<CancelImportResponse>
       <RequestId>17F57FEE-EA4F-4337-8D2E-9C23CAA63D74</RequestId>
</CancelImportResponse>
```

**JSON格式**

```
{
  "RequestId": " 17F57FEE-EA4F-4337-8D2E-9C23CAA63D74"
}
```

