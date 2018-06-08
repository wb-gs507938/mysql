# DescribeDBInstanceIPArrayList {#reference_jgc_wbh_12b .reference}

## 描述 {#section_l21_v32_12b .section}

该接口用于查询允许访问实例的IP名单。

## 请求参数 {#section_qzx_w32_12b .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是|系统规定参数，取值为DescribeDBInstanceIPArrayList。|
|DBInstanceId|String|是|实例名。|

## 返回参数 {#section_rpk_z32_12b .section}

|名称|类型|描述|
|--|--|--|
|<公共返回参数\>| |详见[公共参数](cn.zh-CN/API参考/使用API/公共参数.md#)。|
|Items|List<DBInstanceIPArray\>|实例的IP白名单分组列表。|

## DBInstanceIPArray的参数 {#section_wzp_cch_12b .section}

|名称|类型|描述|
|--|--|--|
|DBInstanceIPArrayName|String|IP白名单分组的名字。|
|DBInstanceIPArrayAttribute|String|默认为空。用以区分不同的属性值，控制台不显示带有“hidden”标签的分组。|
|SecurityIPList|String|IP白名单分组下的IP列表，最多1000个以逗号隔开，有以下三种格式：-   0.0.0.0/0；
-   10.23.12.24（IP）；
-   10.23.12.24/24（CIDR模式，无类域间路由，/24表示了地址中前缀的长度，范围\[1,32\]）。

|

