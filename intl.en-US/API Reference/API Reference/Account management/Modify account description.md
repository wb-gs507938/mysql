# Modify account description {#reference_z2r_n1h_12b .reference}

## Description {#section_l21_v32_12b .section}

Modify an instance remark name to allow you to easily record the instance. For example, you can modify the remark name to Alibaba Cloud Testing Environment Instance Account A.

## Request parameters {#section_qzx_w32_12b .section}

|Name|Type|Required|Description|
|----|----|--------|-----------|
|Action|String|Yes|Required parameter. Value: ModifyAccountDescription.|
|DBInstanceId|String|Yes|Instance ID.|
|AccountName|String|Yes|Account name, which must be unique and meet the following requirements:-   Start with a letter;
-   Consist of lower-case letters, digits, and underscores \(\_\);
-   Contain no more than 16 characters. 
-    For other invalid characters, see [Forbidden keywords table](intl.en-US/API Reference/API Reference/Schedules/Forbidden keywords table.md#).

|
|AccountDescription|String|Yes|Modified content of the account remarks. -   It must start with a Chinese character or English letter.
-    It cannot begin with http:// or https://.
-    It can include Chinese and English characters/letters, underlines \(\_\), hyphens \(-\), and numbers.
-   The length is 2-256 characters.

|

## Return parameters {#section_rpk_z32_12b .section}

|Name|Type|Description|
|----|----|-----------|
|<Public Return Parameters\>| |For more information, see [Public parameters](intl.en-US/API Reference/Use APIs/Public parameters.md#).|

## Request example {#section_l4g_pj2_12b .section}

```
https://rds.aliyuncs.com/?Action=ModifyAccountDescription
&DBInstanceId=rdsaiiabnaiiabn
&AccountName=wangyichengtest
&AccountDescription=testAccoutdescribe
&<Public Request Parameters>
```

## Return example {#section_xtg_rj2_12b .section}

**XML format**

```
< ModifyAccountDescription>
         <RequestId>17F57FEE-EA4F-4337-8D2E-9C23CAA63D74</RequestId>
</ ModifyAccountDescription>
```

**JSON format**

```
{
    "RequestId": " 17F57FEE-EA4F-4337-8D2E-9C23CAA63D74"
}
```

