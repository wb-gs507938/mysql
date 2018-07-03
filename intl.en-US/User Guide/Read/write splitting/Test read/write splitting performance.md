# Test read/write splitting performance {#concept_mfj_hqp_wdb .concept}

After the read/write splitting is enabled, all transactions are routed to the master instance by default. Using Sysbench 0.5, the MySQL stress testing tool, as an example, this article describes how to correctly configure its parameters to conduct read/write splitting performance testing.

## Prerequisites {#section_x4z_pqp_wdb .section}

-   The read/write splitting function is enabled. See [Enable read/write splitting](intl.en-US/User Guide/Read/write splitting/Enable read/write splitting.md#) for detailed procedures.

-   The Sysbench 0.5 is installed. See [Sysbench documentation](https://github.com/akopytov/sysbench/tree/0.5) for instructions on downloading and installing Sysbench 0.5.


## Attentions {#section_cv2_rqp_wdb .section}

-   We recommend that a case with prepare or a transaction not be used to test the load balancing of the read/write splitting function.

-   Avoid the master/slave latency from exceeding the threshold set for the monitoring check due to high stress on write requests.

-   We recommend that you use the following Sysbench scripts to build a specific SQL statement as needed.

    ```
    function thread_init(thread_id)
          db_connect()
      end
    
      function event(thread_id)
          rs = db_query("select 1")
      end
    ```


## Set Sysbench parameters {#section_hnt_tqp_wdb .section}

A transaction is used by default to test the Sysbench oltp.lua script. If you use default parameters, all SQL statements are executed in the transaction and read-only SQL statements are routed to the master database for execution. Therefore, when the Sysbench is used to benchmark the read/write splitting, you must set the Sysbench parameters as needed. For example, you can set the ‘oltp-skip-trx’ parameter to make sure that the Sysbench does not run the SQL statement in a transaction.

## Set common parameters {#section_hql_wqp_wdb .section}

You can set the following parameters as needed.

|Name|Description|
|----|-----------|
|test|Path of the test file.|
|mysql-host|IP address of the MySQL server.|
|mysql-port|Port of the MySQL server.|
|mysql-user|User name.|
|mysql-password|Password.|
|mysql-db|Database for test, which must be created in advance.|
|oltp-tables-count|Number of created tables.|
|oltp-table-size|Number of records generated in each table.|
|rand-init|Indicates whether the data is randomly initialized.|
|max-time|Stress testing duration.|
|max-requests|Total number of requests in a stress testing duration.|
|num-threads|Number of concurrent threads.|
|report-interval|Reporting interval of operating logs.|

## Set parameters for transactions and read/write SQL statements {#section_d2h_yqp_wdb .section}

The following parameters can affect transactions and read/write SQL statements. Therefore, you must set parameters in read/write splitting benchmark tests as needed.

|Name|Description|
|----|-----------|
|oltp-test-mode|Test mode. But this parameter is unavailable in the Sysbench 0.5, so ignore this parameter. Possible values:-   complex: Transactional test as the default value.
-   Simple: Simple test for read-only SQL statements.
-   nontrx: Non-transactional test.
-   sp: Stored procedures.

|
|oltp-skip-trx|Indicates whether begin at the beginning of the SQL statement and commit at the end of the SQL statement are omitted. Possible values:-   off: Default value. All SQL statements are executed in transactions.
-   On: Non-transactional mode. If a comparative stress test is executed repeatedly, you must run prepare and cleanup again.

**Note:** When a stress test is executed to benchmark the read/write splitting performance, you must set it as “on” and omit the begin/commit at the beginning and end of the SQL statement.

|
|oltp-read-only|Indicates whether read-only SQLs are generated. Possible values:-   off: Default value. The mixed read/write SQL statements of oltp.lua is executed.
-   on: Only read-only SQL statements are generated. UPDATE, DELETE, and INSERT SQL statements are not applicable.

**Note:** Set parameter values as needed to perform read-only or read/write tests.

|

## Stress testing examples {#section_wwh_prp_wdb .section}

**Test read/write performance**

1.  Run prepare command.

    ```
    sysbench --test=./tests/db/oltp.lua --mysql-host=127.0.0.1 --mysql-port=3001 --mysql-user=abc --mysql-password=abc123456 --mysql-db=testdb --oltp-tables-count=10 --oltp-table-size=500000 --report-interval=5 --oltp-skip-trx=on --oltp-read-only=off --rand-init=on --max-requests=0 --max-time=300 --num-threads=100 prepare;
    ```

2.  Run run command.

    **Note:** When data is updated for non-transactional read/write tests, errors such as `ALERT: Error 1062 Duplicate entry 'xxx' for key 'PRIMARY'` may occur. You must add `--mysql-ignore-errors=1062` to skip these errors. If the parameter `mysql-ignore-errors` is not effective, it indicates that your current Sysbench version is too old and you must upgrade it to the latest version.

    ```
    sysbench --test=./tests/db/oltp.lua --mysql-host=127.0.0.1 --mysql-port=3001 --mysql-user=abc --mysql-password=abc123456 --mysql-db=testdb --oltp-tables-count=10 --oltp-table-size=500000 --report-interval=5 --oltp-skip-trx=on --oltp-read-only=off --mysql-ignore-errors=1062 --rand-init=on --max-requests=0 --max-time=300 --num-threads=100 run;
    ```

3.  Run cleanup command.

    ```
    sysbench --test=./tests/db/oltp.lua --mysql-host=127.0.0.1 --mysql-port=3001 --mysql-user=abc --mysql-password=abc123456 --mysql-db=testdb --oltp-tables-count=10 --oltp-table-size=500000 --report-interval=5 --oltp-skip-trx=on --oltp-read-only=off --rand-init=on --max-requests=0 --max-time=300 --num-threads=100 cleanup;
    ```


**Test read-only performance**

1.  Run prepare command.

    ```
    sysbench --test=./tests/db/oltp.lua --mysql-host=127.0.0.1--mysql-port=3001--mysql-user=abc --mysql-password=abc123456 --mysql-db=testdb --oltp-tables-count=10--oltp-table-size=500000--report-interval=5--oltp-skip-trx=on --oltp-read-only=on --rand-init=on --max-requests=0--max-time=300--num-threads=100 prepare;
    ```

2.  Run run command.

    ```
    sysbench --test=./tests/db/oltp.lua --mysql-host=127.0.0.1 --mysql-port=3001 --mysql-user=abc --mysql-password=abc123456 --mysql-db=testdb --oltp-tables-count=10 --oltp-table-size=500000 --report-interval=5 --oltp-skip-trx=on --oltp-read-only=on --rand-init=on --max-requests=0 --max-time=300 --num-threads=100 run;
    ```

3.  Run cleanup command.

    ```
    sysbench --test=./tests/db/oltp.lua --mysql-host=127.0.0.1 --mysql-port=3001 --mysql-user=abc --mysql-password=abc123456 --mysql-db=testdb --oltp-tables-count=10 --oltp-table-size=500000 --report-interval=5 --oltp-skip-trx=on --oltp-read-only=on --rand-init=on --max-requests=0 --max-time=300 --num-threads=100 cleanup;
    ```


