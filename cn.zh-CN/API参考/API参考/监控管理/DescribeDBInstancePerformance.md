# DescribeDBInstancePerformance {#reference_q1h_wxl_12b .reference}

## 描述 {#section_l21_v32_12b .section}

根据性能参数查看某个用户实例，某时间段范围内的性能监控数据。根据查询时间范围的不同，有如下3种输出形式：

-   当查询时间范围小于等于1天，按分钟描点性能值。

    **说明：** 实例空间占用Key为MySQL\_SpaceUsage或SQLServer\_SpaceUsage，仅支持查询1天内的监控数据。

-   当查询时间范围1天到7天不支持，暂不支持。

-   当查询时间范围大于7天小于等于15天，按小时描点性能值。

-   当查询时间范围大于15天小于30天，暂不支持。

-   当查询时间范围大于等于30天小于等于1年按天描点。


## 请求参数 {#section_qzx_w32_12b .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是|系统规定参数，取值：DescribeDBInstancePerformance。|
|DBInstanceId|String|是|实例名。|
|Key|String|是|性能指标，多个用英文半角“,”分隔，见性能参数表。|
|StartTime|String|是|查询开始时间，格式如：2012-06-11T15:00Z。|
|EndTime|String|是|查询结束时间，格式如：2012-06-11T15:00Z。|

## 返回参数 {#section_a5x_zlh_12b .section}

|名称|类型|描述|
|--|--|--|
|<公共返回参数\>|无|详见[公共参数](intl.zh-CN/API参考/使用API/公共参数.md#)。|
|DBInstanceId|String|实例名。|
|Engine|String|数据库类型。|
|StartTime|String|查询开始时间，格式：YYYY-MM-DD’T’HH:mmZ，如2011-05-30T03:29Z。|
|EndTime|String|查询结束时间，格式：YYYY-MM-DD’T’HH:mmZ，如2011-05-30T03:29Z，大于查询开始时间。|
|PerformanceKeys| ```
List<PerformanceKey>
```

 |数组格式：\{perf1, perf2, perf3, …\}。|

## PerformanceKey参数 {#section_r1t_gyl_12b .section}

|名称|类型|描述|
|--|--|--|
|Key|String|性能参数。|
|Unit|String|展示单位。|
|ValueFormat|String|值格式1、如果是null，则是VALUE是一个最终值2、如果不是null，则需要解析VALUE，以“&”分隔，如：com\_delete&com\_insert&com\_insert\_select&com\_replace。|
|Values| ```
List<PerformanceValue>
```

 |数组格式：\{value1, value2, …\}。|

## PerformanceValue参数 {#section_n2c_3yl_12b .section}

|名称|类型|描述|
|--|--|--|
|Value|String|性能值。|
|Date|String|计算日期，格式：”yyyy-MM-dd’T’HH:mm:ssZ”，如2011-05-30T03:29:00Z。|

## 请求示例 {#section_l4g_pj2_12b .section}

```
https://rds.aliyuncs.com/?Action=DescribeDBInstancePerformance
&DBInstanceId=riauvjz6zajfiq6ba1370329449201
&key= MySQL_NetworkTraffic
&StartTime=2013-01-11T15:00:00Z
&EndTime=2013-06-05T15:00:00Z
&<公共请求参数>
```

## 返回示例 {#section_xtg_rj2_12b .section}

**XML格式**

```
<DescribeDBInstancePerformanceResponse> 
  <RequestId>A5409D02-D661-4BF3-8F3D-0A814D0574E7</RequestId>
  <DBInstanceID>riauvjz6zajfiq6ba1370329449201</DBInstanceID> 
  <StartTime>2013-01-11T15:00:00Z</StartTime> 
  <EndTime>2013-10-17T15:00Z</EndTime> 
  <Engine>MySQL</Engine> 
   <PerformanceKeys> 
   <PerformanceKey>
       <Key>MySQL_NetworkTraffic</Key> 
       <Unit>KB</Unit> 
       <ValueFormat>recv_k&amp;sent_k</ValueFormat> 
       <Values><Values/> 
   </PerformanceKey>
   </PerformanceKeys> 
</DescribeDBInstancePerformanceResponse>
```

**JSON格式**

```
{
  “RequestId”A5409D02-D661-4BF3-8F3D-0A814D0574E7,
  "DBInstanceID": riauvjz6zajfiq6ba1370329449201,
  "StartTime": "2012-06-11T15:00Z",
  "EndTime": "2013-10-17T15:00Z",
  "Engine": "MySQL",
  "PerformanceKeys": {
      PerformanceKey[
          {
              "Key": "MySQL_NetworkTraffic",
              "Unit": "KB",
              "ValueFormat": "recv_k&sent_k",
              "Values": {
                  "PerformanceValue":[]
              }
          }
      ]
  }
}
```

