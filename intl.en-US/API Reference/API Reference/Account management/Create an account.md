# Create an account {#reference_fty_nxg_12b .reference}

## Description {#section_l21_v32_12b .section}

Create an account for a database. For instances of the same user, a single account can be used to operate multiple databases. A single account can have different permissions on different databases.

The following conditions must be met, otherwise account creation will fail:

-   The instance status is Running.

-   The current database status is Running.

-   The current instance is not locked.

-   The maximum number of accounts for a single instance is not exceeded.


## Request parameters {#section_qzx_w32_12b .section}

|Name|Type|Required?|Description|
|----|----|---------|-----------|
|Action|String|Yes|Required parameter. Value: CreateAccount.|
|DBInstanceId|String|Yes|Instance ID.|
|AccountName|String|Yes|Account name, which must be unique and meet the following requirements:-   Start with a letter;
-   Consist of lower-case letters, digits, and underscores \(\_\);
-   Contain no more than 16 characters.
-   For other invalid characters, see [Forbidden keywords table](intl.en-US/API Reference/API Reference/Schedules/Forbidden keywords table.md#).

|
|AccountPassword|String|Yes|Operation password. It may consist of letters, digits, or underlines, with a length of 6 to 32 characters.|
|AccountType|String|No|Privilege type of account.-   Normal: Common privilege.
-   Super: High privilege. And the default value is Normal.
-   This parameter is valid for MySQL 5.5/5.6 only.
-   MySQL 5.7, SQL Server 2012/2016, PostgreSQL, and PPAS each can have only one initial account. Other accounts are created by the initial account that has logged on to the database.

|
|AccountDescription|String|No|Account remarks.-   It cannot begin with http:// or https://.
-   It must start with a Chinese character or English letter.
-   It can include Chinese and English characters/letters, underscores \(\_\), hyphens \(-\), and digits.
-   The length may be 2-256 characters.

|

## Return parameters {#section_rpk_z32_12b .section}

|Name|Type|Description|
|----|----|-----------|
|<Public Return Parameters\>|-|For more information, see [Public parameters](intl.en-US/API Reference/Use APIs/Public parameters.md#).|

## Request example {#section_l4g_pj2_12b .section}

```
https://rds.aliyuncs.com/?Action=CreateAccount
&AccountName=testacc02
&AccountPassword=pw1234
&DBInstanceId=riauvjz6zajfiq6ba1370329449201
&<[Public Request Parameters]>
```

## Response example {#section_xtg_rj2_12b .section}

**XML format:**

```
<CreateAccountResponse>
         <RequestId>D4D4BE8A-DD46-440A-BFCD-EE31DA81C9DD</RequestId>
</CreateAccountResponse>
```

**JSON format:**

```
{
      "RequestId":"D4D4BE8A-DD46-440A-BFCD-EE31DA81C9DD"
  }
```

