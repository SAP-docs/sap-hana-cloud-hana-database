<!-- loio20d6f4e575191014b333904458242bd7 -->

# DROP INDEX Statement \(Data Definition\)

Removes an index.



<a name="loio20d6f4e575191014b333904458242bd7__sql_drop_index_1sql_drop_index_syntax"/>

## Syntax

```
DROP INDEX <index_name> [ ONLINE [ PREFERRED ] ]
```



<a name="loio20d6f4e575191014b333904458242bd7__sql_drop_index_1sql_drop_index_syntax_elements"/>

## Syntax Elements


<dl>
<dt><b>

*<index\_name\>*

</b></dt>
<dd>

Drops the specified index, with the optional schema name.

```
<index_name> ::= [<schema_name>.]<identifier>

<schema_name> ::= <unicode_name>
```



</dd><dt><b>

ONLINE \[ PREFERRED \]

</b></dt>
<dd>

Allows the dropping of the index without serializing with concurrent DML operations. ONLINE is only supported for column-store, non-replicated tables. The drop results in an operation that only acquires a shared table lock.

When PREFERRED is specified, if ONLINE execution is not supported, then a SQL warning message appears, and the drop index operation executes in table x-lock mode.



</dd>
</dl>



<a name="loio20d6f4e575191014b333904458242bd7__sql_drop_index_1sql_drop_index_description"/>

## Description

The DROP INDEX statement removes an index.



<a name="loio20d6f4e575191014b333904458242bd7__section_fpp_p3v_rsb"/>

## Permissions

You must have the INDEX object privilege on the affected table to drop an index.



<a name="loio20d6f4e575191014b333904458242bd7__sql_drop_index_1sql_drop_index_examples"/>

## Example

Create table A and then add an index, i, on column b of table A.

```
CREATE ROW TABLE A (a INT, b NVARCHAR(10), c NVARCHAR(20));
 CREATE INDEX i ON A(b);
```

Drop index i.

```
DROP INDEX i;
```

**Related Information**  


[INDEXES System View](../../020-System-Views-Reference/021-System-Views/indexes-system-view-20a7044.md "Provides information about indexes on tables.")

[INDEX\_COLUMNS System View](../../020-System-Views-Reference/021-System-Views/index-columns-system-view-20a6a57.md "Provides information about index columns.")

