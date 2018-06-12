# View instance performance data {#reference_q1h_wxl_12b .reference}

## Description {#section_l21_v32_12b .section}

View the performance metric data for a user instance in a certain time period based on performance parameters. There are three output formats based on different query time ranges:

-   When the query time range is less than or equal to 1 day, performance values are shown by minute.

    **Note:** When the instance’s space usage key is MySQL\_SpaceUsage or SQLServer\_SpaceUsage, performance metric data can be queried only if the time range is up to 1 day.

-   Queries with time ranges from 1 to 7 days are not supported at the moment.

-   When the query time range is greater than 7 days and less than or equal to 15 days, performance values are shown by hour.

-   Queries with time ranges greater than 15 days and less than 30 days are not supported at the moment.

-   When the query time range is greater than or equal to 30 days and less than or equal to 1 year, performance values are shown by day.


## Request parameters {#section_qzx_w32_12b .section}

|Name|Type|Required?|Description|
|----|----|---------|-----------|
|Action|String|Yes|Required parameter. Value: DescribeDBInstancePerformance.|
|DBInstanceId|String|Yes|Instance ID.|
|Key|Integer|Yes|Performance indicator. Multiple indicators are separated with the English “,”. See the performance parameters table.|
|StartTime|String|Yes|Query start time, for example, 2012-06-11T15:00Z.|
|EndTime|String|Yes|Query end time, for example, 2012-06-11T15:00Z.|

## Return parameters {#section_a5x_zlh_12b .section}

|Name|Type|Description|
|----|----|-----------|
|<Public Return Parameters\>|None|For more information, see Public parameters.|
|DBInstanceId|String|Instance ID.|
|Engine|String|Database type.|
|StartTime|String|Query start time. Format: YYYY-MM-DD’T’HH:mmZ, for example, 2011-05-30T03:29Z.|
|EndTime|String|Query end time, which must be later than the query start time. Format: YYYY-MM-DD’T’HH:mmZ, for example, 2011-05-30T03:29Z.|
|PerformanceKeys| ```
List<PerformanceKey>
```

 |Format of the array: \{perf1, perf2, perf3, …\}.|

## PerformanceKey parameters {#section_r1t_gyl_12b .section}

|Name|Type|Description|
|----|----|-----------|
|Key|String|Performance parameter.|
|Unit|String|Display unit.|
|ValueFormat|String|Value format. 1. If it is null, VALUE is a final value. 2. If it is not null, VALUE needs to be resolved and separated with “&”, for example, com\_delete&com\_insert&com\_insert\_select&com\_replace|
|Values| ```
List<PerformanceValue>
```

 |Format of the array: \{value1, value2, …\}|

## PerformanceValue parameters {#section_n2c_3yl_12b .section}

|Name|Type|Description|
|----|----|-----------|
|Value|String|Performance value|
|Date|String|Calculation date. Format: “yyyy-MM-dd’T’HH:mm:ssZ”, for example, 2011-05-30T03:29:00Z|

## Request example {#section_l4g_pj2_12b .section}

```
https://rds.aliyuncs.com/?Action=DescribeDBInstancePerformance
&DBInstanceId=riauvjz6zajfiq6ba1370329449201
&key= MySQL_NetworkTraffic
&StartTime=2013-01-11T15:00:00Z
&EndTime=2013-06-05T15:00:00Z
&<Public Request Parameters>
```

## Return example {#section_xtg_rj2_12b .section}

**XML format:**

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

**JSON format:**

```

  “RequestId”A5409D02-D661-4BF3-8F3D-0A814D0574E7,
  "DBInstanceID": riauvjz6zajfiq6ba1370329449201,
  "StartTime": "2012-06-11T15:00Z",
  "EndTime": "2013-10-17T15:00Z",
  "Engine": "MySQL",
  "PerformanceKeys": {
      PerformanceKey[
          
              "Key": "MySQL_NetworkTraffic",
              "Unit": "KB",
              "ValueFormat": "recv_k&sent_k",
              "Values": {
                  "PerformanceValue":[]
              }
          
      
  

```

