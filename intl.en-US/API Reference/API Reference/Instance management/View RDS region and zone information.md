# View RDS region and zone information {#reference_arw_tv2_12b .reference}

## Description {#section_l21_v32_12b .section}

Show the selectable RDS regions and zones. Before calling the CreateInstance interface, use this interface to view RegionId.

## Request parameters {#section_qzx_w32_12b .section}

|Name|Type|Required?|Description|
|----|----|---------|-----------|
|Action|String|Yes|DescribeRegions|

## Return parameters {#section_rpk_z32_12b .section}

|Name|Type|Description|
|----|----|-----------|
|<Public Return Parameters\>|-|For more information, see [Public parameters](intl.en-US/API Reference/Use APIs/Public parameters.md#).|
|Regions|List<RDSRegion\>|Returned region list.|

## RDSRegion {#section_c3m_3w2_12b .section}

|Name|Type|Description|
|----|----|-----------|
|RegionId|String|Data center.|
|ZoneId|String|Zone.|

## Request example {#section_l4g_pj2_12b .section}

```
https://rds.aliyuncs.com/?Action=DescribeRegions
&<Public Request Parameters>
```

## Response example {#section_xtg_rj2_12b .section}

**XML format**

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
</Rdsregion>
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
<RequestId> </RequestId>
</DescribeRegionsResponse>
```

**JSON format**

```

    "Regions": {
      "RDSRegion": [
        {"RegionId": "cn-hangzhou","ZoneId":"cn-hangzhou-a"}, 
        {"RegionId": "cn-hangzhou","ZoneId":"cn-hangzhou-b"},
        { "RegionId": "cn-qingdao","ZoneId":"cn-qingdao-b"}, 
        {"RegionId": "cn-beijing","ZoneId": "cn-beijing-a"}, 
        { "RegionId": "cn-hongkong","ZoneId": "cn-hongkong-a"}, 
        
      
 
    "RequestId": "A36D9720-7902-42A4-B8B9-014A2135E6C3"

```

