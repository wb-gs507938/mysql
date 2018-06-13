# View the account list {#reference_uk5_yyg_12b .reference}

## Description {#section_l21_v32_12b .section}

Retrieve account list information for the specified instance and the specified database or the information of the specified account.

## Request parameters {#section_qzx_w32_12b .section}

|Name|Type|Required|Description|
|----|----|--------|-----------|
|Action|String|Yes|Required parameter. Value: DescribeAccounts.|
|DBInstanceId|String|Yes|Instance ID.|
|AccountName|String|No|Name of an account.|

## Return parameters {#section_rpk_z32_12b .section}

|Name|Type|Description|
|----|----|-----------|
|<Public Return Parameters\>| |For more information, see **[Public parameters](intl.en-US/API Reference/Use APIs/Public parameters.md#)**.|
|Accounts|List<DBInstanceAccount\>|Array composed of the accounts.|

## DBInstanceAccount parameters {#section_o4v_dzg_12b .section}

|Name|Type|Description|
|----|----|-----------|
|DBInstanceId|String|ID of the instance to which the account belongs.|
|AccountName|String|Name of the database operation account.|
|AccountStatus|String|Account status. Values:-   Unavailable
-   Available

|
|AccountDescription|String|Account remarks.|
|DatabasePrivileges|List<DatabasePrivilege\>|Array composed of DatabasePrivileges.|
|AccountType|String|Type of account.-   Normal: Common privilege.
-   Super: High privilege.

|

## DatabasePrivilege parameters {#section_vsw_lzg_12b .section}

|Name|Type|Description|
|----|----|-----------|
|DBName|String|Name of a database.|
|AccountPrivilege|String|Name of the database account.|

## Request example {#section_l4g_pj2_12b .section}

```
https://rds.aliyuncs.com/?Action=DescribeAccounts
&DBInstanceId=rdsubauieubauie
&<Public Request Parameters>
```

## Response example {#section_xtg_rj2_12b .section}

**XML format**

```
<DescribeAccountsResponse>
         <RequestId>2603CA96-B17D-4903-BC04-61A2C829CD94</RequestId>
           <Accounts>
               <DBInstanceAccount>
                  <AccountName>MySQL</AccountName>
                  <DBInstanceId>testdb</DBInstanceId>
                  <AccountStatus>utf8</AccountStatus>
                  <AccountDescription></AccountDescription>
                  <DatabasePrivileges>
      <DatabasePrivilege></DatabasePrivilege>
</DatabasePrivileges>
               <DBInstanceAccount>
           </Accounts>
</DescribeAccountsResponse>
```

**JSON format**

```
{
    "Accounts": {
      "DBInstanceAccount": [
        {
          "AccountDescription": "", 
          "DBInstanceId": "rdsubauieubauie", 
          "DatabasePrivileges": {
            "DatabasePrivilege": []
          }, 
          "AccountStatus": "Unavailable", 
          "AccountName": "testaccount"
        }
      ]
    }, 
    "RequestId": "8D9A9689-F108-43B4-9D2E-0A52FF42B008"
  }
```

