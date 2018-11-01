# ST\_makeTrajectory {#reference_lfr_mhn_qfb1 .reference}

构造一个trajectory对象。

## 语法 {#section_og1_4hn_qfb .section}

```
trajectory ST_makeTrajectory (leaftype type, geometry spatial, tsrange timespan , cstring str_theme_json);
trajectory ST_makeTrajectory (leaftype type, geometry spatial, timestamp start, timestamp end , cstring str_theme_json);
trajectory ST_makeTrajectory (leaftype type, geometry spatial, timestamp[] timeline, cstring str_theme_json );
```

## 参数 {#section_cxv_qhn_qfb .section}

|参数名称|描述|
|----|--|
|type|轨迹的类型，目前只支持 ST\_POINT。|
|spatial|基于 LineString类型的轨迹路径。|
|timespan|轨迹的时间段。|
|start|轨迹的开始时间。|
|end|轨迹的结束时间。|
|timeline|轨迹的时间序列，数量必须和linestring的点数量一致。|
|str\_theme\_json|属性数据信息字符串，json格式。|

str\_theme\_json的格式为`'{"nleafs":3,"themes":{"velocity":[120, 130, 140],"accuracy":[120, 130, 140],"bearing":[120, 130, 140],"acceleration":[120, 130, 140]}}'`， nleafs为每个属性的元素个数，必须与spatial中的点个数保持一致，且所有属性元素个数都必须一致；themes为属性项，格式为'属性名:属性值数组'，属性顺序无要求，如果无属性，固定为null。

目前属性值只支持数值型，统一保存为double，不支持字符串型。

如果传入的为 timespan 或者 start、end参数，则会根据spatial中点的个数进行插值。

## 示例 {#section_lmw_qhn_qfb .section}

```
-- (1) ST_MakeTrajectory with timestamp range
select ST_MakeTrajectory('STPOINT'::leaftype, st_geomfromtext('LINESTRING (114 35, 115 36, 116 37)', 4326), '[2010-01-01 14:30, 2010-01-01 15:30)'::tsrange, '{"nleafs":3,"themes":{"velocity":[120, 130, 140],"accuracy":[120, 130, 140],"bearing":[120, 130, 140],"acceleration":[120, 130, 140]}}');
                        st_maketrajectory         
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- 
{"trajectory":{"leafsize":3,"starttime":"Fri Jan 01 14:30:00 2010","endtime":"Fri Jan 01 15:30:00 2010","spatial":"LINESTRING(114 35,115 36,116 37)","timeline":["Fri Jan 01 14:30:00 2010","Fri Jan 01 15:00:00 2010","Fri Jan 01 15:30:00 2010"],"themeline":{"leafs":3,"velocity":[120.0,130.0,140.0],"accuracy":[120.0,130.0,140.0],"bearing":[120.0,130.0,140.0],"acceleration":[120.0,130.0,140.0]}}}
(1 row)

-- (2) ST_MakeTrajectory with start timestamp and end timestamp
select ST_MakeTrajectory('STPOINT'::leaftype, st_geomfromtext('LINESTRING (114 35, 115 36, 116 37)', 4326), '2010-01-01 14:30'::timestamp, '2010-01-01 15:30'::timestamp, '{"nleafs":3,"themes":{"velocity":[120, 130, 140],"accuracy":[120, 130, 140],"bearing":[120, 130, 140],"acceleration":[120, 130, 140]}}');
                        st_maketrajectory                                                                                                                                                                                             
 ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- 
{"trajectory":{"leafsize":3,"starttime":"Fri Jan 01 14:30:00 2010","endtime":"Fri Jan 01 15:30:00 2010","spatial":"LINESTRING(114 35,115 36,116 37)","timeline":["Fri Jan 01 14:30:00 2010","Fri Jan 01 15:00:00 2010","Fri Jan 01 15:30:00 2010"],"themeline":{"leafs":3,"velocity":[120.0,130.0,140.0],"accuracy":[120.0,130.0,140.0],"bearing":[120.0,130.0,140.0],"acceleration":[120.0,130.0,140.0]}}}
(1 row)

-- (3) ST_MakeTrajectory with timestamp array
select ST_MakeTrajectory('STPOINT'::leaftype, st_geomfromtext('LINESTRING (114 35, 115 36, 116 37)', 4326),ARRAY['2010-01-01 14:30'::timestamp, '2010-01-01 15:00'::timestamp, '2010-01-01 15:30'::timestamp], '{"nleafs":3,"themes":{"velocity":[120, 130, 140],"accuracy":[120, 130, 140],"bearing":[120, 130, 140],"acceleration":[120, 130, 140]}}'); 
                        st_maketrajectory                                                                                                                                                                                              
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- 
{"trajectory":{"leafsize":3,"starttime":"Fri Jan 01 14:30:00 2010","endtime":"Fri Jan 01 15:30:00 2010","spatial":"LINESTRING(114 35,115 36,116 37)","timeline":["Fri Jan 01 14:30:00 2010","Fri Jan 01 15:00:00 2010","Fri Jan 01 15:30:00 2010"],"themeline":{"leafs":3,"velocity":[120.0,130.0,140.0],"accuracy":[120.0,130.0,140.0],"bearing":[120.0,130.0,140.0],"acceleration":[120.0,130.0,140.0]}}}
(1 row)  

--json is null
select ST_MakeTrajectory('STPOINT'::leaftype, st_geomfromtext('LINESTRING (114 35, 115 36, 116 37)', 4326), '[2010-01-01 14:30, 2010-01-01 15:30)'::tsrange, null); 
                        st_maketrajectory                                                                                                                  
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ 
{"trajectory":{"leafsize":3,"starttime":"Fri Jan 01 14:30:00 2010","endtime":"Fri Jan 01 15:30:00 2010","spatial":"LINESTRING(114 35,115 36,116 37)","timeline":["Fri Jan 01 14:30:00 2010","Fri Jan 01 15:00:00 2010","Fri Jan 01 15:30:00 2010"]}}
(1 row)
```

