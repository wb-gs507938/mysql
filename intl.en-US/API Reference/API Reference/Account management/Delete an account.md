# Delete an account {#reference_yqq_nyg_12b .reference}

## Description {#section_l21_v32_12b .section}

Directly delete database accounts. The instance status must be Running.

## Request parameters {#section_qzx_w32_12b .section}

|Name|Type|Required?|Description|
|----|----|---------|-----------|
|Action|String|Yes|Required parameter. Value: DeleteAccount.|
|DBInstanceId|String|Yes|Instance ID.|
|AccountName|String|Yes|Account name, which must be unique and meet the following requirements:-   Start with a letter;
-   Consist of lower-case letters, digits, and underscores \(\_\);
-   Contain no more than 16 characters.
-   For invalid characters, see [Forbidden keywords table](intl.en-US/API Reference/API Reference/Schedules/Forbidden keywords table.md#)

|

## Return parameters {#section_rpk_z32_12b .section}

|Name|Type|Description|
|----|----|-----------|
|Public Return Parameters|-|For more information, see [Public parameters](intl.en-US/API Reference/Use APIs/Public parameters.md#).|

## Request example {#section_l4g_pj2_12b .section}

```
https://rds.aliyuncs.com/?Action=DeleteAccount
&DBInstanceId=riaqu32iiaeiyeuya1370317952018
&AccountName=wangyichengtest
&<[Public Request Parameters]>
```

## Response example {#section_xtg_rj2_12b .section}

**XML format**

```
<DeleteAccountResponse>
         <RequestId>91E855E5-7E80-4955-929B-C74EE1D38C66</RequestId>
</DeleteAccountResponse>
```

**JSON format**

```
{
      "RequestID":"91E855E5-7E80-4955-929B-C74EE1D38C66"
  }
```

