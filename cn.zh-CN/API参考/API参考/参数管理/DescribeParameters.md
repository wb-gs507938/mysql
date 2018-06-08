# DescribeParameters {#reference_spx_b1m_12b .reference}

## 描述 {#section_l21_v32_12b .section}

该接口返回用户某个实例当前的参数配置。

## 请求参数 {#section_qzx_w32_12b .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是|系统规定参数，取值：DescribeParameters。|
|DBInstanceId|String|是|实例名。|

## 返回参数 {#section_a5x_zlh_12b .section}

|名称|类型|描述|
|--|--|--|
|<公共返回参数\>|无|详见[公共参数](cn.zh-CN/API参考/使用API/公共参数.md#)。|
|Engine|String|数据库类型。|
|EngineVersion|String|数据库版本号。|
|RunningParameters| ```
List<DBInstanceParameter>
```

 |当前运行的参数列表，格式为\{parameter1,parameter2,parameter3, …\}。|
|ConfigParameters| ```
List<DBInstanceParameter>
```

 |正在同步的参数列表，格式为\{parameter1,parameter2,parameter3,…\}。|

## DBInstanceParameter参数 {#section_hfv_f1m_12b .section}

|名称|类型|描述|
|--|--|--|
|ParameterName|String|参数名。|
|ParameterValue|String|参数值。|
|ParameterDescription|String|参数描述。|

## 请求示例 {#section_l4g_pj2_12b .section}

```
https://rds.aliyuncs.com/?Action=DescribeParameters
&DBInstanceId=riauvjz6zajfiq6ba1370329449201
&<公共请求参数>
```

## 返回示例 {#section_xtg_rj2_12b .section}

**XML格式**

```
< DescribeParametersResponse> 
  <RequestId>2A748162-8040-4D6B-813E-6910C8C033F1</RequestId>
  <Engine>mssql</ Engine >
  <EngineVersion>2008r2</ EngineVersion >
  <RunningParameters>
    <DBInstanceParameter>
    <ParameterDescription>此选项设置服务器范围内的默认填充因子值。提供填充因子是为了优化索引数据存储和性能</ParameterDescription>
    <ParameterName>fill factor</ParameterName>
    <ParameterValue>0</ParameterValue>
    </DBInstanceParameter>
  </RunningParameters>
  <ConfigParameters>
    <DBInstanceParameter>
    <ParameterDescription>此选项设置服务器范围内的默认填充因子值。提供填充因子是为了优化索引数据存储和性能</ParameterDescription>
    <ParameterName>fill factor</ParameterName>
    <ParameterValue>50</ParameterValue>
  </DBInstanceParameter>
  </ConfigParameters>
</DescribeParametersResponse>
```

**JSON格式**

```
{
  "ConfigParameters": {
      "DBInstanceParameter": [
          {
              "ParameterDescription": "此选项设置服务器范围内的默认填充因子值。提供填充因子是为了优化索引数据存储和性能。", 
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
              "ParameterDescription": "此选项设置服务器范围内的默认填充因子值。提供填充因子是为了优化索引数据存储和性能。", 
              "ParameterName": "fill factor", 
              "ParameterValue": "0"
          }
      ]
  }, 
  "RequestId": "2A748162-8040-4D6B-813E-6910C8C033F1"
}
```

