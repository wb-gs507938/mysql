# S​T\_ExportAsTIFF {#reference_lpr_zgn_qfb .reference}

将一个raster对象导出为TiffG格式的OSS文件。

## 语法 {#section_wkk_wcn_qfb .section}

```
boolean ST_ExportAsTIFF(raster source,  cstring url,  integer level = 0);
```

## 参数 {#section_whn_ddn_qfb .section}

|参数名称|描述|
|:---|:-|
|source|需要导出的raster对象。|
|url|外部文件路径，参考 [ST\_CreateRast](cn.zh-CN/用户指南/时空数据库/Raster SQL参考/R​aster创建/ST_CreateRast.md#) 中构建路径的描述。|
|level|需要导出的金字塔层级。|

## 描述 {#section_s3l_ltn_qfb .section}

导出成功返回true，失败则返回false。

## 示例 {#section_xhh_zfn_qfb .section}

```
Select ST_ExportTo(raster, 'OSS://ABCDEFG:1234567890@oss-cn.aliyuncs.com/mybucket/data/4.tif') from rat where id=1;
```

