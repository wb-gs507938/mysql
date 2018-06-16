# End connection for SQL Server instances {#concept_zrc_nmn_wdb .concept}

**Note:** The operation described in this document is applicable only to instances of RDS SQL Server 2012 and later versions.

Instances of RDS SQL Server 2012 and later versions are granted the End Connection \(Kill\) permission. However, you can only end the connection that you created and cannot end other connections, for example, backup connection.

Run the following command to end a connection: `KILL(SPID)`

