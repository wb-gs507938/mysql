# ModifyParameter {#reference_b55_k1m_12b .reference}

## 描述 {#section_l21_v32_12b .section}

用户可以修改实例参数，提交请求后，RDS将下达任务，新修改的参数应用到实例。如果所提交的参数中，有需要重启数据库的，RDS将重启数据库。必须满足以下条件，否则调用失败：

-   当前实例状态：使用中。

-   当前实例锁定模式：正常。


参数值有如下3类：

-   \[1-65535\]，表示数字范围，通过正则识别，从而提取出最小值，最大值。然后根据最小值和最大值对输入参数进行验证，另外，还须是整除因子的倍数。

-   \[utf8|gbk|latin1\]，表示固定的取值规则，通过正则识别，从而提取出固定的取值。然后根据这些固定的取值对输入参数进行验证。

-   其它，这种情况符合正则表达式。


下达任务之前，RDS将会进行参数检查，步骤如下：

-   参数是否存在。

-   参数是否可修改。

-   参数是否合法。


若参数非法，RDS返回400错误，并返回非法的参数信息。类似：

```
{"HttpStatusCode":400,"Code":"InvalidParameter.Format",
"Message":"Specified parameter is not valid.[auto_increment_increment:a,character_set_client:41]"}
```

## 请求参数 {#section_qzx_w32_12b .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是|系统规定参数，取值：`ModifyParameter`|
|DBInstanceId|String|是|实例名。|
|Parameters|String|是|参数及其值的JSON串，参数的值都是字符串类型，\{“auto\_increment”:”1”,“character\_set\_client”:”utf8”\}。|
|Forcerestart|String|否|true：强制重启（若修改的参数当中，有需要重启的参数，则必须传入true，否则修改将不生效）；false：不强制重启。默认不强制重启。|

## 返回参数 {#section_a5x_zlh_12b .section}

|名称|类型|描述|
|--|--|--|
|<公共返回参数\>| |详见[公共参数](intl.zh-CN/API参考/使用API/公共参数.md#)。|

## 请求示例 {#section_l4g_pj2_12b .section}

```
https://rds.aliyuncs.com/?Action=ModifyeParameter
&DBInstanceId=riauvjz6zajfiq6ba1370329449201L
&Parameters={"auto_increment":"1","character_set_client":"gbk"}
&<公共请求参数>
```

## 返回示例 {#section_xtg_rj2_12b .section}

**XML格式**

```
<ModifyeParameterResponse>
       <RequestId>542BB8D6-4268-45CC-A557-B03EFD7AB30A</RequestId>
</ModifyeParameterResponse>
```

**JSON格式**

```
{
       "RequestId":"542BB8D6-4268-45CC-A557-B03EFD7AB30A",
}
```

