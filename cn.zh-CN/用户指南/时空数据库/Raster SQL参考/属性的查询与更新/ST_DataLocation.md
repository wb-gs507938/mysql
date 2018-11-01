# ST\_DataLocation {#reference_dtg_kc4_qfb .reference}

获得raster对象的源文件路径。

## 语法 {#section_ysj_vhn_qfb .section}

```
text ST_DataLocation(raster rast);
```

## 参数 {#section_gyb_phn_qfb .section}

|参数名称|描述|
|:---|:-|
|rast|raster对象。|

## 示例 {#section_cxp_4jn_qfb .section}

```
select ST_DataLocation(rast) from rat;

__________________________________
oss://aaa:bbb:endpoint@/mybrucket/aaa.tif
```

