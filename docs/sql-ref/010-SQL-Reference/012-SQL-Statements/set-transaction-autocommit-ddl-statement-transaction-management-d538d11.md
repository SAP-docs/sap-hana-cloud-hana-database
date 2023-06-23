<!-- loiod538d11053bd4f3f847ec5ce817a3d4c -->

# SET TRANSACTION AUTOCOMMIT DDL Statement \(Transaction Management\)

Specifies the auto commit property for DDL statements specific to the session.



## Syntax

```
SET TRANSACTION AUTOCOMMIT DDL { ON | OFF }
```



## Description

The default setting for this command is ON. A user can specify the `AUTOCOMMIT` property for DDL statements specific to the session. If the `AUTOCOMMIT` property is enabled, then the transaction automatically commits after executing each DDL statement. Conversely, the transaction commits only after executing a `COMMIT` statement, allowing for the rollback of DDL statements.

Executing this command results in an implicit commit.

Certain DDL cases do not impact rollback behavior. For instance, failed DDL due to syntax checking errors or non-existent object references are deemed as 'DDL not executed'. These scenarios do not allow the transaction to fully roll back in the event of another failure within the transaction.

The support for DDL rollbacks across various table types is as follows:

-   Column, history column and row table: Rollbacks on DDL and DML statements are supported.

-   Global temporary tables and global temporary column tables: Rollbacks on DDL are supported, however, rollbacks on DML, including TRUNCATE TABLE, for global temporary column tables are not supported.

-   Local temporary tables and local temporary column tables: Rollbacks on both DDL and DML are supported.

-   No logging column table: Rollbacks on DDL are not supported, but rollbacks on DML are supported.


Rollbacks on the following DDL are not supported:

-   ALTER TABLE \{SET | UNSET\} ROW ORDER

-   ALTER TABLE to enable, disable client-side encryption or to change column encryption keys

-   \{CREATE | ALTER | DROP\} ADAPTER

-   \{CREATE | ALTER | DROP\} AGENT


Before attempting to execute `SET TRANSACTION AUTOCOMMIT DDL OFF`, ensure that you are using an `AUTOCOMMIT`-disabled session.



## Example

Turn off `DDL AUTOCOMMIT` mode.

```
SET TRANSACTION AUTOCOMMIT DDL OFF;
```

Create a table T and insert two rows into it.

```
CREATE ROW TABLE T (KEY INT PRIMARY KEY, VAL INT);
INSERT INTO T VALUES (1, 1);
INSERT INTO T VALUES (2, 2);
```

Commit the current transaction.

```
COMMIT;
```

Add a new column VAL2 to table T and insert a row.

```
ALTER TABLE T ADD (VAL2 INT);
INSERT INTO T VALUES (3, 3, 3);
```

Roll back the current transaction.

```
ROLLBACK;
```

Select the data in table T and get two rows with two columns.

```
SELECT * FROM T;
```

