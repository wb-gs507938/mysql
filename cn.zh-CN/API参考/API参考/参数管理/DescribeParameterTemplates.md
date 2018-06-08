# DescribeParameterTemplates {#reference_szs_nzl_12b .reference}

## 描述 {#section_l21_v32_12b .section}

该接口返回参数模板列表，包含参数名、参数默认值、是否可修改、是否需要重启才能生效、参数校验规则（正则表达式）。

**说明：** 该接口只适用于MySQL和SQL Server类型的数据库。

## 请求参数 {#section_qzx_w32_12b .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是|系统规定参数，取值：DescribeParameterTemplates。|
|Engine|String|是|数据库类型，取值为MySQL或SQL Server。|
|EngineVersion|String|是|数据库版本号。MySQL数据库为5.1、5.5或5.6，SQL Server数据库为2008r2、2012\_web或2016\_web。|

## 返回参数 {#section_a5x_zlh_12b .section}

|名称|类型|描述|
|--|--|--|
|<公共返回参数\>| |详见[公共参数](cn.zh-CN/API参考/使用API/公共参数.md#)。|
|Engine|String|数据库类型。|
|EngineVersion|String|数据库版本号。|
|ParameterCount|Integer|参数个数。|
|Parameters| ```
List<TemplateRecord>
```

 |参数列表，格式为\{parameter1, parameter2, parameter3, …\}。|

## TemplateRecord参数 {#section_r33_vzl_12b .section}

|名称|类型|描述|
|--|--|--|
|ParameterName|String|参数名。|
|ParameterValue|String|参数默认值。|
|ForceModify|String|False：不可修改；True：可修改。|
|ForceRestart|String| -   False：需要重启数据库才能生效
-   True：立即生效

 |
|CheckingCode|String|校验代码，参数的可选范围，是一个正则表达式。|
|ParameterDescription|String|参数描述。|

## 请求示例 {#section_l4g_pj2_12b .section}

```
https://rds.aliyuncs.com/?Action=DescribeParameterTemplates
&Engine=SQLServer
&EngineVersion=2008r2
&<公共请求参数>
```

## 返回示例 {#section_xtg_rj2_12b .section}

**XML格式**

```
<DescribeParameterTemplatesResponse>
  <Engine>mssql</Engine>
  <EngineVersion>2008r2</EngineVersion>
  <ParameterCount>1</ParameterCount>
  <Parameters>
    <TemplateRecord>
    <CheckingCode>[0-100]</CheckingCode>
    <ForceRestart>True</ForceRestart>
    <Factor>1</Factor>
    <ParameterDescription>此选项设置服务器范围内的默认填充因子值。提供填充因子是为了优化索引数据存储和性能。</ParameterDescription>
    <ParameterName>fill factor</ParameterName>
    <ParameterValue>0</ParameterValue>
    <ForceModify>True</ForceModify>
    <Unit>INT</Unit>
    </TemplateRecord>
  </Parameters>
  <RequestId>7B96585A-0FF2-4979-8FE5-7D147A29FDC0</RequestId>
</DescribeParameterTemplatesResponse>
```

**JSON格式**

```
{
"Engine": "mssql", 
"EngineVersion": "2008r2", 
"ParameterCount":1
  "Parameters": {
         "TemplateRecord": [
            {
              "ParameterDescription": "此选项设置服务器范围内的默认填充因子值。提供填充因子是为了优化索引数据存储和性能。", 
              "ForceRestart": "True", 
              "CheckingCode": "[0-100]"
              "Factor":"1"
              "ParameterName":"fill factor"
              "ParameterValue":"0"
              "ForceModify":"True"
              "Unit":"INT"
           }
          ]
       }, 
  "RequestId": "7B96585A-0FF2-4979-8FE5-7D147A29FDC0"
}
```

