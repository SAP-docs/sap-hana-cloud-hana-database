<!-- loio20d44b4175191014a940afff4b47c7ea -->

# CREATE INDEX Statement \(Data Definition\)

Creates an index on a table column.



<a name="loio20d44b4175191014a940afff4b47c7ea__sql_create_index_1sql_create_index_syntax"/>

## Syntax

```
CREATE [ <index_type> ] INDEX <index_name> ON <table_name>
   ( <column_name_order_entry>[, <column_name_order_entry> [,...]) 
   [ <global_index_order> ] 
   [ <fillfactor> ] 
   [ NOWAIT ] 
   [ ONLINE ]  
   [ <load_unit> ]
```



<a name="loio20d44b4175191014a940afff4b47c7ea__sql_create_index_1sql_create_index_syntax_elements"/>

## Syntax Elements


<dl>
<dt><b>

*<index\_type\>*

</b></dt>
<dd>

Defines the type of index to create.

```
<index_type> ::= 
 UNIQUE 
 | [ UNIQUE ] <rs_tree_type_index> 
 | [ UNIQUE ] <cs_inverted_type_index>
```

When the index type \(*<rs\_tree\_type\_index\>* or *<cs\_inverted\_type\_index\>*\) is omitted, the database server chooses the appropriate type by considering the table type and the column data type.

'rs\_' and 'cs\_' at the beginning of the specification types indicate which type of table the specification corresponds to \(row store and column store, respectively\). If you mistakenly specify a row store index type and the table is a column store table, then the specification is ignored and the index is created as INVERTED INDIVIDUAL for a unique index or INVERTED VALUE for a non-unique index. If you mistakenly specify a column store index type and the table is a row store table, an error is returned.


<dl>
<dt><b>

UNIQUE

</b></dt>
<dd>

Specifies that the index must have unique values. The optional *<rs\_tree\_type\_index\>* specification is only applicable to row store tables.

A composite unique key enables the specification of multiple columns as a unique key. With a unique constraint, multiple rows cannot have the same value in the same column.

A UNIQUE column can contain multiple NULL values.



</dd><dt><b>

*<rs\_tree\_type\_index\>*

</b></dt>
<dd>

Specifies the tree type for the index. Tree type specification is only applicable to row store tables.

```
<rs_tree_type_index> ::= { BTREE | CPBTREE }
```


<dl>
<dt><b>

CPBTREE

</b></dt>
<dd>

Specifies a CPB+-tree index for row store tables. CPB+-tree stands for Compressed Prefix B+-Tree, which is based on pkB-tree. CPB+-tree is a very small index because it uses 'partial key' that is only part of full key in index nodes. CPB+-tree shows better performance than B+-Tree for larger keys. Specify this type of tree for the following scenarios:

-   for character string types
-   for binary string types
-   for decimal types
-   when the constraint is a composite key
-   when the constraint is a non-unique constraint



</dd><dt><b>

BTREE

</b></dt>
<dd>

Specifies a B+-tree index. B+-tree indexes maintain sorted data, which performs efficient insertion, deletion, and search of records. Specify this type of tree for scenarios not described for CPBTREE.



</dd>
</dl>



</dd><dt><b>

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



</dd>
</dl>


<dl>
<dt><b>

*<index\_name\>*

</b></dt>
<dd>

Specifies the name of the index to be created, with optional schema name.

```
<index_name> ::= [ <schema_name>.]<identifier>

<schema_name> ::= <identifier>
```



</dd><dt><b>

*<column\_name\_order\_entry\>*

</b></dt>
<dd>

Specifies the columns to be used in the index, with an optional ordering.

```
<column_name_order_entry> ::= <column_name> [ <column_order> ]
```



</dd><dt><b>

*<column\_order\>*

</b></dt>
<dd>

Specifies whether the column index should be created in ascending or descending order. The default ordering is ASC.

```
<column_order> ::= { ASC | DESC }
```



</dd><dt><b>

*<global\_index\_order\>*

</b></dt>
<dd>

Specifies the index ordering for all columns in the index.

```
<global_index_order> ::= { ASC | DESC }
```

*<column\_order\>* and *<global\_index\_order\>* cannot be used when *<global\_index\_order\>* is used.



</dd><dt><b>

*<fillfactor\>*

</b></dt>
<dd>

Specifies how each node of a new index is filled. It is a percentage value of integer from 50 to 100, and the default value is 90.

```
<fillfactor> ::= FILLFACTOR <unsigned_integer>
```



</dd><dt><b>

NOWAIT

</b></dt>
<dd>

Specifies that the CREATE INDEX statement returns an error immediately in case a table lock cannot be acquired.



</dd><dt><b>

ONLINE

</b></dt>
<dd>

For column store tables, the ONLINE keyword allows the creation of the index without serializing with concurrent DML operations. This is only supported for non-replicated, non-history tables. Creating an index in a supported case results in an operation that acquires a shared table lock. In the unsupported cases, or when the ONLINE keyword is omitted, an exclusive table lock is only taken for a short time at the beginning and end of the CREATE INDEX operation; during the rest of the CREATE INDEX operation, shared table lock is taken, which allows concurrent read and DML access operations but blocks concurrent DDL operations.

For row store tables, you can specify ONLINE to not place an exclusive lock on the table and enable read access during index creation; if ONLINE is not specified neither concurrent read nor DML operations are allowed during index creation.

Note that the ONLINE keyword affects SQL table locks, but not other internal locks. Therefore a DML write or read operation could be blocked for some time even if the ONLINE keyword is specified. This blocking time is typically shorter than the complete index creation time, but especially in the case of a single column index creation it could even last for the complete index creation time.



</dd><dt><b>

*<load\_unit\>*

</b></dt>
<dd>

Specifies the load unit for the index. This clause is supported only for multi-column INVERTED HASH and INVERTED VALUE indexes on column store tables.

```
<load_unit> ::= { COLUMN | PAGE } LOADABLE
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



</dd>
</dl>

Column store inverted indexes can be as large as the column itself. The *<load\_unit\>* setting of an index impacts the memory footprint of the index. For example, a PAGE LOADABLE index consumes much less memory, but may degrade performance slightly. This may be suitable for an index that is not frequently used. When performance is the priority, you may want to set the index to COLUMN LOADABLE, assuming the memory overhead is acceptable.

The load unit for an index is noted in the LOAD\_UNIT column of the INDEXES system view.



</dd>
</dl>



<a name="loio20d44b4175191014a940afff4b47c7ea__sql_create_index_1sql_create_index_description"/>

## Description

When column data types are character string types, binary string types, decimal types, or when the constraint is a composite key, or a non-unique constraint, the default index type is CPBTREE. In other cases BTREE is used. If neither BTREE nor CPBTREE keyword is specified, then the SAP HANA database chooses the appropriate index type.

For row store tables, when column data types are character string types, binary string types, decimal types, or when the constraint is a composite key, or a non-unique constraint, the default index type is CPBTREE. In other cases BTREE is used. If neither BTREE nor CPBTREE keyword is specified, then the SAP HANA database chooses the appropriate index type.

For column store tables, the default index type is INVERTED INDIVIDUAL for unique indexes and INVERTED VALUE for non-unique indexes.

To determine the maximum index key size, check the MAXIMUM\_SIZE\_OF\_KEY\_IN\_INDEX value in the M\_SYSTEM\_LIMITS system view.



<a name="loio20d44b4175191014a940afff4b47c7ea__section_fpp_p3v_rsb"/>

## Permissions

You must have the INDEX object privilege on the affected table to create an index.



<a name="loio20d44b4175191014a940afff4b47c7ea__sql_create_index_1sql_create_index_examples"/>

## Example


<dl>
<dt><b>

Row store index example

</b></dt>
<dd>

Create a row store table `t`, and then add the index `idx` on column `b` of table `t` with ascending order.

```
CREATE ROW TABLE t (a INT, b NVARCHAR(10), c NVARCHAR(20)); 
CREATE INDEX idx ON t(b);
```

Create a CPBTREE index `idx1` on column `a` of table `t` with ascending order and column `b` with descending order.

```
CREATE CPBTREE INDEX idx1 ON t(a, b DESC);
```

Create a CPBTREE index `idx2` on column `a` and `c` of table `t` with descending order.

```
CREATE INDEX idx2 ON t(a, c) DESC;
```

Create a UNIQUE CPBTREE index `idx3` on column `b` and `c` of table `t` with ascending order.

```
CREATE UNIQUE INDEX idx3 ON t(b, c);
```

Create a UNIQUE BTREE index `idx4` on column `a` of table `t` with ascending order.

```
CREATE UNIQUE INDEX idx4 ON t(a);
```



</dd><dt><b>

Column store index example

</b></dt>
<dd>

Create table s, and then add the index idx10 on column b of table s.

```
CREATE TABLE s (a INT, b NVARCHAR(10), c NVARCHAR(20));
CREATE INDEX idx10 ON s(b);
```

Create an INVERTED VALUE index idx11 on column a of table s.

```
CREATE INVERTED VALUE INDEX idx11 ON s(a, b);
```

Create a UNIQUE INVERTED VALUE index idx12 on column a and c of table s and set the load unit type to PAGE LOADABLE.

```
CREATE UNIQUE INVERTED VALUE INDEX idx12 ON s(a, c) PAGE LOADABLE;
```

Create a UNIQUE INVERTED INDIVIDUAL index idx13 on column b and c of table s.

```
CREATE UNIQUE INDEX idx13 ON s(b, c);
```

The base columns b and c allow NULL values. The following inserts are possible:

```
INSERT INTO s VALUES(0, 1, NULL);
INSERT INTO s VALUES(1, NULL, NULL);
INSERT INTO s VALUES(2, NULL, NULL);
```

But the following insert will generate a unique constraint violation error:

```
INSERT INTO s VALUES(3, 1, NULL);
```



</dd>
</dl>

**Related Information**  


[ALTER INDEX Statement \(Data Definition\)](alter-index-statement-data-definition-20d014b.md "Alters an index.")

[INDEXES System View](../../020-System-Views-Reference/021-System-Views/indexes-system-view-20a7044.md "Provides information about indexes on tables.")

[INDEX\_COLUMNS System View](../../020-System-Views-Reference/021-System-Views/index-columns-system-view-20a6a57.md "Provides information about index columns.")

[SAP HANA Cloud Configuration Parameter Reference](https://help.sap.com/viewer/138dcf7d779543608917a2307a6115f2/2023_2_QRC/en-US/4b4d88980622427ab2d6ca8c05448166.html "Reference documentation for public configuration parameters in SAP HANA Cloud.") :arrow_upper_right:

[M\_SYSTEM\_LIMITS System View](../../020-System-Views-Reference/022-Monitoring-Views/m-system-limits-system-view-20c6023.md "Provides system limit information.")

[Managing Indexes](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2023_2_QRC/en-US/713e65a10d55404b9ac503bb7b4c735a.html "For multi-column indexes in the column store you can set a default index type.") :arrow_upper_right:

