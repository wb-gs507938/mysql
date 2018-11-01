# S​T\_Rast2WorldCoord {#reference_lpr_zgn_qfb .reference}

由像元坐标及像元所在金字塔层级，根据仿射变换公式计算世界坐标。

## 语法 {#section_wkk_wcn_qfb .section}

```
point ST_Rast2WorldCoord(raster rast, integer pyramidLevel,  integer row,  integer column);
```

## 参数 {#section_whn_ddn_qfb .section}

|参数名称|描述|
|:---|:-|
|rast|目标raster对象|
|pyramidLevel|金字塔层级|
|row|行号|
|column|列号|

## 描述 {#section_f2z_ctn_qfb .section}

raster对象必须要有空间参考。

## 示例 {#section_xhh_zfn_qfb .section}

```
Select ST_Rast2WorldCoord(rast, 0, 0, 0) from rat;
```

