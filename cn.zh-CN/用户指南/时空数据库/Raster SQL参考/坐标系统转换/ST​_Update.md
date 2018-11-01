# ST​\_Update {#reference_lpr_zgn_qfb .reference}

用源raster更新目标raster。

## 语法 {#section_wkk_wcn_qfb .section}

```
raster ST_Update(raster source,  raster dest);
```

## 参数 {#section_whn_ddn_qfb .section}

|参数名称|描述|
|:---|:-|
|source|源raster对象。|
|dest|目标raster对象。|

## 示例 {#section_xhh_zfn_qfb .section}

```
Update rat Set rast=ST_Update(rast, (Select rast from rat where id=2)) where id = 1 ;
```

