# SQL Server结束连接 {#concept_zrc_nmn_wdb .concept}

**说明：** 本文仅适用于RDS for SQL Server 2012及以上版本的实例。

RDS SQL Server 2012及以上版本已被授予结束连接的权限（即KILL权限），但您只能结束自己的连接，无法结束其它连接，例如备份的连接。

执行如下命令，即可结束连接：`KILL (SPID)`

