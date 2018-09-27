# RDS for MySQL release notes {#concept_kry_21l_n2b .concept}

## MySQL 5.7 {#section_qws_5xk_n2b .section}

**mysql57\_20180431:**

-   New features:
    -   Supports the High-availability Edition.
    -   Supports the [database proxy](https://www.alibabacloud.com/help/doc-detail/72253.htm) function.
    -   Supports [SQL audit](intl.en-US/User Guide/Security/SQL audit.md#).
    -   Enhanced protection for instances that are generating snapshots.

## MySQL 5.6 {#section_d3k_zxk_n2b .section}

-   **mysql\_201806\*\* \(5.6.16\) \(coming soon\):**
    -   New feature: Increases the slow log precision to microsecond.
-   **mysql\_20180426 \(5.6.16\)**
    -   New feature: Supports hidden indexes so that you can set invisible indexes. For more information, see [Reference](https://github.com/alibaba/AliSQL/wiki/Changes-in-AliSQL-5.6.32-(2017-07-16)#1-invisible-indexes).
    -   Bugs fixed:
        -   Fixed bugs that occur when backup instances are applying threads.
        -   Resolved the performance deterioration that occurs when backup instances are applying partition updates.
        -   Resolved the problem that an entire TokuDB table is rebuilt by the ALTER TABLE COMMENT command. For more information, see [Reference](https://github.com/alibaba/AliSQL/wiki/Changes-in-AliSQL-5.6.32-(2018-05-01)#1-alter-tokudb-table-comment-rebuild-whole-engine-data).
        -   Resolved possible deadlocks triggered by the SHOW SLAVE STATUS or SHOW STATUS command.
-   **mysql\_20171205 \(5.6.16\):**
    -   Resolved the problem that concurrent execution of OPTIMIZE TABLE and ONLINE ALTER TABLE causes deadlocks.
    -   Resolved conflicts between SEQUENCE and implicit primary keys.
    -   Resolved problems related to SHOW CREATE SEQUENCE.
    -   Resolved the problem that TokuDB table statistics are incorrect.
    -   Resolved the problem that parallel OPTIMIZE table commands cause deadlocks.
    -   Resolved the character set problems recorded in QUERY\_LOG\_EVENT.
    -   Resolved the problem that databases cannot be stopped due to signal processing. For more information, see [Reference](https://github.com/alibaba/AliSQL/wiki/Changes-in-AliSQL-5.6.32-%282017-10-10%29#1-the-ack-receiver-thread-didnt-handle-signal-correctly).
    -   Resolved problems caused by RESET MASTER.
    -   Resolved the problem that backup databases are stuck in the waiting state.
    -   Resolved the status maintenance problem caused by master node failovers of Finance Edition instances.
    -   Resolved the possible process termination caused by SHOW CREATE TABLE.
-   **mysql\_20170927 \(5.6.16\):**
    -   Resolved the problem that TokuDB table queries use incorrect indexes.
-   **mysql\_20170901 \(5.6.16\):**
    -   New features:
        -   The SSL encryption version is upgraded to TLS1.2. For more information, see [Reference](https://github.com/alibaba/AliSQL/wiki/Changes-in-AliSQL-5.6.32-(2017-10-10)#2-upgrade-ssl-tlsv12).
        -   SEQUENCE is supported.
    -   Resolved the problem that NOT IN queries return incorrect results in certain scenarios.
-   **mysql\_20170530 \(5.6.16\):**
    -   New feature: A master account can kill connections of common accounts.
-   **mysql\_20170221 \(5.6.16\):**
    -   New feature: [Read/write splitting](intl.en-US/User Guide/Read/write splitting/Introduction to read/write splitting.md#) is supported

