# CreateAccount {#reference_fty_nxg_12b .reference}

## 描述 {#section_l21_v32_12b .section}

该接口用于为数据库创建账号，同一个用户实例下，一个账号可以对多个数据库，同一账号对不同数据库权限可以不同。

实例和数据库必须满足以下条件，否则将创建失败：

-   当前实例状态：运行中。

-   当前数据库状态：运行中。

-   当前实例没有被锁定。

-   没有超出单个实例内的最大账号数量。


## 请求参数 {#section_qzx_w32_12b .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是|系统规定参数，取值为CreateAccount。|
|DBInstanceId|String|是|实例名。|
|AccountName|String|是|操作账号，必须唯一：-   以字母开头；
-   由小写字母，数字、下划线组成；
-   长度不超过16个字符。
-   其他非法字符，见[禁用关键字表](cn.zh-CN/API参考/API参考/附表/禁用关键字表.md#)。

|
|AccountPassword|String|是|操作密码，由字母、数字或下划线组成，长度为6~32位。|
|AccountType|String|否|取值为：-   Normal：普通账号，默认为 Normal。
-   Super：超级账号
-   该参数仅对 MySQL5.5/5.6、SQL Server 2008 R2 有效。
-   MySQL 5.7、SQL Server 2012/2016、PostgreSQL 和 PPAS 有且仅有一个初始账号，其他账号由初始账号连接数据库后创建。

|
|AccountDescription|String|否|账号备注：-   不能以http://和https://开头；
-   以中文、英文字母开头；
-   可以包含中文、英文字符、“\_”、“-”和数字；
-   长度为2~256字符。

|

## 返回参数 {#section_rpk_z32_12b .section}

|参数|类型|说明|
|--|--|--|
|<公共返回参数\>|-|详见[公共参数](cn.zh-CN/API参考/使用API/公共参数.md#)。|

## 请求示例 {#section_l4g_pj2_12b .section}

```
https://rds.aliyuncs.com/?Action=CreateAccount
&AccountName=testacc02
&AccountPassword=pw1234
&DBInstanceId=riauvjz6zajfiq6ba1370329449201
&<[公共请求参数]>
```

## 返回示例 {#section_xtg_rj2_12b .section}

**XML格式**

```
<CreateAccountResponse>
         <RequestId>D4D4BE8A-DD46-440A-BFCD-EE31DA81C9DD</RequestId>
</CreateAccountResponse>
```

**JSON格式**

```
{
      "RequestId":"D4D4BE8A-DD46-440A-BFCD-EE31DA81C9DD"
  }
```

