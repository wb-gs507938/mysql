# DescribeRegions {#reference_arw_tv2_12b .reference}

## 描述 {#section_l21_v32_12b .section}

该接口用于查看用户可选的RDS地域和可用区。调用创建实例接口之前，先用该接口查询RegionId。

## 请求参数 {#section_qzx_w32_12b .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是|DescribeRegions|

## 返回参数 {#section_rpk_z32_12b .section}

|名称|类型|描述|
|--|--|--|
|<公共返回参数\>|-|详见[公共参数](cn.zh-CN/API参考/使用API/公共参数.md#)。|
|Regions|List<RDSRegion\>|返回Region列表。|

## RDSRegion {#section_c3m_3w2_12b .section}

|名称|类型|描述|
|--|--|--|
|RegionId|String|数据中心。|
|ZoneId|String|可用区。|

## 请求示例 {#section_l4g_pj2_12b .section}

```
https://rds.aliyuncs.com/?Action=DescribeRegions
&<公共请求参数>
```

## 返回示例 {#section_xtg_rj2_12b .section}

**XML格式**

```
<DescribeRegionsResponse>
 <Regions>
  <RDSRegion>
<RegionId>cn-hangzhou</RegionId>
<ZoneId>cn-hangzhou-a</RegionId>
  </RDSRegion>
  <RDSRegion>
<RegionId>cn-hangzhou</RegionId>
<ZoneId>cn-hangzhou-b</ZoneId>
  </RDSRegion>
  <RDSRegion>
<RegionId>cn-qingdao</RegionId>
<ZoneId>cn-qingdao-a</ZoneId>
  </RDSRegion>
  <RDSRegion>
<RegionId>cn-beijing</RegionId>
<ZoneId>cn-beijing-a</ZoneId>
  </RDSRegion>
  <RDSRegion>
<RegionId>cn-hongkong</RegionId>
<ZoneId>cn-hongkong-a</ZoneId>
  </RDSRegion>
  <RDSRegion>
<RegionId>cn-shenzhen</RegionId>
<ZoneId>cn-shenzhen-a</ZoneId>
  </RDSRegion>
</Regions>
<RequestId>A36D9720-7902-42A4-B8B9-014A2135E6C3</RequestId>
</DescribeRegionsResponse>
```

**JSON格式**

```
{
    "Regions": {
      "RDSRegion": [
        {"RegionId": "cn-hangzhou","ZoneId":"cn-hangzhou-a"}, 
        {"RegionId": "cn-hangzhou","ZoneId":"cn-hangzhou-b"},
        { "RegionId": "cn-qingdao","ZoneId":"cn-qingdao-b"}, 
        {"RegionId": "cn-beijing","ZoneId": "cn-beijing-a"}, 
        { "RegionId": "cn-hongkong","ZoneId": "cn-hongkong-a"}, 
        {"RegionId": "cn-shenzhen","ZoneId": "cn-shenzhen-a"}
      ]
}, 
    "RequestId": "A36D9720-7902-42A4-B8B9-014A2135E6C3"
}
```

