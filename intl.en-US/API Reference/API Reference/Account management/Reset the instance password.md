# Reset the instance password {#reference_ydw_z1h_12b .reference}

## Description {#section_l21_v32_12b .section}

Reset the account password. The following conditions must be met, otherwise the operation will fail:

-   The instance status is Running.
-   The instance is not locked.

## Request parameters {#section_qzx_w32_12b .section}

|Name|Type|Required|Description|
|----|----|--------|-----------|
|Action|String|Yes|Required parameter. Value: ResetAccountPassword.|
|DBInstanceId|String|Yes|Instance ID.|
|AccountName|String|Yes|Name of an account.|
|AccountPassword|String|Yes|A new password. It may consist of letters, numbers, or underlines, with a length of 6 to 32 characters.|

## Return parameters {#section_rpk_z32_12b .section}

|Name|Type|Description|
|----|----|-----------|
|<Public Return Parameters\>| |For more information, see [Public parameters](intl.en-US/API Reference/Use APIs/Public parameters.md#).|

## Request example {#section_l4g_pj2_12b .section}

```
https://rds.aliyuncs.com/?Action=ResetAccountPassword
&AccountName=testacc02
&AccountPassword=newpw1234
&DBInstanceId=riauvjz6zajfiq6ba1370329449201
&<Public Request Parameters>
```

## Response example {#section_xtg_rj2_12b .section}

**XML format**

```
<ResetAccountPasswordResponse>
         <RequestId>D4D4BE8A-DD46-440A-BFCD-EE31DA81C9DD</RequestId>
</ResetAccountPasswordResponse>
```

**JSON format**

```
{
         "RequestId":"D4D4BE8A-DD46-440A-BFCD-EE31DA81C9DD"
}
```

