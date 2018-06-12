# View the list of currently running instance database parameters {#reference_spx_b1m_12b .reference}

## Description {#section_l21_v32_12b .section}

This interface returns an instance’s current parameter configuration to the user.

## Request parameters {#section_qzx_w32_12b .section}

|Name|Type|Required|Description|
|----|----|--------|-----------|
|Action|String|Yes|Required parameter. Value: DescribeParameters.|
|DBInstanceId|String|Yes|Instance ID.|

## Return parameters {#section_a5x_zlh_12b .section}

|Name|Type|Description|
|----|----|-----------|
|<Public Return Parameters\>|None|For details, see [Public parameters](intl.en-US/API Reference/Use APIs/Public parameters.md#).|
|Engine|String|Database type.|
|EngineVersion|String|Database version.|
|RunningParameters| ```
List<DBInstanceParameter>
```

 |A list of currently running parameters, in the format of \{parameter1,parameter2,parameter3, …\}.|
|ConfigParameters| ```
List<DBInstanceParameter>
```

 |A list of parameters being synchronized, in the format of \{parameter1,parameter2,parameter3,…\}.|

## DBInstance parameters {#section_hfv_f1m_12b .section}

|Name|Type|Description|
|----|----|-----------|
|ParameterName|String|Parameter name.|
|ParameterValue|String|Parameter value.|
|ParameterDescription|String|Parameter description.|

## Request example {#section_l4g_pj2_12b .section}

```
https://rds.aliyuncs.com/?Action=DescribeParameters
&DBInstanceId=riauvjz6zajfiq6ba1370329449201
&<Public Request Parameters>
```

## Response example {#section_xtg_rj2_12b .section}

**XML format:**

```
< DescribeParametersResponse> 
  <RequestId>2A748162-8040-4D6B-813E-6910C8C033F1</RequestId>
  <Engine>mssql</ Engine >
  <EngineVersion>2008r2</ EngineVersion >
  <RunningParameters>
    <DBInstanceParameter>
    <ParameterDescription> This option sets the default fill factor value for the server range. A fill factor is provided to optimize index data storage and performance </ParameterDescription>
    <ParameterName>fill factor</ParameterName>
    <ParameterValue>0</ParameterValue>
    </DBInstanceParameter>
  </RunningParameters>
  <ConfigParameters>
    <DBInstanceParameter>
    <ParameterDescription> This option sets the default fill factor value for the server range. A fill factor is provided to optimize index data storage and performance </ParameterDescription>
    <ParameterName>fill factor</ParameterName>
    <ParameterValue>50</ParameterValue>
  </DBInstanceParameter>
  </ConfigParameters>
</DescribeParametersResponse>
```

**JSON format:**

```
{
  "ConfigParameters": {
      "DBInstanceParameter": [
          {
               "ParameterDescription": "This option sets the default fill factor value for the server range. A fill factor is provided to optimize index data storage and performance.", 
              "ParameterName": "fill factor", 
              "ParameterValue": "50"
          }
      ]
  }, 
  "Engine": "mssql", 
  "EngineVersion": "2008r2", 
  "RunningParameters": {
      "DBInstanceParameter": [
          {
               "ParameterDescription": "This option sets the default fill factor value for the server range. A fill factor is provided to optimize index data storage and performance.",  
              "ParameterName": "fill factor", 
              "ParameterValue": "0"
          }
      ]
  }, 
  "RequestId": "2A748162-8040-4D6B-813E-6910C8C033F1"
}
```

