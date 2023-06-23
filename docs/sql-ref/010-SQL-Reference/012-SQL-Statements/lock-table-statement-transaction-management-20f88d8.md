<!-- loio20f88d8d75191014a51abbaa4e3d36cb -->

# LOCK TABLE Statement \(Transaction Management\)

Acquires an exclusive lock for a table.



<a name="loio20f88d8d75191014a51abbaa4e3d36cb__sql_lock_table_1sql_lock_table_syntax"/>

## Syntax

```
LOCK TABLE <table_name> 
 [ PARTITION <partition_id> ]   
 IN { EXCLUSIVE | INTENTIONAL EXCLUSIVE } MODE 
 [ <wait_nowait> ]
```



<a name="loio20f88d8d75191014a51abbaa4e3d36cb__sql_lock_table_1sql_lock_table_syntax_elements"/>

## Syntax Elements


<dl>
<dt><b>

*<table\_name\>*

</b></dt>
<dd>

Specifies the table to lock, with the optional schema name.

```
<table_name> ::= [<schema_name>.]<identifier>

<schema_name> ::= <unicode_name>
```



</dd><dt><b>

*<partition\_id\>*

</b></dt>
<dd>

Specifies the logical partition ID of the partition to lock. Specifying the PARTITION clause allows for parallel table optimizations such as delta merge operations. Without the PARTITION clause, these optimizations are not possible.

```
<partition_id> ::= <unsigned_integer>
```



</dd><dt><b>

EXCLUSIVE

</b></dt>
<dd>

Locks the table in EXCLUSIVE mode. EXCLUSIVE locks are acquired explicitly by LOCK TABLE, but are also acquired implicitly by DDL commands. EXCLUSIVE locks have the following characteristics:

-   The transaction that holds the lock can read and write to the table. All other transactions can read from the table but cannot write to it.

-   When a table has an EXCLUSIVE lock on it, all other lock requests by other transactions are blocked.

-   The database releases acquired locks at the end of the transaction.




</dd><dt><b>

INTENTIONAL EXCLUSIVE

</b></dt>
<dd>

Locks the table in INTENTIONAL EXCLUSIVE mode. However, INTENTIONAL EXCLUSIVE locks are only acquired by DML commands; use EXCLUSIVE mode instead. The description for INTENTIONAL EXCLUSIVE locks \(acquired implicitly by DML commands **only**\) is being provided here to explain the behavioral differences between the two different locks that are used in the database.

-   Multiple transactions can acquire an INTENTIONAL EXCLUSIVE lock.

-   When a table has an INTENTIONAL EXCLUSIVE lock on it, incoming EXCLUSIVE lock requests for the table by other transactions are blocked, whereas other INTENTIONAL EXCLUSIVE locks are allowed.

-   The database releases acquired locks at the end of the transaction.




</dd><dt><b>

*<wait\_nowait\>*

</b></dt>
<dd>

Specifies when to return an error if the table lock could not be acquired.

```
<wait_nowait> ::= WAIT <unsigned_integer> | NOWAIT 
```

If WAIT *<unsigned\_integer\>* is specified, then the statement waits up to the specified number of seconds for the lock. If the statement fails to acquire a lock after waiting, then it returns an error message indicating a timeout. If NOWAIT is specified, and the statement fails to acquire a table lock, then an error is returned indicating that the resource is busy. WAIT 0 is equivalent to NOWAIT.

When a timeout error is returned, the current transaction is not rolled back.

If *<wait\_nowait\>* is not specified, then the default behavior reflects the lock\_wait\_timeout transaction timeout setting located in `indexserver.ini`.



</dd>
</dl>



<a name="loio20f88d8d75191014a51abbaa4e3d36cb__sql_lock_table_1sql_lock_table_description"/>

## Description

LOCK TABLE acquires a lock for a table.

If EXCLUSIVE is specified and there are views that reference the table, then the LOCK TABLE statement also attempts to lock the views in exclusive mode so that new transactions cannot hold locks on any dependent views. If all of the view locks cannot be acquired at that time, then the statement returns a non-zero SQLCODE even though the table itself is locked. Schema locks are only released upon the COMMIT or ROLLBACK of a transaction.



<a name="loio20f88d8d75191014a51abbaa4e3d36cb__sql_lock_table_1sql_lock_table_example"/>

## Example

The following statements create a table A, and acquire an exclusive lock on it:

```
CREATE ROW TABLE A (A INT PRIMARY KEY, B INT);
LOCK TABLE A IN EXCLUSIVE MODE;
```

The following statement attempts to acquire an exclusive lock for table A, and specifies that an error should be returned if the lock cannot be immediately obtained.

```
LOCK TABLE A IN EXCLUSIVE MODE NOWAIT;
```

The following statements create a partitioned table PART\_A, and acquire an exlusive lock on partition 1:

```
CREATE COLUMN TABLE PART_A (A INT) PARTITION BY HASH(A) PARTITIONS 3;
LOCK TABLE PART_A PARTITION (1) IN EXCLUSIVE MODE;
```

**Related Information**  


[Introduction to SQL](../introduction-to-sql-209f502.md "This chapter describes the SAP HANA database implementation of Structured Query Language (SQL).")

[M\_OBJECT\_LOCKS System View](../../020-System-Views-Reference/022-Monitoring-Views/m-object-locks-system-view-20b66f9.md "Provides the status of currently acquired locks on objects with detailed information such as lock acquisition time and lock mode.")

