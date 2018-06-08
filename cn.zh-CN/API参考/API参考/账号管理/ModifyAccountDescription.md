# ModifyAccountDescription {#reference_z2r_n1h_12b .reference}

## 描述 {#section_l21_v32_12b .section}

该接口用于修改数据库名的备注名，用于方便用户记录该实例，比如为实例修改备注名为“阿里云测试环境实例账号A”。

## 请求参数 {#section_qzx_w32_12b .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是|系统规定参数，取值为ModifyAccountDescription。|
|DBInstanceId|String|是|实例名。|
|AccountName|String|是|操作账号，需惟一性检查：-   以字母开头；
-   由小写字母，数字、下划线组成；
-   长度不超过16个字符。
-   其他非法字符，详见[禁用关键字表](cn.zh-CN/API参考/API参考/附表/禁用关键字表.md#)。

|
|AccountDescription|String|是|修改账号备注：-   以中文、英文字母开头；
-   不能以http://或https://开头
-   可以包含中文、英文字符、“\_”、“ -”、数字；
-   长度为2~256个字符。

|

## 返回参数 {#section_rpk_z32_12b .section}

|名称|类型|描述|
|--|--|--|
|<公共返回参数\>| |详见[公共参数](cn.zh-CN/API参考/使用API/公共参数.md#)。|

## 请求示例 {#section_l4g_pj2_12b .section}

```
https://rds.aliyuncs.com/?Action=ModifyAccountDescription
&DBInstanceId=rdsaiiabnaiiabn
&AccountName=wangyichengtest
&AccountDescription=testAccoutdescribe
&<公共请求参数>
```

## 返回示例 {#section_xtg_rj2_12b .section}

**XML格式**

```
< ModifyAccountDescription>
         <RequestId>17F57FEE-EA4F-4337-8D2E-9C23CAA63D74</RequestId>
</ ModifyAccountDescription>
```

**JSON格式**

```
{
    "RequestId": " 17F57FEE-EA4F-4337-8D2E-9C23CAA63D74"
}
```

