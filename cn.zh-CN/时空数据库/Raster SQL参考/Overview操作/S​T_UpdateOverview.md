# S​T\_UpdateOverview {#reference_p3y_wc4_qfb .reference}

使用raster对象对overview进行更新。

## 语法 {#section_og1_4hn_qfb .section}

```
raster ST_UpdateOverview(raster raster_obj,raster source[]);
```

## 参数 {#section_cxv_qhn_qfb .section}

|参数名称|描述|
|----|--|
|raster\_obj|需要更新的raster对象。|
|source|源raster对象。|

所有指定的raster对象需要满足以下条件：

-   具有相同的波段数。
-   所有的raster对象要么都进行了地理参考，要么都不是。如果都是地理参考，则采用世界坐标镶嵌。
-   指定raster对象的像素类型可以不同。如果是世界坐标镶嵌，则SRID、像素分辨率必须一致。

## 示例 {#section_lmw_qhn_qfb .section}

```
Update raster_table set raster_obj = ST_UpdateOverview(raster_obj, Array(select raster_obj from raster_table_new)) where id = 1;
```

