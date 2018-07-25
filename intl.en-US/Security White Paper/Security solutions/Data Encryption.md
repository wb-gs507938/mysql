# Data Encryption {#concept_kx4_ghc_p2b .concept}

## SSL {#section_zk3_hhc_p2b .section}

RDS provides Secure Sockets Layer \(SSL\) for MySQL and SQL Server. You can use the server root certificate provided by RDS to verify whether the database service with the target IP address and port is provided by RDS, which can effectively prevent man-in-the-middle attacks. To guarantee security and validity, RDS allows you to enable and update the SSL certificates for servers.

Though RDS can encrypt the connection between an application and a database, the SSL service can run properly only after the application enables authentication on the server. In addition, SSL results in extra CPU resource consumption and affects the throughput and response time of RDS instances to a certain degree. The specific impact varies depending on the number of user connection times and the data transfer frequency.

For operational instructions, see [Set SSL encryption](../../../../intl.en-US/User Guide/Security management/Set SSL encryption.md).

## TDE {#section_al3_hhc_p2b .section}

RDS provides transparent data encryption \(TDE\) for MySQL and SQL Server. The TDE function of RDS for MySQL is developed by Alibaba Cloud and the TDE function of RDS for SQL Server is based on the SQL Server Enterprise Edition.

You can specify the database or table to be encrypted in a TDE-enabled RDS instance. The data of the specified database or table is encrypted before being written to any device such as an HDD, SSD, or PCIe card, or to any service such as OSS or Archive Storage. Therefore, data files and backups of the instance are all ciphertext.

TDE adopts the Advanced Encryption Standard \(AES\) algorithm. The key length is 128 bits. The key for TDE is encrypted and stored by KMS, and RDS dynamically reads the key only once when the instance is started or migrated. You can replace the key as needed on the KMS console.

For operational instructions, see [Set Transparent Data Encryption](../../../../intl.en-US/User Guide/Security management/Set Transparent Data Encryption.md).

