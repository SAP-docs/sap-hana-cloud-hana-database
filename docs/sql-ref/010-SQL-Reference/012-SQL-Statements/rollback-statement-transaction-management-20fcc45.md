<!-- loio20fcc453751910149557fc90fe781449 -->

# ROLLBACK Statement \(Transaction Management\)

Changes made during the current transaction are reverted and current database session is set to an idle state.



<a name="loio20fcc453751910149557fc90fe781449__sql_rollback_1sql_rollback_syntax"/>

## Syntax

```
ROLLBACK
```



<a name="loio20fcc453751910149557fc90fe781449__sql_rollback_1sql_rollback_description"/>

## Description

The SAP HANA database supports transactional consistency which guarantees that a transaction is completely applied to the system or disposed. During a transaction, data manipulation language \(DML\) modifications to the database can be explicitly reverted via ROLLBACK command. After ROLLBACK is issued, changes made during the current transaction are reverted and current database session is set to an idle state. ROLLBACK only works with an autocommit disabled session.

If you attempt to use the ROLLBACK statements in an autocommit enabled session, then nothing occurs as transactions are automatically committed to the database.



<a name="loio20fcc453751910149557fc90fe781449__sql_rollback_1sql_rollback_example"/>

## Example

Before attempting to execute the example below, ensure that you are using an autocommit disabled session.

Create a table T1.

```
CREATE ROW TABLE T1 (KEY INT PRIMARY KEY, VAL INT);
```

Insert three rows into table T1.

```
INSERT INTO T1 VALUES (1, 1);
 INSERT INTO T1 VALUES (2, 2);
 INSERT INTO T1 VALUES (3, 3);
```

Roll back the current transaction.

```
ROLLBACK;
```

Select the data in table T1.

```
SELECT * FROM T1;
```

The SELECT command above returns an empty table.

**Related Information**  


[SET TRANSACTION AUTOCOMMIT DDL Statement \(Transaction Management\)](set-transaction-autocommit-ddl-statement-transaction-management-d538d11.md "Specifies the auto commit property for DDL statements specific to the session.")

