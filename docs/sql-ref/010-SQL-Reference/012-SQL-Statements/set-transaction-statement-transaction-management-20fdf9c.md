<!-- loio20fdf9cb75191014b85aaa9dec841291 -->

# SET TRANSACTION Statement \(Transaction Management\)

Sets transaction parameters.



<a name="loio20fdf9cb75191014b85aaa9dec841291__sql_set_transaction_1sql_set_transaction_syntax"/>

## Syntax

```
SET TRANSACTION { 
 <isolation_level> 
 | <transaction_access_mode> 
 | <transaction_lock_wait_timeout>
 | <ddl_on_off>
 }
```



<a name="loio20fdf9cb75191014b85aaa9dec841291__sql_set_transaction_1sql_set_transaction_syntax_elements"/>

## Syntax Elements


<dl>
<dt><b>

*<isolation\_level\>*

</b></dt>
<dd>

Sets the statement level read consistency of the data in the database.

```
<isolation_level> ::= ISOLATION LEVEL <level>

<level> ::= 
 READ COMMITTED 
 | REPEATABLE READ 
 | SERIALIZABLE
```

If *<isolation\_level\>* is omitted, then the default is READ COMMITTED.

The READ COMMITTED isolation level provides statement-level read consistency during a transaction. Each statement in a transaction uses the committed state of the data in the database as the execution of the statement begins. This means that each statement in the same transaction may see varying snapshots of the data in the database as they are executed. This is because data can be committed during the transaction.

The REPEATABLE READ and SERIALIZABLE isolation levels provide transaction level snapshot isolation; that is, all statements of a transaction use the same snapshot of the database data. This snapshot contains all changes that were committed at the time the transaction started along with the changes made by the transaction itself.

REPEATABLE READ guarantees that the data the transaction reads is not being modified by another transaction and will not change unless the reading transaction modifies it and commits the change.

SERIALIZABLE guarantees maximum data integrity, since only one transaction run as a single serial operation can both read and modify the data at a time. Other transactions can access the data only after the serializable transaction has committed or rolled back. SERIALIZABLE can impact overall performance, since transactions are serialized.



</dd><dt><b>

*<transaction\_access\_mode\>*

</b></dt>
<dd>

Controls whether a transaction can modify data during execution. If transaction\_access\_mode is not set, then the default is READ WRITE.

```
<transaction_access_mode> ::= READ ONLY | READ WRITE
```

When READ ONLY access mode is set, only read operations with SELECT statements are allowed. This setting remains in effect for the session, even after a COMMIT or ROLLBACK. An exception is thrown if update or insert operations are attempted while in this mode.

When READ WRITE access mode is set, statements within a transaction can freely read or make changes to the database data as required.



</dd><dt><b>

*<transaction\_lock\_wait\_timeout\>*

</b></dt>
<dd>

Configures a time limit for how long TABLE LOCK or RECORD LOCK waits.

```
<transaction_lock_wait_timeout> ::= LOCK WAIT TIMEOUT <unsigned_integer>
```

The default value of *<transaction\_lock\_wait\_timeout\>* is specified in `indexserver.ini`, in the transaction section. The value must specify the number of milliseconds and be between 0 and 2147483647. If a lock is not acquired before the timeout period expires, then the executing statement returns the error code 131. The transaction is rolled back by *<transaction\_lock\_wait\_timeout\>*.



</dd><dt><b>

*<ddl\_on\_off\>*

</b></dt>
<dd>

Turns transaction DDL on or off for the session.

```
<ddl_on_off> ::= DDL { ON | OFF }
```

When DDL OFF is specified, the session blocks all DDL executions. Also, the TRUNCATE statement works for local temporary tables but not with any other table type. The default behavior is DDL ON.

DCL statements like GRANT are threaded as DDL. Therefore, DCL statements are blocked when DDL blocking is enabled.

Query the value of M\_SESSION\_CONTEXT.DDL\_ENABLED to determine the current setting for the session.



</dd>
</dl>



<a name="loio20fdf9cb75191014b85aaa9dec841291__sql_set_transaction_1sql_set_transaction_description"/>

## Description

The SAP HANA database uses multi-version concurrency control \(MVCC\) to ensure consistent read operations. Concurrent read operations have a consistent view of the database data without blocking concurrent write operations. Updates are implemented by inserting new versions of data and not by overwriting existing records.

The isolation level specified determines the lock operation type that is used. The system supports both statement level snapshot isolation and transaction level snapshot isolation.

For statement snapshot isolation use level READ COMMITTED. For transaction snapshot isolation use REPEATABLE READ or SERIALIZABLE.

During a transaction when rows are inserted, updated, or deleted, the system sets exclusive locks on the affected rows for the duration of the transaction. The system also sets shared locks on the affected tables for the duration of the transaction. This guarantees that the table is not dropped or altered while rows of the table are being updated. The database releases these locks at the end of the transaction.

Reading a row does not set any locks on either tables or rows within the database regardless of the isolation level used.

Data Definition Language \(DDL\) statements \(CREATE TABLE, DROP TABLE, CREATE VIEW, and so on\) always take an instantaneous effect on following SQL statements regardless of the transaction isolation level being used. For an example of this behavior, consider the following sequence:

1.  A long running SERIALIZABLE isolation transaction begins operating on Table C.

2.  From outside the transaction some DDL is executed which adds a new column to Table C.

3.  From within the SERIALIZABLE isolation transaction the new column is accessible as soon as the DDL statement completes. This access occurs regardless of the isolation level of the transaction.




<a name="loio20fdf9cb75191014b85aaa9dec841291__sql_set_transaction_1sql_set_transaction_examples"/>

## Example

The following example sets the transaction isolation level to READ COMMITTED to provide statement level read consistency during the current transaction.

```
SET TRANSACTION ISOLATION LEVEL READ COMMITTED;
```

The following example sets the transaction lock timeout to 1 minute. \(1 second = 1000 milliseconds\).

```
SET TRANSACTION LOCK WAIT TIMEOUT 60000;
```

The following example turns DDL off for the session and then turns it back on again:

```
CREATE TABLE Table0 (A INT);
SET TRANSACTION DDL OFF; --> Turns off DDL for the session
CREATE TABLE Table1 (A INT); --> DDL operation fails and returns and error indicating that DDL is disabled in the session
INSERT INTO Table0 VALUES (0); --> DML operation succeeds
SELECT VALUE FROM M_SESSION_CONTEXT WHERE KEY='DDL_ENABLED'; --> This returns FALSE for DDL_ENABLED.
SET TRANSACTION DDL ON; --> Turns DDL back on for the session
```

