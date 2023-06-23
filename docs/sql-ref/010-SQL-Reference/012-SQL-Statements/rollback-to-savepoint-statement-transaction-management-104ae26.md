<!-- loio104ae26787e24bddbda2953c0397b6e8 -->

# ROLLBACK TO SAVEPOINT Statement \(Transaction Management\)

Rolls back a transaction to the named savepoint without terminating the transaction.



<a name="loio104ae26787e24bddbda2953c0397b6e8__sql_rollback_1sql_rollback_syntax"/>

## Syntax

```
ROLLBACK TO SAVEPOINT <savepoint_name>
```



<a name="loio104ae26787e24bddbda2953c0397b6e8__section_ynn_4s2_wgb"/>

## Syntax Elements


<dl>
<dt><b>

*<savepoint\_name\>*

</b></dt>
<dd>

Specifies the case-insensitive identifier that was specified on a SAVEPOINT statement within the current transaction.



</dd>
</dl>



<a name="loio104ae26787e24bddbda2953c0397b6e8__sql_rollback_1sql_rollback_description"/>

## Description

The ROLLBACK TO SAVEPOINT statement undoes any changes that have been made since the SAVEPONIT was established without terminating the current transaction. Changes made before the SAVEPOINT was set are not undone. Savepoints set after that savepoint to which you rolled back are erased, but the rollback savepoint remains.

The savepoint name specified must exist within the current transaction.

A ROLLBACK or COMMIT erases all savepoints.

The *<savepoint\_name\>* identifier can be used in a SAVEPOINT or RELEASE SAVEPOINT statement.



<a name="loio104ae26787e24bddbda2953c0397b6e8__section_jzb_dx3_chb"/>

## Examples

Create a table T.

```
CREATE ROW TABLE T (KEY INT PRIMARY KEY, VAL INT);
```

Insert two rows into table T.

```
INSERT INTO T VALUES (1, 1);
 INSERT INTO T VALUES (2, 2);
```

Set a savepoint.

```
SAVEPOINT savepoint1;
```

Insert a row into table T.

```
INSERT INTO T VALUES (3, 3);
```

Roll back the current transaction to savepoint1.

```
ROLLBACK TO SAVEPOINT savepoint1;
```

Select the data in table T.

```
SELECT * FROM T;
```

The SELECT command above rows one and two, but not three.

**Related Information**  


[RELEASE SAVEPOINT Statement \(Transaction Management\)](release-savepoint-statement-transaction-management-445eb4d.md "Releases a specified savepoint name.")

[SAVEPOINT Statement \(Transaction Management\)](savepoint-statement-transaction-management-cd4172a.md "Defines a location to which a transaction can return if part of the transaction is conditionally canceled.")

