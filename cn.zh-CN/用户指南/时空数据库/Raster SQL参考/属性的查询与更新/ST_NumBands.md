# ST\_NumBands {#reference_amw_4zn_qfb .reference}

获得raster对象的波段数。

## 语法 {#section_ysj_vhn_qfb .section}

```
integer ST_NumBands(raster rast);
```

## 参数 {#section_gyb_phn_qfb .section}

|参数名称|描述|
|:---|:-|
|rast|raster对象。|

## 示例 {#section_cxp_4jn_qfb .section}

```
select ST_NumBands(rast) from rat;

——————————————————————————————————
3
```

