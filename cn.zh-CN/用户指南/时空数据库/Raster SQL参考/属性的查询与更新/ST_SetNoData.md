# ST\_SetNoData {#reference_dxb_bf4_qfb .reference}

设置raster对象的指定波段的NoData（无效值标识）的值。

## 语法 {#section_ysj_vhn_qfb .section}

```
boolean ST_IsGeoreferenced(raster rast);
```

## 参数 {#section_gyb_phn_qfb .section}

|参数名称|描述|
|:---|:-|
|rast|raster对象。|
|band|指定的波段序号，从0开始，-1表示所有波段。|
|nodata\_value|指定设置的nodata值。|

## 示例 {#section_cxp_4jn_qfb .section}

```
update rast set rast=ST_SetNoData(rast,0, 999.999);

__________________________________
(1 row)
```

