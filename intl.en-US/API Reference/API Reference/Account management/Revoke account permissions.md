# Revoke account permissions {#reference_ssc_g1h_12b .reference}

## Description {#section_l21_v32_12b .section}

Delete an account’s access permission on a database.  The following conditions must be met, otherwise deletion will fail:

-   The current database instance status is Running.
-   The current database status is Running.

## Request parameters {#section_qzx_w32_12b .section}

|Name|Type|Required|Description|
|----|----|--------|-----------|
|Action|String|Yes|Required parameter. Value: RevokeAccountPrivilege.|
|DBInstanceId|String|Yes|Instance ID.|
|AccountName|String|Yes|Name of an account.|
|DBName|String|Yes|Name of a database.|

## Return parameters {#section_rpk_z32_12b .section}

|Name|Type|Description|
|----|----|-----------|
|<Public Return Parameters\>| |For more information, see [Public parameters](intl.en-US/API Reference/Use APIs/Public parameters.md#).|

## Request example {#section_l4g_pj2_12b .section}

```
https://rds.aliyuncs.com/?Action=RevokeAccountPrivilege
&AccountName=testacc02
&DBName=testdb03
&DBInstanceId=riauvjz6zajfiq6ba1370329449201
&<Public Request Parameters>
```

## Return example {#section_xtg_rj2_12b .section}

**XML format**

```
<RevokeAccountPrivilegeResponse>
         <RequestId>E22099CA-A61E-4992-A0B7-CE82DC175626</RequestId>
</RevokeAccountPrivilegeResponse>
```

**JSON format**

```
{
         "RequestId":"E22099CA-A61E-4992-A0B7-CE82DC175626"
}
```

