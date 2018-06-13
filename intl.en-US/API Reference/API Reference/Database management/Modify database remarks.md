# Modify database remarks {#reference_xbj_pfg_12b .reference}

## Description {#section_l21_v32_12b .section}

This interface is used to modify an instance remark name to allow you to easily record the instance. For example, you can modify the remark name to Instance Database A for Alibaba Cloud Testing Environment.

**Note:** This interface does not support PostgreSQL or PPAS.

## Request parameters {#section_qzx_w32_12b .section}

|Name|Type|Required|Description|
|----|----|--------|-----------|
|Action|String|Yes|Required parameter. Value: ModifyDBDescription.|
|DBInstanceId|String|Yes|Instance ID.|
|DBName|String|Yes|Name of a database.|
|DBDescription|String|Yes|Modify the database remarks.|

## Return parameters {#section_rpk_z32_12b .section}

|Name|Type|Description|
|----|----|-----------|
|<Public Return Parameters\>| |For more information, see [Public parameters](intl.en-US/API Reference/Use APIs/Public parameters.md#).|

## Request example {#section_l4g_pj2_12b .section}

```
https://rds.aliyuncs.com/?Action=ModifyDBDescription
&DBInstanceId=rdsaiiabnaiiabn
&DBInstanceDescription=testwangyichengDBdescribe
&<Public Request Parameters>
```

## Response example {#section_xtg_rj2_12b .section}

**XML format**

```
< ModifyDBDescriptionResponse>
         <RequestId>17F57FEE-EA4F-4337-8D2E-9C23CAA63D74</RequestId>
</ ModifyDBDescriptionResponse>
```

**JSON format**

```
{
    "RequestId": " 17F57FEE-EA4F-4337-8D2E-9C23CAA63D74"
  }
```

