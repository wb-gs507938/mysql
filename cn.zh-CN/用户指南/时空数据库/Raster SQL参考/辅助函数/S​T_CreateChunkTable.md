# S​T\_CreateChunkTable {#reference_pmy_yd4_qfb .reference}

创建辅助的块存储表。

## 语法 {#section_og1_4hn_qfb .section}

```
raster ST_CreateChunkTable(cstring chunkTableName);
```

## 参数 {#section_cxv_qhn_qfb .section}

|参数名称|描述|
|----|--|
|chunkTableName|块表名称，必须符合数据库命名规范。|

## 示例 {#section_lmw_qhn_qfb .section}

```
Select ST_CreateChunkTable('rbt');
```

