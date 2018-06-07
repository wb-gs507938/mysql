# DeleteAccount {#reference_yqq_nyg_12b .reference}

## 描述 {#section_l21_v32_12b .section}

该接口用于删除数据库账号，实例状态要求为运行中。

## 请求参数 {#section_qzx_w32_12b .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是|系统规定参数，取值为DeleteAccount。|
|DBInstanceId|String|是|实例名。|
|AccountName|String|是|操作账号，需惟一性检查：-   以字母开头；
-   由小写字母，数字、下划线组成；
-   长度不超过16个字符。
-   其他非法字符，详见[禁用关键字表](cn.zh-CN/API参考/API参考/附表/禁用关键字表.md#)

|

## 返回参数 {#section_rpk_z32_12b .section}

|参数|类型|说明|
|--|--|--|
|<公共返回参数\>|-|详见[公共参数](cn.zh-CN/API参考/使用API/公共参数.md#)。|

## 请求示例 {#section_l4g_pj2_12b .section}

```
https://rds.aliyuncs.com/?Action=DeleteAccount
&DBInstanceId=riaqu32iiaeiyeuya1370317952018
&AccountName=wangyichengtest
&<[公共请求参数]>
```

## 返回示例 {#section_xtg_rj2_12b .section}

**XML格式**

```
<DeleteAccountResponse>
         <RequestId>91E855E5-7E80-4955-929B-C74EE1D38C66</RequestId>
</DeleteAccountResponse>
```

**JSON格式**

```
{
      "RequestID":"91E855E5-7E80-4955-929B-C74EE1D38C66"
  }
```

