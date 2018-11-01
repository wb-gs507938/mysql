# ST\_leafType {#reference_lfr_mhn_qfb .reference}

获得轨迹的叶面类型。

## 语法 {#section_og1_4hn_qfb .section}

```
leaftype ST_leafType(trajectory traj);
```

## 参数 {#section_cxv_qhn_qfb .section}

|参数名称|描述|
|----|--|
|traj|需要获得类型的轨迹。|

目前只支持ST\_POINT类型。

## 示例 {#section_lmw_qhn_qfb .section}

```
Select ST_leafType(raj) from traj_table;
```

