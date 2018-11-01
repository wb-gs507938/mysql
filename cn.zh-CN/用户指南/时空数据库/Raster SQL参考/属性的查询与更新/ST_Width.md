# ST\_Width {#reference_jqc_cyn_qfb .reference}

获得raster对象的宽度。如果需要获得分块的宽度，参见ST\_ChuckWidth。

## 语法 {#section_jjm_myn_qfb .section}

```
integer ST_Width(raster rast);
```

## **参数** {#section_syp_pyn_qfb .section}

|参数名称|描述|
|----|--|
|rast|raster对象。|

## 示例 {#section_gqv_5yn_qfb .section}

```
select ST_Width(rast) from rat; —————————————————————————————— 10060
```

