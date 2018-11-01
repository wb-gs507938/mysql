# ST\_ClearChunks {#reference_ukg_124_qfb .reference}

清空一个raster对象所有的块数据。

## 语法 {#section_og1_4hn_qfb .section}

```
raster ST_ClearChunks(raster rast);
```

## 参数 {#section_cxv_qhn_qfb .section}

|参数名称|描述|
|----|--|
|rast|需要清空块的rast对象。|

该函数会清空raster对象所有的块，不正确使用会导致raster对象无法正确获取，仅在删除raster对象时供触发器使用。

## 示例 {#section_lmw_qhn_qfb .section}

```
Select ST_ClearChunks(rast) From rat where id = 1;
```

