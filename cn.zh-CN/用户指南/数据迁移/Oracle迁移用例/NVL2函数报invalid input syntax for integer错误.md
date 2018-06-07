# NVL2函数报invalid input syntax for integer错误 {#concept_qhj_1r5_ydb .concept}

## 错误描述 {#section_pzz_qr5_ydb .section}

```
ERROR:  invalid input syntax for integer: "aa"LINE 1: select nvl2('aa',1,2);                    ^********** Error **********ERROR: invalid input syntax for integer: "aa"SQL state: 22P02Character: 13
```

## 解决方案 {#section_h2v_rr5_ydb .section}

通过自行扩充一个自定义的public.nvl2即可解决数据类型问题，同时用户无需要调整原有Oracle已经开发好的程序或存储过程。

```
create or replace function public.nvl2(p_v1 string, p_v2 anyelement, p_v3 anyelement) return anyelement as
declare
    v_v1 int;
begin
    IF p_v1 NOTNULL THEN 
        v_v1=1;
    ELSE 
        v_v1=null; 
    END IF;
    return pg_catalog.nvl2(v_v1, p_v2, p_v3);
end;
select nvl2('aa',1,2); --此时运行的应该是上面新建立的public.nvl2
select nvl2(100,1,2);  --此时运行的应该是系统原生的pg_catalog.nvl2
select nvl2(null,1,2);  --此时运行的应该是系统原生的pg_catalog.nvl2
```

