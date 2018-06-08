# DescribeDatabases {#reference_p2q_52g_12b .reference}

## 描述 {#section_l21_v32_12b .section}

该接口用于查找指定实例、指定DB的DB列表信息。如果查找参数类型错误，将返回错误提示，返回数据为空。

**说明：** 接口不支持PostgreSQL和PPAS。

## 请求参数 {#section_qzx_w32_12b .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是|系统规定参数，取值为DescribeDatabases。|
|DBInstanceId|String|是|实例名。|
|DBName|String|否|数据库名称。|
|DBStatus|String|否|数据库状态，取值范围：-   Creating：创建中
-   Running：使用中
-   Deleting：删除中

|

## 返回参数 {#section_rpk_z32_12b .section}

|名称|类型|描述|
|--|--|--|
|<公共返回参数\>| |详见[公共参数](cn.zh-CN/API参考/使用API/公共参数.md#)。|
|Databases|List<Database\>|由Database组成的数据。|

## DATABASE参数 {#section_vdm_ffg_12b .section}

|名称|类型|描述|
|--|--|--|
|DBName|String|数据库名称。|
|DBInstanceId|String|数据库所属实例名称。|
|Engine|String|数据库实例类型。|
|DBStatus|String|数据库状态，取值范围：-   Creating：创建中
-   Running：使用中
-   Deleting：删除中

|
|CharacterSetName|String|字符集。|
|DBDescription|String|数据库描述。|
|Accounts|List<AccountPrivilegeInfo\>|由Acounts组成的list。|
|Account|String|账号名称。|
|AccountPrivilege|String|账号对该DB具有的权限。|

## AccountPrivilegeInfo参数 {#section_d33_jfg_12b .section}

|名称|类型|描述|
|--|--|--|
|Account|String|账号名称。|
|AccountPrivilege|String|账号对该DB具有的权限。|

## 请求示例 {#section_l4g_pj2_12b .section}

```
https://rds.aliyuncs.com/?Action=DescribeDatabases
&DBInstanceId=rds3meynazqbzju
&<公共请求参数>
```

## 返回示例 {#section_xtg_rj2_12b .section}

**XML格式**

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

**JSON格式**

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

