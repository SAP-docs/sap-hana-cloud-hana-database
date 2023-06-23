<!-- loio445eb4d2202f4f29b67e9874a3c9acfb -->

# RELEASE SAVEPOINT Statement \(Transaction Management\)

Releases a specified savepoint name.



<a name="loio445eb4d2202f4f29b67e9874a3c9acfb__sql_rollback_1sql_rollback_syntax"/>

## Syntax

```
RELEASE SAVEPOINT <savepoint_name>
```



<a name="loio445eb4d2202f4f29b67e9874a3c9acfb__section_ynn_4s2_wgb"/>

## Syntax Elements


<dl>
<dt><b>

*<savepoint\_name\>*

</b></dt>
<dd>

Specifies the case-insensitive identifier that was specified on a SAVEPOINT statement within the current transaction.



</dd>
</dl>



<a name="loio445eb4d2202f4f29b67e9874a3c9acfb__sql_rollback_1sql_rollback_description"/>

## Description

Releases an established savepoint within the current transaction. The savepoint name specified must exist for the current transaction.

The *<savepoint\_name\>* identifier can be used in a SAVEPOINT or ROLLBACK TO SAVEPOINT statement.



<a name="loio445eb4d2202f4f29b67e9874a3c9acfb__section_kn5_5x3_chb"/>

## Examples

Release a SAVEPOINT named savepoint1.

```
RELEASE SAVEPONT savepoint1;
```

**Related Information**  


[ROLLBACK TO SAVEPOINT Statement \(Transaction Management\)](rollback-to-savepoint-statement-transaction-management-104ae26.md "Rolls back a transaction to the named savepoint without terminating the transaction.")

[SAVEPOINT Statement \(Transaction Management\)](savepoint-statement-transaction-management-cd4172a.md "Defines a location to which a transaction can return if part of the transaction is conditionally canceled.")

