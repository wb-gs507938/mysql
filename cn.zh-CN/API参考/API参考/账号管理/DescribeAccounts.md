# DescribeAccounts {#reference_uk5_yyg_12b .reference}

## 描述 {#section_l21_v32_12b .section}

该接口用于查找指定实例、指定DB的帐户列表信息或某个指定账号的信息。

## 请求参数 {#section_qzx_w32_12b .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是|系统规定参数，取值为DescribeAccounts。|
|DBInstanceId|String|是|实例名。|
|AccountName|String|否|账号名。|

## 返回参数 {#section_rpk_z32_12b .section}

|名称|类型|描述|
|--|--|--|
|<公共返回参数\>| |详见**[公共参数](cn.zh-CN/API参考/使用API/公共参数.md#)**。|
|Accounts|List<DBInstanceAccount\>|由Account组成的数组。|

## DBInstanceAccount参数 {#section_o4v_dzg_12b .section}

|名称|类型|描述|
|--|--|--|
|DBInstanceId|String|账号所属实例名称。|
|AccountName|String|DB操作账号名称。|
|AccountStatus|String|账号状态：-   Unavailable：不可用
-   Available：可用

|
|AccountDescription|String|账号备注信息。|
|DatabasePrivileges|List<DatabasePrivilege\>|由DatabasePrivilege组成的数组。|
|AccountType|String|取值为：-   Normal：普通账号，默认为 Normal。
-   Super：超级账号

|

## DatabasePrivilege参数 {#section_vsw_lzg_12b .section}

|名称|类型|描述|
|--|--|--|
|DBName|String|数据库名称。|
|AccountPrivilege|String|DB操作账号名称。|

## 请求示例 {#section_l4g_pj2_12b .section}

```
https://rds.aliyuncs.com/?Action=DescribeAccounts
&DBInstanceId=rdsubauieubauie
&<公共请求参数>
```

## 返回示例 {#section_xtg_rj2_12b .section}

**XML格式**

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

**JSON格式**

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

