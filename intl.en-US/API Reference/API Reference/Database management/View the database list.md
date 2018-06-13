# View the database list {#reference_p2q_52g_12b .reference}

## Description {#section_l21_v32_12b .section}

Retrieve the database list information for the specified instances and databases. If the search parameter type is incorrect, an error prompt is returned and the returned data is blank.

**Note:** This interface does not support PostgreSQL or PPAS.

## Request parameters {#section_qzx_w32_12b .section}

|Name|Type|Required?|Description|
|----|----|---------|-----------|
|Action|String|Yes|Required parameter. Value: DescribeDatabases.|
|DBInstanceId|String|Yes|Instance ID.|
|DBName|String|No|Name of a database.|
|DBStatus|String|No|Status of a database. Values:-   Creating
-   Running
-   Deleting

|

## Return parameters {#section_rpk_z32_12b .section}

|Name|Type|Description|
|----|----|-----------|
|<Public return parameter\>| |For more information, see [Public parameters](intl.en-US/API Reference/Use APIs/Public parameters.md#).|
|Databases|List<Database\>|Data composed of the databases.|

## DATABASE parameters {#section_vdm_ffg_12b .section}

|Name|Type|Description|
|----|----|-----------|
|DBName|String|Name of a database.|
|DBInstanceId|String|ID of the instance to which the database belongs.|
|Engine|String|Database instance type.|
|DBStatus|String|Status of a database. Values:-   Creating
-   Running
-   Deleting

|
|CharacterSetName|String|Character set.|
|DBDescription|String|Database description.|
|Accounts|List<AccountPrivilegeInfo\>|List composed of the accounts.|
|Account|String|Name of an account.|
|AccountPrivilege|String|Permissions of the account on the database.|

## AccountPrivilegeInfo parameters {#section_d33_jfg_12b .section}

|Name|Type|Description|
|----|----|-----------|
|Account|String|Name of an account.|
|AccountPrivilege|String|Permissions of the account on the database.|

## Request example {#section_l4g_pj2_12b .section}

```
https://rds.aliyuncs.com/?Action=DescribeDatabases
&DBInstanceId=rds3meynazqbzju
&<Public Request Parameters>
```

## Response example {#section_xtg_rj2_12b .section}

**XML format:**

```
< DescribeDatabasesResponse>
         <RequestId>2603CA96-B17D-4903-BC04-61A2C829CD94</RequestId>
           <Databases>
               <Database>
                  <Engine>MySQL</Engine>
                  <DBName>testdb</DBName>
                  <CharacterSetName>utf8</CharacterSetName>
                  <DBStatus>Creating</DBStatus>
                  <DBInstanceId>rds3meynazqbzju</DBInstanceId>
                  <Accounts>
                         <AccountPrivilegeInfo></AccountPrivilegeInfo>
                  <Accounts>  
               </Database>
               <Database>
                  <Engine>MySQL</Engine>
                  <DBName>testdb2</DBName>
                  <CharacterSetName>gbk</CharacterSetName>
                  <DBStatus>Creating</DBStatus>
                  <DBInstanceId>rds3meynazqbzju</DBInstanceId>
                  <Accounts>
                         <AccountPrivilegeInfo></AccountPrivilegeInfo>
                  <Accounts>  
               </Database>
          </Databases>
</ DescribeDatabasesResponse>
```

**JSON format:**

```
 {
    "RequestId": "2603CA96-B17D-4903-BC04-61A2C829CD94", 
    "Databases": {
      "Database": [
        {
          "Engine": "MySQL", 
          "CharacterSetName": "utf8", 
          "DBStatus": "Creating", 
          "DBDescription": "", 
          "DBInstanceId": "rds3meynazqbzju", 
          "Accounts": {
            " AccountPrivilegeInfo": []
          }, 
          "DBName": "testdb"
        }, 
        {
          "Engine": "MySQL", 
          "CharacterSetName": "gbk", 
          "DBStatus": "Creating", 
          "DBDescription": "", 
          "DBInstanceId": "rds3meynazqbzju", 
          "Accounts": {
            " AccountPrivilegeInfo": []
          }, 
          "DBName": "testdb2"
        }
      ]
    }
  }
```

