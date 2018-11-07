# S​T\_BuildPyramid {#reference_lpr_zgn_qfb .reference}

创建影像金字塔。

## 语法 {#section_wkk_wcn_qfb .section}

```
raster ST_BuildPyramid(raster source);
raster ST_BuildPyramid(raster source,  cstring chunkTableName);
```

## 参数 {#section_whn_ddn_qfb .section}

|参数名称|描述|
|:---|:-|
|source|需要创建金字塔的raster对象。|
|chunkTableName|金字塔所存储的分块表名称。|

## 示例 {#section_xhh_zfn_qfb .section}

```
Update raster_table set raster_obj = ST_BuildPyramid(raster_obj) where id = 1;

Update raster_table set raster_obj = ST_BuildPyramid(raster_obj, 'chunk_table') where id = 2;
```

