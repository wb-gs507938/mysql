# Modify the database parameter list {#reference_b55_k1m_12b .reference}

## Description {#section_l21_v32_12b .section}

You can modify instance parameters. After submitting a request, the RDS assigns a task and the new parameter is applied to the instance. If any submitted parameter requires that the database be restarted, the RDS restarts the database. Instances must meet the following conditions, or the call may fail:

-   The current instance status is Running.

-   The current instance lock mode is Normal.


There are three types of parameter values:

-   \[1-65535\]: indicates a numerical range. Regular identification is used to extract the minimum and maximum values. Then the input parameter is verified based on the minimum and maximum values. In addition, the parameter must be a multiple of a divisible factor.

-   \[utf8|gbk|latin1\]: indicates a set value determination rule. Regular identification is used to extract the fixed value. Then the parameter is verified based on these fixed values.

-   Others: a regular expression must apply.


Before the task is assigned, the RDS checks the parameter as follows:

-   Whether the parameter exist.

-   Whether the parameter can be modified.

-   Whether the parameter is valid.


If the parameter is invalid, the RDS returns Error Code 400 and the information about the invalid parameter. For example:

```
{"HttpStatusCode":400,"Code":"InvalidParameter.Format",
"Message":"Specified parameter is not valid.[auto_increment_increment:a,character_set_client:41]"}
```

## Request parameters {#section_qzx_w32_12b .section}

|Name|Type|Required?|Description|
|----|----|---------|-----------|
|Action|String|Yes|required parameter. Value:```
ModifyParameter
```

.|
|DBInstanceId|String|Yes|Instance ID.|
|Parameters|String|Yes|JSON string for the parameter and its value. The parameter value must be string-type. \{“auto\_increment\_increment”:”1”, “character\_set\_client”:”utf8”\}.|
|Forcerestart|String|No|true: force restart \(true must be input when a parameter among parameters to be modified needs to be restarted; otherwise, the modification is invalid\). False: force restart disabled. The force restart is disabled by default.|

## Return parameters {#section_a5x_zlh_12b .section}

|Name|Type|Description|
|----|----|-----------|
|<Public Return Parameters\>| |For more information, see [Public parameters](intl.en-US/API Reference/Use APIs/Public parameters.md#).|

## Request example {#section_l4g_pj2_12b .section}

```
https://rds.aliyuncs.com/?Action=ModifyeParameter
&DBInstanceId=riauvjz6zajfiq6ba1370329449201L
&Parameters={"auto_increment":"1","character_set_client":"gbk"}
&<Public Request Parameters>
```

## Response example {#section_xtg_rj2_12b .section}

**XML format:**

```
<ModifyeParameterResponse>
       <RequestId>542BB8D6-4268-45CC-A557-B03EFD7AB30A</RequestId>
</ModifyeParameterResponse>
```

**JSON format:**

```
{
       "RequestId":"542BB8D6-4268-45CC-A557-B03EFD7AB30A",
}
```

