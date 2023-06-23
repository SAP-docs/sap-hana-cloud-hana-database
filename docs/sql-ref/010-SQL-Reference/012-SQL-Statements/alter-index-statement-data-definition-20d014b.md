<!-- loio20d014b575191014b66d8ef88f6a55f6 -->

# ALTER INDEX Statement \(Data Definition\)

Alters an index.



<a name="loio20d014b575191014b66d8ef88f6a55f6__sql_alter_index_1sql_alter_index_syntax"/>

## Syntax

```
ALTER INDEX <index_name> 
 { REBUILD
 | UNIQUE <cs_inverted_type_index>
 | <load_unit> }
```



<a name="loio20d014b575191014b66d8ef88f6a55f6__sql_alter_index_1xyz_elements"/>

## Syntax Elements


<dl>
<dt><b>

*<index\_name\>*

</b></dt>
<dd>

Specifies the name of the index to be rebuilt with an optional schema name.

```
<index_name> ::= [<schema_name>.]<identifier>

<schema_name> ::= <unicode_name>
```



</dd><dt><b>

REBUILD

</b></dt>
<dd>

Rebuilds the index.



</dd><dt><b>

UNIQUE *<cs\_inverted\_type\_index\>*

</b></dt>
<dd>

Changes the index type of a composite UNIQUE INVERTED index on a column store table.


<dl>
<dt><b>

*<cs\_inverted\_type\_index\>*

</b></dt>
<dd>

Specifies the inverted index type for column store tables. Inverted index types are only applicable to column store tables.

```
<cs_inverted_type_index> ::= INVERTED { HASH | VALUE | INDIVIDUAL }
```


<dl>
<dt><b>

INVERTED HASH

</b></dt>
<dd>

INVERTED HASH should not be used as a composite type in cases where range queries or similar queries on the composite keys are a significant part of the workload. In these cases, use INVERTED VALUE instead. This type of index is only available for composite unique constraints, which may be defined as a secondary unique index or primary key.



</dd><dt><b>

INVERTED VALUE

</b></dt>
<dd>

INVERTED VALUE is the default non-unique index type for column store tables.



</dd><dt><b>

INVERTED INDIVIDUAL

</b></dt>
<dd>

An INVERTED INDIVIDUAL index is a lightweight index type for column store tables with reduced memory footprint. The name INVERTED INDIVIDUAL reflects that internally only inverted indexes on individual columns are created \(that is, no concat attributes are created\). This type of index is only available for multi-column unique constraints, which may be defined as secondary unique index or primary key. INVERTED INDIVIDUAL is the default unique index type for column store tables.



</dd>
</dl>



</dd>
</dl>



</dd><dt><b>

*<load\_unit\>*

</b></dt>
<dd>

Changes the load unit for a composite inverted \(value or hash\) index on a column store table.

```
<load_unit> ::= { COLUMN | PAGE | DEFAULT } LOADABLE
```


<dl>
<dt><b>

COLUMN LOADABLE

</b></dt>
<dd>

The query results are loaded by column. This is the default for column store tables.



</dd><dt><b>

PAGE LOADABLE

</b></dt>
<dd>

The query results are loaded by page.



</dd><dt><b>

DEFAULT LOADABLE

</b></dt>
<dd>

If you specify DEFAULT, then there is no explicit preference for the load unit that is used when the results are loaded from the table. The index inherits the load unit setting from the first level above it \(if specified\): column, table, database. If there is no load unit setting to inherit, the default behavior is COLUMN LOADABLE.



</dd>
</dl>

Column store inverted indexes can be as large as the column itself. The *<load\_unit\>* setting of an index impacts the memory footprint of the index. For example, a PAGE LOADABLE index consumes much less memory, but may degrade performance slightly. This may be suitable for an index that is not frequently used. When performance is the priority, you may want to set the index to COLUMN LOADABLE, assuming the memory overhead is acceptable.

The load unit for an index is noted in the LOAD\_UNIT column of the INDEXES system view.



</dd>
</dl>



<a name="loio20d014b575191014b66d8ef88f6a55f6__sql_alter_index_1sql_alter_index_description"/>

## Description

Alters the specification for an existing index.



<a name="loio20d014b575191014b66d8ef88f6a55f6__section_fpp_p3v_rsb"/>

## Permissions

You must have the INDEX object privilege on the affected table to alter an index.



<a name="loio20d014b575191014b66d8ef88f6a55f6__sql_alter_index_1sql_alter_index_examples"/>

## Example

The following example creates table A1 and an INDEX\_1 on column b of table A1:

```
CREATE TABLE A1 (a INT, b NVARCHAR(10), c NVARCHAR(20));
 CREATE INDEX INDEX_1 ON A1(b);
```

The following example rebuilds INDEX\_1:

```
ALTER INDEX INDEX_1 REBUILD;
```

The following example alters INDEX\_1 to use a target index type INVERTED HASH:

```
ALTER INDEX INDEX_1 UNIQUE INVERTED HASH;
```

The following example changes the load unit type for the myIDX index to PAGE LOADABLE:

```
ALTER INDEX myIDX PAGE LOADABLE;
```

**Related Information**  


[CREATE INDEX Statement \(Data Definition\)](create-index-statement-data-definition-20d44b4.md "Creates an index on a table column.")

