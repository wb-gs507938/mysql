# ST\_RasterMode {#reference_wfg_jd4_qfb .reference}

获得raster对象的存储模式。可以为以下值之一：“Internal”，“External”。

## 语法 {#section_ysj_vhn_qfb .section}

```
 text ST_RasterMode(raster rast);
```

## 参数 {#section_gyb_phn_qfb .section}

|参数名称|描述|
|:---|:-|
|rast|raster对象。|

## 示例 {#section_cxp_4jn_qfb .section}

```
select ST_RasterMode(rast) from rat where id=1;

__________________________________
internal
```

