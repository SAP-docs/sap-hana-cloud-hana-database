<!-- loiocd4172aead1e47e99f6599656887f343 -->

# SAVEPOINT Statement \(Transaction Management\)

Defines a location to which a transaction can return if part of the transaction is conditionally canceled.



<a name="loiocd4172aead1e47e99f6599656887f343__sql_rollback_1sql_rollback_syntax"/>

## Syntax

```
SAVEPOINT <savepoint_name>
```



<a name="loiocd4172aead1e47e99f6599656887f343__section_ynn_4s2_wgb"/>

## Syntax Elements


<dl>
<dt><b>

*<savepoint\_name\>*

</b></dt>
<dd>

Specifies a unique incase-sensitive identifier for the savepoint.



</dd>
</dl>



<a name="loiocd4172aead1e47e99f6599656887f343__sql_rollback_1sql_rollback_description"/>

## Description

Establish a savepoint within the current transaction.

The number of active savepoints for each transaction is unlimited. Savepoint names must be unique within a given transaction. If you create a second savepoint with the same identifier as an earlier savepoint, then the earlier savepoint is erased.

The *<savepoint\_name\>* identifier can be used in a RELEASE SAVEPOINT or ROLLBACK TO SAVEPOINT statement.

This statement should not be confused with the ALTER SYSTEM SAVEPOINT statement, which performs a database checkpoint, not a transactional checkpoint.



<a name="loiocd4172aead1e47e99f6599656887f343__section_kn5_5x3_chb"/>

## Examples

Create a SAVEPOINT named savepoint1.

```
SAVEPONT savepoint1;
```

**Related Information**  


[RELEASE SAVEPOINT Statement \(Transaction Management\)](release-savepoint-statement-transaction-management-445eb4d.md "Releases a specified savepoint name.")

[ROLLBACK TO SAVEPOINT Statement \(Transaction Management\)](rollback-to-savepoint-statement-transaction-management-104ae26.md "Rolls back a transaction to the named savepoint without terminating the transaction.")

[ALTER SYSTEM SAVEPOINT Statement \(System Management\)](alter-system-savepoint-statement-system-management-20d2b6e.md "Executes a database checkpoint on the persistence manager.")

