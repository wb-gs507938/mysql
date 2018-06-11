# Why does RDS for MySQL not support the MyISAM engine? {#concept_idt_zxx_b2b .concept}

The following lists the major reasons why RDS for MySQL does not support the MyISAM engine:

-   MyISAM has defects in data integrity protection, and these defects may cause corruption or even loss of database data. Additionally, many of these defects are design issues and cannot be fixed without compromising compatibility.

-   Most data corruption issues of MyISAM can only be manually fixed, and therefore MyISAM cannot be used for product services.

-   For RDS storage, MyISAM is not the best solution for I/O operations. Therefore, MyISAM does not necessarily surpass InnoDB in terms of performance.

-   It is easy to migrate from MyISAM to InnoDB because most applications simply need to modify the table creation code.

-   MyISAM is developing towards InnoDB. MySQL 5.7 can be completely different from MyISAM and the system's data control is also switched to InnoDB.


