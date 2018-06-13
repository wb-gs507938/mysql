# Grant account permissions {#reference_x1w_rzg_12b .reference}

## Description {#section_l21_v32_12b .section}

Grant database access permissions to accounts. A single account can be associated with one or more databases. If the specified account already has the access permission on the specified database, the operation directly returns a successful result.

**Note:** Instance status must be Running.

## Request parameters {#section_qzx_w32_12b .section}

|Name|Type|Required?|Description|
|----|----|---------|-----------|
|Action|String|Yes|Required parameter. Value: GrantAccountPrivilege.|
|DBInstanceId|String|Yes|Instance ID.|
|AccountName|String|Yes|Name of an account.|
|DBName|String|Yes|Name of the database associated with this account.|
|AccountPrivilege|String|Yes|Account permission. Values:-   ReadOnly
-   ReadWrite

|

## Return parameters {#section_rpk_z32_12b .section}

|Name|Type|Description|
|----|----|-----------|
|<Public Return Parameters\>| |For more information, see [Public parameters](intl.en-US/API Reference/Use APIs/Public parameters.md#).|

## Request example {#section_l4g_pj2_12b .section}

```
https://rds.aliyuncs.com/?Action=GrantAccountPrivilege
&AccountName=testacc02
&AccountPrivilege=ReadWrite
&DBName=testdb03
&DBInstanceId=riauvjz6zajfiq6ba1370329449201
&<Public Request Parameters>
```

## Response example {#section_xtg_rj2_12b .section}

**XML format**

```
<GrantAccountPrivilegeResponse>
         <RequestId>81BC9559-7B22-4B7F-B705-5F56DEECDEA7</RequestId>
</GrantAccountPrivilegeResponse>
```

**JSON format**

```
{
         "RequestId":"81BC9559-7B22-4B7F-B705-5F56DEECDEA7"
}
```

