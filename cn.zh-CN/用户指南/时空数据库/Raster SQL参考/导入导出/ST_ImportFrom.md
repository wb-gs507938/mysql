# ST\_ImportFrom {#reference_lpr_zgn_qfb .reference}

从一个OSS文件导入到数据库。

## 语法 {#section_wkk_wcn_qfb .section}

```
raster ST_ImportFrom(cstring chunkTableName, cstring url);
```

## 参数 {#section_whn_ddn_qfb .section}

|参数名称|描述|
|:---|:-|
|chunkTableName|块表的名称，名称必须符合数据库表名的规范。|
|u​rl|外部文件路径，参考 [ST\_CreateRast](cn.zh-CN/用户指南/时空数据库/Raster SQL参考/R​aster创建/ST_CreateRast.md#) 中构建路径的描述。|

## 描述 {#section_f2z_ctn_qfb .section}

函数将创建一个raster对象，并将外部OSS文件导入到该对象中。

## 示例 {#section_xhh_zfn_qfb .section}

```
Select ST_ImportFrom('rbt2','OSS://ABCDEFG:1234567890@oss-cn.aliyuncs.com/mybucket/data/4.tif');
```

