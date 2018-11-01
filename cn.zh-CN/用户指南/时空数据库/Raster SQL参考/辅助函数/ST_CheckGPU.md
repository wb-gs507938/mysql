# ST\_CheckGPU {#reference_lfr_mhn_qfb19 .reference}

验证是否有GPU环境。

## 语法 {#section_og1_4hn_qfb .section}

```
text  ST_CheckGPU();
```

## 参数 {#section_cxv_qhn_qfb .section}

验证当前运行环境是否有可识别的GPU设备。

## 示例 {#section_lmw_qhn_qfb .section}

```
postgres=# select st_checkgpu();
                                      st_checkgpu                                       
----------------------------------------------------------------------------------------
 [GPU prop]multiProcessorCount=20; sharedMemPerBlock=49152; maxThreadsPerBlock=1024 .\r+
 
(1 row)
```

