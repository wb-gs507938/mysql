# ST\_bearingAtTime {#reference_ecl_jsn_qfb .reference}

获取指定时间位置的方位角属性。

## 语法 {#section_og1_4hn_qfb .section}

```
float8 ST_bearingAtTime (trajectory traj, timestamp t);
```

## 参数 {#section_cxv_qhn_qfb .section}

|参数名称|描述|
|----|--|
|traj|轨迹对象。|
|t|指定的时间点。|

## 示例 {#section_lmw_qhn_qfb .section}

```
Select ST_bearingAtTime(traj) From traj_table;
```

