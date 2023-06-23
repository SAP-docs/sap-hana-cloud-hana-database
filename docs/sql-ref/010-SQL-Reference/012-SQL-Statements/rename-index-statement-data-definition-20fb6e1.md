<!-- loio20fb6e10751910148b45cefcb6294342 -->

# RENAME INDEX Statement \(Data Definition\)

Changes the name of an index.



<a name="loio20fb6e10751910148b45cefcb6294342__sql_rename_index_1sql_rename_index_syntax"/>

## Syntax

```
RENAME INDEX <current_index_name> TO <new_index_name>
```



<a name="loio20fb6e10751910148b45cefcb6294342__sql_rename_index_1sql_rename_index_syntax_elements"/>

## Syntax Elements


<dl>
<dt><b>

*<current\_index\_name\>*

</b></dt>
<dd>

Specifies the current index name with an optional schema name.

```
<current_index_name> ::= [<schema_name>.]<identifier>

<schema_name> ::= <unicode_name>
```



</dd><dt><b>

*<new\_index\_name\>*

</b></dt>
<dd>

Specifies the new index name.

```
<new_index_name> ::= <identifier>
```



</dd>
</dl>



<a name="loio20fb6e10751910148b45cefcb6294342__sql_rename_index_1sql_rename_index_description"/>

## Description

The RENAME INDEX statement changes the name of an index.



<a name="loio20fb6e10751910148b45cefcb6294342__sql_rename_index_1sql_rename_index_examples"/>

## Example

Create Table B and then index idx on column B of table B.

```
CREATE ROW TABLE B (A INT PRIMARY KEY, B INT);
 CREATE INDEX idx on B(B);
```

Show the list of index names on table B by using the INDEXES system table.

```
SELECT INDEX_NAME FROM INDEXES WHERE SCHEMA_NAME = CURRENT_SCHEMA AND TABLE_NAME = 'B';
```

Rename index idx to new\_idx.

```
RENAME INDEX idx TO new_idx;
```

Show a list of index names on table B after the renaming has occurred.

```
SELECT INDEX_NAME FROM INDEXES WHERE SCHEMA_NAME = CURRENT_SCHEMA AND TABLE_NAME = 'B';
```

**Related Information**  


[INDEXES System View](../../020-System-Views-Reference/021-System-Views/indexes-system-view-20a7044.md "Provides information about indexes on tables.")

[INDEX\_COLUMNS System View](../../020-System-Views-Reference/021-System-Views/index-columns-system-view-20a6a57.md "Provides information about index columns.")

