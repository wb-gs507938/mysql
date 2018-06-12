# View database parameter templates {#reference_szs_nzl_12b .reference}

## Description {#section_l21_v32_12b .section}

The interface returns a list of parameter templates. The list includes parameter names, default parameter values, whether or not they can be modified, whether the database must be restarted for them to take effect, and the parameter validation rules \(regular expressions\).

**Note:** This API is only applicable to MySQL and SQL Server instances.

## Request parameters {#section_qzx_w32_12b .section}

|Name|Type|Required|Description|
|----|----|--------|-----------|
|Action|String|Yes|Required parameter. Value: DescribeParameterTemplates.|
|Engine|String|Yes|Database type, values: MySQL and SQLServer.|
|EngineVersion|String|Yes|Database version. For MySQL databases: 5.1, 5.5, or 5.6. For SQL Server databases: 2008r2, 2012\_web, 2016\_web.|

## Return parameters {#section_a5x_zlh_12b .section}

|Name|Type|Description|
|----|----|-----------|
|<Public Return Parameters\>| |For more information, see [Public parameters](intl.en-US/API Reference/Use APIs/Public parameters.md#).|
|Engine|String|Database type.|
|EngineVersion|String|Database version.|
|ParameterCount|Integer|Number of parameters.|
|Parameters| ```
List<TemplateRecord>
```

 |Parameter list. Format: \{parameter1, parameter2, parameter3, …\}.|

## TemplateRecord parameters {#section_r33_vzl_12b .section}

|Name|Type|Description|
|----|----|-----------|
|ParameterName|String|Parameter name.|
|ParameterValue|String|Default parameter value.|
|ForceModify|String|False: Default parameter values cannot be modified. True: Default parameter values can be modified.|
|ForceRestart|String| -   False: The modification takes effect immediately.
-   True: The modification takes effect after the database is restarted.

 |
|CheckingCode|String|Check code. The available range for a parameter and a regular expression.|
|ParameterDescription|String|Parameter description.|

## Request example {#section_l4g_pj2_12b .section}

```
https://rds.aliyuncs.com/?Action=DescribeParameterTemplates
&Engine=SQLServer
&EngineVersion=2008r2
&<Public Request Parameters>
```

## Response example {#section_xtg_rj2_12b .section}

**XML format**

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
    <ParameterDescription> This option sets the default fill factor value for the server range. A fill factor is provided to optimize index data storage and performance. </ParameterDescription>
    <ParameterName>fill factor</ParameterName>
    <ParameterValue>0</ParameterValue>
    <ForceModify>True</ForceModify>
    <Unit>INT</Unit>
    </TemplateRecord>
  </Parameters>
  <RequestId>7B96585A-0FF2-4979-8FE5-7D147A29FDC0</RequestId>
</DescribeParameterTemplatesResponse>
```

**JSON format**

```
{
"Engine": "mssql", 
"EngineVersion": "2008r2", 
"ParameterCount":1
  "Parameters": {
         "TemplateRecord": [
            {
              "ParameterDescription": "This option sets the default fill factor value for the server range. A fill factor is provided to optimize index data storage and performance.", 
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

