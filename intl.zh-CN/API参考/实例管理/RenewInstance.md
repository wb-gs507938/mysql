# RenewInstance {#reference1317 .reference}

手动对实例进行续费，仅适用于包年包月实例。

## 描述 {#section_fbc_rqg_yfb .section}

**说明：** 请确保在使用该接口前，已充分了解RDS产品的收费方式和[价格](https://www.aliyun.com/price/product?spm=a2c4g.11186623.2.16.7a92a4c9MxTq85#/rds/detail)。

您可以通过该接口为RDS 实例续费。需要注意：

-   该接口仅支持续费包年包月RDS 实例。
-   付款时，默认优先使用您的账号下可用的优惠券。
-   您的账号必须支持账号余额支付或信用支付。

## 请求参数 {#section_xxc_rqg_yfb .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是|系统规定参数，取值：RenewInstance。|
|DBInstanceId|String|是|指定的需要实例规格的实例 ID。|
|Period|Integer|是|预付费续费时长。取值范围：-   \[1,9\]
-   12
-   24
-   36
-   48
-   60

|
|PeriodUnit|String|否|预付费参数Period的单位。取值范围：-   Week：取值为 Week 时，参数 Period 的取值范围为 \{1, 2, 3, 4\}。
-   Month：取值为 Month 时，参数 Period 的取值范围为  \{ 1, 2, 3, 4, 5, 6, 7, 8, 9, 12, 24, 36, 48, 60\}。

默认值：Month。

|
|ClientToken|String|否|用于保证请求的幂等性。由客户端生成该参数值，要保证在不同请求间唯一，最大值不超过 64 个 ASCII 字符，且该参数值中不能包含非 ASCII 字符。|
|AutoPay|String|否|是否自动付费。取值：-   True：自动付费。请确保账号有足够的余额。
-   False：您需要到控制台手动付费。具体操作为：登录控制台，在右上角选择**费用** \> **进入费用中心**，在订单管理找到目标订单进行支付。

默认值：False。

|

## 返回参数 {#section_pzj_rqg_yfb .section}

|参数|类型|描述|
|--|--|--|
|OrderId|String|订单ID。|
|RequestId|String|请求ID。|

## 请求示例 {#section_wrk_rqg_yfb .section}

```
http://rds.aliyuncs.com/?
&Action=RenewInstance
&DBInstanceId=rm-xxxxx
&Period=12
&&<公共请求参数>d=1
```

## 返回示例 {#section_m2l_rqg_yfb .section}

**JSON格式**

```
{"OrderId":"202844382740728",
"RequestId":"372EB863-7AC6-4883-B519-F6590677AFA4"}
```

**异常返回示例**

```
{"RequestId":"ABE64F05-7621-4244-9390-86076A63B7AB",
"HostId":"rds.aliyuncs.com",
"Code":"INST_HAS_UNPAID_ORDER",
"Message":"The specified db instance has unpaid order."}
```

## 错误码 {#section_fvp_2wg_yfb .section}

[查看本产品错误码](https://error-center.aliyun.com/status/product/Rds)

