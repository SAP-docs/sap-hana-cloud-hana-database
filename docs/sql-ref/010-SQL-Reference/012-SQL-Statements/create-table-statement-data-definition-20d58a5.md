<!-- loio20d58a5f75191014b2fe92141b7df228 -->

# CREATE TABLE Statement \(Data Definition\)

Creates a base or temporary table. See the CREATE VIRTUAL TABLE statement for creating virtual tables.



<a name="loio20d58a5f75191014b2fe92141b7df228__sql_create_table_syntax"/>

## Syntax

```
CREATE [ <table_type><table_name> | <replica_name> }
   <table_contents_source>
   [<system_versioning_spec>]
   [<application_time_period_configuration>]
   [<bi_temporal_table_spec>]
   [<with_association_clause>] 
   [<with_annotation_clause>]
   [<with_mask_clause>]        
   [<logging_option>] 
   [<auto_merge_option>]
   [<unload_priority_clause>]
   [<partition_clause>] 
   [<persistent_memory_spec_clause>] 
   [<group_option_list>]
   [<location_clause>] 
   [<replica_clause>]
   [<with_replica_list>] 
   [<global_temporary_option>] 
   [<unused_retention_period_option>] 
   [<record_commit_timestamp_clause>]            
   [<table_comment_string>]
   [<numa_node_preference_clause>]
   [<load_unit>]
   [<primary_key_update_clause>]
```



<a name="loio20d58a5f75191014b2fe92141b7df228__sql_create_table_syntax_elements"/>

## Syntax Elements


<dl>
<dt><b>

*<table\_type\>*

</b></dt>
<dd>

Defines the type of table to create.

```
<table_type> ::= 
 { ROW | [ COLUMN ] } TABLE
 |  ] { <temporary_table_type>
 | VIRTUAL TABLE

<temporary_table_type> ::= 
 GLOBAL TEMPORARY { [ ROW ] | COLUMN } TABLE
 | LOCAL TEMPORARY { [ ROW ] | COLUMN } TABLE
```

If neither ROW nor COLUMN is specified, the default ROW for temporary tables \(local and global\), and COLUMN for non temporary tables.


<dl>
<dt><b>

ROW and COLUMN TABLE

</b></dt>
<dd>

Creates a row or column table, respectively. If the majority of table access is through a large number of tables with only a few selected attributes, then use COLUMN-based storage. If the majority of table access involves selecting a few records with all attributes selected, then ROW-based storage is preferable. The SAP HANA database uses a combination of table types to enable storage and interpretation in both ROW and COLUMN forms.



</dd><dt><b>

*<temporary\_table\_type\>*

</b></dt>
<dd>

A simple comparison of the temporary table types is provided in this table. To learn more information about each type, see the descriptions found after the table.


<table>
<tr>
<th valign="top">

Characteristic

</th>
<th valign="top">

Global temp \(column\)

</th>
<th valign="top">

Global temp \(row\)

</th>
<th valign="top">

Local temp \(column\)

</th>
<th valign="top">

Local temp \(row\)

</th>
</tr>
<tr>
<td valign="top">

Metadata shared across sessions

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

Dropped after session terminates

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
</tr>
<tr>
<td valign="top">

Allows add or drop of primary key

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

Allows add or drop of identity column

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
</tr>
</table>



</dd><dt><b>

GLOBAL TEMPORARY ROW TABLE

</b></dt>
<dd>

Creates a global temporary row table and makes the table definition globally available while data is visible only to the current session. Metadata for a global temporary table persists and is shared across sessions. The data in a global temporary table is session-specific, meaning only the session owner of a global temporary table can insert, read, or truncate the data for the session. As well, data in a temporary table is automatically dropped when the session is terminated. You can drop a global temporary table, but only after you truncate the session-specific data.

Supported operations:

-   Create with or without a primary key
-   Add or drop a primary key
-   Add or drop an identity column
-   Add or drop unique constraint
-   Rename table
-   Add, alter, rename, or drop column
-   Truncate
-   Drop
-   Create or drop a view on a global temporary table
-   Create synonym
-   Select
-   Select into or insert
-   Delete
-   Update
-   Upsert or replace



</dd><dt><b>

GLOBAL TEMPORARY COLUMN TABLE

</b></dt>
<dd>

Creates a global temporary column table. The table definition becomes globally available, yet data visibility is confined to the current session.

Metadata for a global temporary table persists and is shared across multiple sessions. The data within a global temporary table is session-specific; only the session owner can insert, read, or truncate the data for that session. Additionally, data in a temporary table is automatically purged when the session concludes. A global temporary table can be dropped, but only after truncating the session-specific data.

Supported operations:

-   Create without a primary key
-   Truncate
-   Drop
-   Create or drop a view on a global temporary column table
-   Create synonym
-   Select
-   Select into or insert
-   Add, alter or drop column
-   Add or drop an identity column



</dd><dt><b>

LOCAL TEMPORARY ROW TABLE

</b></dt>
<dd>

Creates a local temporary row table, visible only to the current session.

Metadata exists for the duration of the session and is session specific, meaning only the session owner of the local temporary table can see it. The table is dropped at the end of the session.

Data in a local temporary row table is session specific, meaning only the session owner of the local temporary row table can insert, read, or truncate the data.

Primary keys are supported on LOCAL TEMPORARY ROW tables.

Supported operations:

-   Create with or without a primary key

-   Truncate

-   Drop

-   Select

-   Select into or insert

-   Delete

-   Update

-   Upsert or replace




</dd><dt><b>

LOCAL TEMPORARY COLUMN TABLE

</b></dt>
<dd>

Creates a local temporary column table, visible only to the current session.

Metadata exists for the duration of the session and is session-specific, meaning only the session owner of the local temporary column table can see. The table is dropped at the end of the session.

Data in a local temporary column table is session-specific, meaning only the session owner of the local temporary column table can insert, read, or truncate the data.

Supported operations:

-   Create without a primary key

-   Truncate

-   Drop

-   Select

-   Select into or insert

-   Delete
-   Update
-   Upsert or replace



</dd><dt><b>

VIRTUAL TABLE

</b></dt>
<dd>

Creates a virtual table based on an existing table/view inside a remote source.



</dd>
</dl>



</dd><dt><b>

*<table\_name\>*

</b></dt>
<dd>

Specifies a name for the table

```
<table_name> ::= [ <schema_name>.]<identifier>
```



</dd><dt><b>

*<replica\_name\>*

</b></dt>
<dd>

Specifies the schema and a name for the new replica. This clause is for use with creating a replica based on an existing source table \(CREATE TABLE...LIKE\). See [*<like\_table\_clause\>*](create-table-statement-data-definition-20d58a5.md#loio20d58a5f75191014b2fe92141b7df228__like_table_clause).

```
<replica_name> ::= [ <replica_schema_name>.]<identifier>
```



</dd><dt><b>

*<table\_contents\_source\>*

</b></dt>
<dd>

Specifies the source from which the table definition is derived.

```
<table_contents_source> ::= 
 (<table_element>, ...) [<with_association_clause>]
 | <like_table_clause>
 | [(<column_name>, ...)] <as_subquery>
```

You can create a table in the following ways:

-   Describing the table elements \(defined in this section\).

-   Basing the new table on an existing table \(CREATE TABLE...LIKE\). See[*<like\_table\_clause\>*](create-table-statement-data-definition-20d58a5.md#loio20d58a5f75191014b2fe92141b7df228__like_table_clause)\).

-   From the result of a subquery \(CREATE TABLE...AS\). See[*<subquery\>*](create-table-statement-data-definition-20d58a5.md#loio20d58a5f75191014b2fe92141b7df228__create_table_as_subquery)\).



<dl>
<dt><b>

*<table\_element\>*

</b></dt>
<dd>

Defines the table columns with associated column or table constraints.

```
<table_element> ::=
 <column_definition> [ <column_constraint> ] 
 | <table_constraint>
```



</dd><dt><b>

*<column\_definition\>*

</b></dt>
<dd>

Defines a table column.

```
<column_definition> ::= <column_name> { <data_type> | <lob_data_type> }
   [ <ddic_data_type> ] 
   [ <default_value_clause> ]
   [ <col_gen_as_expression> | <col_gen_as_ident> ]
   [ <col_calculated_field> ]
   [ <fuzzy_search_index> ]
   [ <fuzzy_search_mode> ] 
   [ <persistent_memory_spec_clause> ]
   [ <column_comment_string> ]
   [ <load_unit> ]
   [ <numa_node_preference_clause> ]
```


<dl>
<dt><b>

*<column\_name\>*

</b></dt>
<dd>

Specifies the column name.

```
<column_name> ::= <identifier>
```



</dd><dt><b>

*<data\_type\>*

</b></dt>
<dd>

Specifies the column data types.

```
<data_type> ::=
ARRAY
 | DATE 
 | TIME 
 | SECONDDATE 
 | TIMESTAMP 
 | TINYINT 
 | SMALLINT 
 | INT
 | BIGINT 
 | SMALLDECIMAL 
 | REAL 
 | DOUBLE
 | NVARCHAR [ (<unsigned_integer>) ]
 | VARBINARY [ (<unsigned_integer>) ]
 | DECIMAL [ (<unsigned_integer> [, <unsigned_integer> ]) ] 
 | FLOAT [ (<unsigned_integer>) ] 
 | BOOLEAN
 | REAL_VECTOR [ (<unsigned_integer>) ]
```

For tables with time-selection partitioning, the data type for the time-selection column must be NVARCHAR\(8\).



</dd><dt><b>

*<lob\_data\_type\>*

</b></dt>
<dd>

Specifies the LOB data type.

```
<lob_data_type> ::=
 <lob_type_name> [ MEMORY THRESHOLD <memory_threshold_value> ]
```


<dl>
<dt><b>

*<lob\_type\_name\>*

</b></dt>
<dd>

Specifies the type of LOB.

```
<lob_type_name> ::= { BLOB | CLOB | NCLOB }
```



</dd>
</dl>



</dd><dt><b>

*<ddic\_data\_type\>*

</b></dt>
<dd>

The available data types.

```
<ddic_data_type> ::= 
 DDIC_ACCP | DDIC_CHAR | DDIC_CDAY | DDIC_CLNT | DDIC_CUKY | DDIC_CURR | DDIC_D16D
 | DDIC_D34D | DDIC_D16R | DDIC_D34R | DDIC_D16S | DDIC_D34S | DDIC_DATS | DDIC_DAY  | DDIC_DEC
 | DDIC_FLTP | DDIC_GUID | DDIC_INT1 | DDIC_INT2 | DDIC_INT4 | DDIC_INT8 | DDIC_LANG | DDIC_LCHR
 | DDIC_MIN  | DDIC_MON  | DDIC_LRAW | DDIC_NUMC | DDIC_PREC | DDIC_QUAN | DDIC_RAW  | DDIC_RSTR
 | DDIC_SEC  | DDIC_SRST | DDIC_SSTR | DDIC_STRG | DDIC_STXT | DDIC_TIMS | DDIC_UNIT | DDIC_UTCM
 | DDIC_UTCL | DDIC_UTCS | DDIC_TEXT | DDIC_VARC | DDIC_WEEK
```



</dd><dt><b>

*<memory\_threshold\_value\>*

</b></dt>
<dd>

Specifies whether LOB data should be stored in memory.

```
<memory_threshold_value> ::= { <unsigned_integer> | NULL }
```

-   If *<memory\_threshold\_value\>* is not provided, then a hybrid LOB with a memory threshold of 1000 is created by default.

-   If *<memory\_threshold\_value\>* is provided and its LOB size is equal or less than the memory threshold value, then the LOB data is stored in memory.

-   If *<memory\_threshold\_value\>* is NULL, then all LOB data is stored in memory.

-   If *<memory\_table lobthreshold\_value\>* is 0, then all LOB data is stored in disk.


This type of index can only be used for column store tables.



</dd><dt><b>

*<default\_value\_clause\>*

</b></dt>
<dd>

Specifies a value to be assigned to the column if an INSERT statement does not provide a value for the column.

```
<default_value_clause> ::= DEFAULT <default_value_exp>

<default_value_exp> ::= 
 NULL 
 | <string_literal>
 | <signed_numeric_literal> <unsigned_numeric_literal> 
 | <datetime_value_function>

<datetime_value_function> ::= 
 CURRENT_DATE 
 | CURRENT_TIME 
 | CURRENT_TIMESTAMP 
 | CURRENT_UTCDATE 
 | CURRENT_UTCTIME 
 | CURRENT_UTCTIMESTAMP
```



</dd><dt><b>

*<col\_gen\_as\_expression\>*

</b></dt>
<dd>

Specifies the expression to generate the column value at runtime.

```
<col_gen_as_expression> ::= GENERATED ALWAYS AS <expression>
```



</dd><dt><b>

*<col\_gen\_as\_ident\>*

</b></dt>
<dd>

Specifies an identity column. Only one can be specified per table.

Generated columns are only supported in column store table definitions, and can only reference base columns that are defined prior to them in the DDL statement \(that is, to the left of them\). You cannot define a default for a generated column, and they cannot be used as part of a primary key or unique constraint.

You cannot drop a base column that is referenced by a generated column.

```
<col_gen_as_ident> ::= 
 GENERATED { ALWAYS | BY DEFAULT } AS IDENTITY [ ( <sequence_option> )  ) ]
 
<sequence_option>] ::= 
 <sequence_param_list> 
 | RESET BY <subquery> 
 | <sequence_param_list> RESET BY <subquery>
 
<sequence_param_list> ::= <sequence_parameter> [, <sequence_parameter> [,…] ]
 
<sequence_parameter> ::= 
 START WITH <start_value>
 | INCREMENT BY <increment_value>
 | MAXVALUE <max_value>
 | NO MAXVALUE
 | MINVALUE <min_value>
 | NO MINVALUE
 | CYCLE
 | NO CYCLE
 | CACHE <cache_size>
 | NO CACHE
 | RESET BY <subquery>
```

There are two types of IDENTITY columns: GENERATED ALWAYS, and GENERATED BY DEFAULT:


<dl>
<dt><b>

GENERATED ALWAYS

</b></dt>
<dd>

A GENERATED ALWAYS AS IDENTITY column increments based solely on the sequence parameter settings \(*<sequence\_param\_list\>*\). With the exception changes to the RESET BY definition, the sequence defined for a GENERATED ALWAYS IDENTITY column cannot be altered or reset after it has been set, and inserting a value into a GENERATED ALWAYS identity column fails and returns an error.

Non-deterministic functions are not allowed for columns defined as GENERATED ALWAYS.



</dd><dt><b>

GENERATED BY DEFAULT

</b></dt>
<dd>

A GENERATED BY DEFAULT IDENTITY column increments using the sequence parameter settings \(*<sequence\_param\_list\>*\) only when no identity value is specified in the INSERT statement \(that is, the identity column is left out of the insert column list\). When a value is specified for the identity column during the INSERT, then the specified value is inserted \(assuming the value does not already exist\) and the following behavior occurs with respect to the value of the identity column:

-   If the specified value is higher than the existing identity value with a positive increment, then this resets the current sequence value to an allowable sequence value that is equal to the specified value, or the next one lower than the specified value.

-   If the specified value is lower than the existing value with a negative increment, then this resets the current sequence value to an allowable sequence value that is equal to the specified value, or the next one higher than the specified value.

-   Otherwise, the current sequence value is not reset.




</dd>
</dl>

Identity columns are supported in global and local temporary tables, both for row store and column store tables. They can be added to, or dropped from, a table. However, they cannot be altered.

If the RESET BY *<subquery\>* clause is specified, then during the restart of the database, the database automatically executes the subquery and restarts the sequence value with the returned value.

If the RESET BY *<subquery\>* clause is omitted, an automatic subquery is generated to obtain the next value for the identity column, taking into account the specified *<increment\_value\>*. When the *<increment\_value\>* is positive, the subquery is designed to retrieve a value greater than the maximum value of the column. On the other hand, when the *<increment\_value\>* is negative, the subquery is designed to retrieve a value lower than the minimum value of the column.

For more information on subqueries, see the SELECT statement.

For more information on sequences and sequence parameters, see the CREATE SEQUENCE statement.



</dd><dt><b>

*<col\_calculated\_field\>*

</b></dt>
<dd>

Specifies the expression that replaces the column at query compilation time.

```
<col_calculated_field> ::= AS <expression>
```

-   The data type of a calculated field column can be a default value.

-   The calculated field column can reference not only base columns, but also other calculated field columns.

-   The maximum of recursive calculated field is 16.

-   Dropping or altering the base columns of a calculated field is not possible.

-   A calculated field column without a declared data type cannot be hidden.



</dd><dt><b>

*<fuzzy\_search\_index\>*

</b></dt>
<dd>

Turns a fuzzy search index on or off \(the default\).

```
<fuzzy_search_index> ::= FUZZY SEARCH INDEX { ON | OFF }
```



</dd><dt><b>

*<fuzzy\_search\_mode\>*

</b></dt>
<dd>

Sets the fuzzy search mode with the value of *<string\_literal\>*.

```
<fuzzy_search_mode> ::= 
 FUZZY SEARCH MODE [ <string_literal> | NULL ]
```

If NULL is specified, then the fuzzy search mode is reset.



</dd><dt><b>

*<column\_comment\_string\>*

</b></dt>
<dd>

Specifies a descriptive comment for the column.

```
<column_comment_string> ::= COMMENT <string_literal>
```

Specifying *<column\_comment\_string\>* saves you from having to execute a separate COMMENT ON statement later.



</dd>
</dl>



</dd><dt><b>

*<column\_constraint\>*

</b></dt>
<dd>

Specifies a constraint on a column.

```
<column_constraint> ::= 
 NULL
 | NOT NULL
 | { HIDDEN | NOT HIDDEN }
 | [ CONSTRAINT <constraint_name> ] { <unique_specification> | <references_specification> }
```


<dl>
<dt><b>

NULL

</b></dt>
<dd>

Allows NULL values in the column. If NULL is specified it is not considered a constraint, it represents that a column may contain a null value. The default is NULL.



</dd><dt><b>

NOT NULL

</b></dt>
<dd>

Prohibits NULL values in the column.



</dd><dt><b>

HIDDEN | NOT HIDDEN

</b></dt>
<dd>

Specifies whether to hide the column; if not specified, the default behavior is NOT HIDDEN. A hidden column is excluded from a SELECT \* operation on a table. It is also excluded in an INSERT INTO..VALUES operation unless the column list specifically references it. A hidden column still appears in system views such as TABLE\_COLUMNS, INDEX\_VIEWS, PARTITIONS, and so on. In the TABLE\_COLUMNS system view, the IS\_HIDDEN column indicates whether a column is hidden. Hidden columns still appear when using smart data access and in federation with other databases.



</dd><dt><b>

*<unique\_specification\>*

</b></dt>
<dd>

Specifies a uniqueness constraint on a column. There are two uniqueness constraints you can set: UNIQUE and PRIMARY KEY.

```
<unique_specification> ::=
 UNIQUE [ <rs_tree_type_index> | <cs_inverted_type_index> ] 
 | PRIMARY KEY [ <rs_tree_type_index> | <cs_inverted_type_index> ] 

```

When the optional index type \(*<rs\_tree\_type\_index\>* or *<cs\_inverted\_type\_index\>*\) is omitted, the database server chooses the appropriate type by considering the table type and the column data type.

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

PRIMARY KEY

</b></dt>
<dd>

Specifies a primary key constraint, which is a combination of a NOT NULL constraint and a UNIQUE constraint.



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



</dd><dt><b>

*<references\_specification\>*

</b></dt>
<dd>

For *<references\_specification\>*, see [References Specification](create-table-statement-data-definition-20d58a5.md#loio20d58a5f75191014b2fe92141b7df228__create_table_references_specification).



</dd>
</dl>



</dd>
</dl>



</dd><dt><b>

*<table\_constraint\>*

</b></dt>
<dd>

The table constraint can be either a unique constraint, a referential constraint, or a check constraint.

```
<table_constraint> ::= 
 [ CONSTRAINT <constraint_name> ]
 { <unique_constraint_definition> 
  | <referential_constraint_definition>  
  | <check_constraint_definition> }
```


<dl>
<dt><b>

*<unique\_constraint\_definition\>*

</b></dt>
<dd>

Specifies unique constraints.

```
<unique_constraint_definition> ::= 
 <unique_specification> ( <unique_column_name_list> ) 
```



</dd><dt><b>

*<unique\_column\_name\_list\>*

</b></dt>
<dd>

Specifies the unique column name list of one or more column names.

```
<unique_column_name_list> ::= 
 <unique_column_name>[, <unique_column_name>
```



</dd><dt><b>

*<unique\_column\_name\>*

</b></dt>
<dd>

Specifies a column name identifier.

```
<unique_column_name> ::= <identifier>
```



</dd><dt><b>

*<referential\_constraint\_definition\>*

</b></dt>
<dd>

Specifies a referential constraint.

```
<referential_constraint_definition> ::= 
 FOREIGN KEY ( <referencing_column_name_list> ) <references_specification>
```

To ensure uniqueness, the target of a foreign key constraint must be either a full primary key or a unique column. Self-referencing foreign key constraints are supported.



</dd><dt><b>

*<referencing\_column\_name\_list\>*

</b></dt>
<dd>

Specifies the target column\(s\) of the foreign key constraint.

```
<referencing_column_name_list> ::= 
 <referencing_column_name>[, <referencing_column_name> ]
```

Specifies that a hash encodes the composite key in a condensed manner. This option allows for faster equality queries over the composite keys, \[,…\] Specifies that a hash encodes the composite key\] in a condensed manner. This option allows for faster equality queries over the composite keys, as well as reduced memory requirements for storage of the composite key.



</dd><dt><b>

*<referencing\_column\_name\>*

</b></dt>
<dd>

The identifier of a referencing column.

```
<referencing_column_name> ::= <identifier>
```



</dd><dt><b>

*<references\_specification\>*

</b></dt>
<dd>

Specifies the referenced table, with optional column=name list and trigger action.

```
<references_specification> ::= 
  REFERENCES <referenced_table> [ ( <referenced_column_name_list> ) ]
  [ <referential_triggered_action> ]
  [ <constraint_enforcement> ]
  [ <constraint_check_time> ]

<constraint_check_time> ::= INITIALLY { IMMEDIATE | DEFERRED }
```



</dd><dt><b>

*<referenced\_table\>*

</b></dt>
<dd>

Specifies the identifier of a table to be referenced.

```
<referenced_table> ::= <identifier>
```



</dd><dt><b>

*<referenced\_column\_name\_list\>*

</b></dt>
<dd>

Specifies the referenced column name list, which can have one or more column names.

If *<referenced\_column\_name\_list\>* is specified, then there is a one-to-one correspondence between *<column\_name\>* of *<column\_definition\>* \(see [column definition](create-table-statement-data-definition-20d58a5.md#loio20d58a5f75191014b2fe92141b7df228__create_table_column_definition)\) and *<referenced\_column\_name\>*. If it is not specified, then there is a one-to-one correspondence between *<column\_name\>* of *<column\_definition\>* and the column name of the referenced table's primary key.

```
<referenced_column_name_list> ::= 
 <referenced_column_name>[, <referenced_column_name> [,…] ]
```

*<referenced\_column\_name\>* specifies the identifier of the column name to be referenced.



</dd><dt><b>

*<constraint\_check\_time\>*

</b></dt>
<dd>

Specifies when to check constraints. The default is INITIALLY IMMEDIATE.

-   IMMEDIATE - referential constraints are checked immediately during statement execution. If a referential constraint is violated, then the statement fails.

-   DEFERRED - referential constraints are checked at commit time. If a referential constraint is violated, then the transaction is rolled back. Also, if *<referential\_triggered\_action\>* is set to something other than RESTRICT, then the referential constraint check on the parent \(referencing\) table is not deferred and instead is checked immediately.




</dd><dt><b>

*<referential\_triggered\_action\>*

</b></dt>
<dd>

Specifies an update rule with an optional delete rule or a delete rule with an optional update rule. The order in which they are specified provides an order of precedence for execution.

```
<referential_triggered_action> ::= 
 <update_rule> [ <delete_rule> ]
 | <delete_rule> [ <update_rule >]
```



</dd><dt><b>

*<update\_rule\>*

</b></dt>
<dd>

Specifies the update rule.

```
<update_rule> ::= ON UPDATE <referential_action>

<referential_action> ::= 
 CASCADE 
 | RESTRICT 
 | SET DEFAULT 
 | SET NULL
```

The following UPDATE referential actions are possible:


<table>
<tr>
<th valign="top">

Action Name

</th>
<th valign="top">

Update Action

</th>
</tr>
<tr>
<td valign="top">

RESTRICT

</td>
<td valign="top">

Any updates to a referenced table are prohibited if there are any matched records in the referencing table. This is the default action.

</td>
</tr>
<tr>
<td valign="top">

CASCADE

</td>
<td valign="top">

When a record in the referenced table is updated, the corresponding records in the referencing table are automatically updated to match the new values. This is the default action.

</td>
</tr>
<tr>
<td valign="top">

SET NULL

</td>
<td valign="top">

If a record is updated in the referenced table, then the corresponding records in the referencing table are also updated with null values.

</td>
</tr>
<tr>
<td valign="top">

SET DEFAULT

</td>
<td valign="top">

If a record is updated in the referenced table, then the corresponding records in the referencing table are also updated with their default values

</td>
</tr>
</table>



</dd><dt><b>

*<delete\_rule\>*

</b></dt>
<dd>

Specifies the delete rule.

```
<delete_rule> ::= ON DELETE <referential_action>
```

The following DELETE referential actions are possible:


<table>
<tr>
<th valign="top">

Action Name

</th>
<th valign="top">

Delete Action

</th>
</tr>
<tr>
<td valign="top">

RESTRICT

</td>
<td valign="top">

Any deletions to a referenced table are prohibited if there are any matched records in the referencing table. This is the default action.

</td>
</tr>
<tr>
<td valign="top">

CASCADE

</td>
<td valign="top">

If a record in the referenced table is deleted, then the corresponding records in the referencing table are also deleted. When you specify NOT ENFORCED, new or modified rows are not checked to determine whether they violate the foreign key constraint. If a record in the referenced table is deleted, then the corresponding records in the referencing table are also deleted.

</td>
</tr>
<tr>
<td valign="top">

SET NULL

</td>
<td valign="top">

If a record in the referenced table is deleted, then the corresponding records in the referencing table are set to null.

</td>
</tr>
<tr>
<td valign="top">

SET DEFAULT

</td>
<td valign="top">

If a record in the referenced table is deleted, then the corresponding records in the referencing table are set to their default values.

</td>
</tr>
</table>



</dd><dt><b>

*<check\_constraint\_definition\>*

</b></dt>
<dd>

```
<check_constraint_definition> ::= CHECK ( <search_condition> )
```

Specifies a predicate to use as a table check constraint. A table check constraint is satisfied if *<search\_condition\>* evaluates to true.



</dd><dt><b>

*<constraint\_enforcement\>*

</b></dt>
<dd>

Enable or disable constraint enforcement and validation.

```
<constraint_enforcement> ::= <constraint_name> <constraint_enforcement>

<constraint_enforcement> ::= <enforcement_option>
 | <validation_option>
 | <enforcement_option> <validation_option>

<enforcement_option> ::= [NOT] ENFORCED

<validation_option> ::= [NOT] VALIDATED
```

When you specify NOT VALIDATED, existing data is not checked to determine whether it violates the foreign key constraint.

Enable or disable constraint enforcement rather than dropping and recreating the constraint.

The default *<enforcement\_option\>* is ENFORCED and the default *<validation\_option\>* is VALIDATED.



</dd><dt><b>

*<like\_table\_clause\>*

</b></dt>
<dd>

Specifies a source table to be used for the definition.

```
<like_table_clause>::=
 LIKE { <like_table_name> <table_creation_syntax> 
 | <like_table_name> <like_table_replica_specification> }

<table_creation_syntax> ::= 
 [ WITH [ NO ] DATA ] [ <like_without_option> ]
     [ WITH INDEX ] [ <defined_index_name_list> ]
```

With the exception of mask definitions, all the column definitions with constraints, default values, and other properties, such as generated columns and so on, are copied from the table *<like\_table\_name\>*. All table constraints, indexes, and the table location are also copied. Use the ALTER TABLE statement to add mask definitions to the new table.



</dd><dt><b>

*<like\_table\_name\>*

</b></dt>
<dd>

Specifies the table being used for source definition information.

```
<like_table_name> ::= 
 [ [ <database_name>.]<source_schema_name>.]<source_table_name>

<source_table_name> ::= <identifier>
```

Schema name and database name are optional. *<database\_name\>* is only for use in a multitenant system where cross-database access is enabled for the given database name.



</dd><dt><b>

WITH \[NO\] DATA

</b></dt>
<dd>

Specifies that data is copied from the *<like\_table\_name\>* table. The default value of WITH NO DATA does not copy the table data.



</dd><dt><b>

*<like\_without\_option\>*

</b></dt>
<dd>

Specifies which properties are not copied from the *<like\_table\_name\>* table. For example, when WITHOUT PARTITION is specified, the table is not partitioned. The WITHOUT clause

```
<like_without_option> ::= 
 WITHOUT AUTO MERGE 
 | WITHOUT NO LOGGING 
 | WITHOUT PARTITION 
 | WITHOUT UNLOAD 
 | WITHOUT PRELOAD 
 | WITHOUT UNLOAD PRIORITY 
 | WITHOUT INDEX 
 | WITHOUT FUZZY SEARCH INDEX 
 | WITHOUT FUZZY SEARCH MODE 
 | WITHOUT GLOBAL TEMPORARY 
 | WITHOUT LOCAL TEMPORARY
 | WITHOUT CONSTRAINT
 | WITHOUT NUMA NODE
```

When you specify WITHOUT CONSTRAINT, the following restraints are not copied to the new table: PRIMARY KEY, UNIQUE, NOT NULL, CHECK constraints, and REFERENTIAL CONSTRAINT \(foreign keys\).

Use the WITHOUT NUMA NODE parameter to ignore NUMA NODE preferences that were set on the source table while creating the new table. If you do not include the WITHOUT NUMA NODE parameter, then SAP HANA compares the number of NUMA nodes on the target system with the number on the source system. If the number of NUMA nodes on the target system is greater than, or equal to, the number on the source system, then SAP HANA applies the node preference to the new table. If it has fewer NUMA nodes, then SAP HANA ignores the NUMA node preferences.



</dd><dt><b>

*<like\_table\_replica\_specification\>*

</b></dt>
<dd>

Creates a replica based on an existing table.

```
<like_table_replica_specification> ::= 
 [ <sync_or_async> ] REPLICA [ ( <src_table_column_list> ) ] 
 [ <replica_partition> ] 
 [ AT '<replica_indexserver_host>:<replica_indexserver_port>' ]

<src_table_column_list> ::= <column_name> [, <column_name> [,...] ]
<replica_partition> ::= <partition_clause>
```



</dd><dt><b>

*<replica\_partition\>*

</b></dt>
<dd>

Specifies the partitions for the replicated table.

```
<replica_partition> ::= <partition_clause>
```

The *<replica\_partition\>* clause supports all partition types not using time selection. See [*<partition\_clause\>*](create-table-statement-data-definition-20d58a5.md#loio20d58a5f75191014b2fe92141b7df228__create_table_partition_clause) in this topic.



</dd><dt><b>

*<as\_subquery\>*

</b></dt>
<dd>

Creates a table and fills it with the data computed by the subquery. For more information about subqueries, see the SELECT statement topic.

```
<as_subquery> ::= { AS ( <subquery> ) [ WITH [ NO ] DATA ] | <with_clause> }
 [ ADD <identity_column> ]

<with_clause> :: ( WITH <alias> AS ( <subquery> AS <alias> [,... ] ) SELECT <expression> FROM <alias>

<identity_column> ::=  ( <column_name> INT GENERATED ALWAYS AS IDENTITY( START WITH <integer> INCREMENT BY <integer> ) )
```

While both the AS *<subquery\>* syntax and the *<with\_clause\>* syntax create a table with data in it, the AS *<subquery\>* syntax *copies**<subquery\>*, whereas the *<with\_clause\>* syntax allows you to *define* the data to insert into the columns.

If the *<as\_subquery\>* clause follows a *<column\_names\>* clause, then the column names specified in *<column\_names\>* override the column names defined in *<as\_subquery\>*.



</dd><dt><b>

*<subquery\>*

</b></dt>
<dd>

Defines the columns for the new table, If there are constraints on column derived from *<subquery\>*, only the NOT NULL constraints are copied over.

WITH DATA inserts copies of the data from the columns in *<subquery\>*; this is the default. If you specify WITH NO DATA, the table is created without any data.



</dd><dt><b>

*<with\_clause\>*

</b></dt>
<dd>

Defines the columns for the table as well as the data to insert into them.



</dd><dt><b>

ADD *<identity\_column\>*

</b></dt>
<dd>

Defines an ID column to add to columns derived from *<subquery\>*. ADD *<identity\_column\>* syntax is not supported when creating virtual tables.



</dd>
</dl>



</dd><dt><b>

*<with\_annotation\_clause\>*

</b></dt>
<dd>

Specifies table-, column-, and parameter-level annotations in the form of key/value pairs. You can reference annotations in subsequent queries to filter results.

```
<with_annotation_clause> ::= WITH ANNOTATIONS ( { [ <set_table_annotations> ] [ <set_column_annotations> ] [ <set_parameter_annotations> ] } )

<set_table_annotations> ::= <key_set_operation>

<set_column_annotations> ::= <column_annotation> [ <column_annotation> […] ]
<column_annotation> ::= COLUMN <column_ref> <key_set_operation>

<set_parameter_annotations> ::= <parameter_annotation> [ <parameter_annotation> […] ]
<parameter_annotation> ::= PARAMETER <column_ref> <key_set_operation>

<key_set_operation> ::= SET <key_value_pair_list> 

<key_value_pair_list> ::= <key_value_pair> [, <key_value_pair> [,…] ]
<key_value_pair> ::= '<key>'='<value>'

<column_ref> ::= <identifier>
<key> ::= <string>
<value> ::= <string>
```

While you must specify annotation on at least one object with the WITH ANNOTATION clause \(table, column, or parameter\), there is no limit on the number of annotations or types of annotations you can specify.

*<key\>* and *<value\>* represent the annotations you are configuring for the object \(table, column, or parameter\).



</dd><dt><b>

*<system\_versioning\_spec\>*

</b></dt>
<dd>

Configures system versioning for a table. System-versioning allows change tracking on database tables. This is achieved by adding validity-period columns to a table, and storing change information for the table in an associated history tables.

```
<system_versioning_spec> ::= { <history_table_definition> | <system_versioned_table_definition> }

<history_table_definition> ::= ( <column_definition> [,…] , 
 <sys_validfrom_column_name> TIMESTAMP NOT NULL, 
 <sys_validto_column_name> TIMESTAMP NOT NULL [ GENERATED ALWAYS AS ROW COMMIT ]
 )
                                       
<system_versioned_table_definition> ::= ( 
  <column_definition> [,…] ,
  <sys_validfrom_column_name> TIMESTAMP NOT NULL GENERATED ALWAYS AS ROW START [ COMMIT ], 
  <sys_validto_column_name> TIMESTAMP NOT NULL GENERATED ALWAYS AS ROW END,
  PERIOD FOR SYSTEM_TIME( <sys_validfrom_column_name>, <sys_validto_column_name><history_table_name> ]
  [ [ NOT ] VALIDATED ] 
 )
```


<dl>
<dt><b>

*<column\_definition\>*

</b></dt>
<dd>

This is the normal data column definition as described in the *<table\_elements\>* description and is only being included in the *<history\_table\_definition\>* and *<system\_versioned\_table\_definition\>* to demonstrate where to locate the system-versioning clauses relative to the overall table creation syntax.



</dd><dt><b>

*<sys\_validfrom\_column\_name\>*

</b></dt>
<dd>

In both *<history\_table\_definition\>* and *<system\_versioned\_table\_definition\>*, this column defines the column that holds the start time of the validity period. Note that in *<system\_versioned\_table\_definition\>*, an additional option GENERATED ALWAYS AS ROW START is added. This is the mechanism by which the system automatically updates the TIMESTAMP value in the column.

If the keyword COMMIT is present, then the timestamp values will be determined at the end of the database transaction. Otherwise the timestamps will be generated at transaction start. Notice that if COMMIT is specified, then the *<sys\_validto\_column\_name\>* in the *<history\_table\_definition\>* must have the GENERATED ALWAYS AS ROW COMMIT clause.



</dd><dt><b>

*<sys\_validto\_column\_name\>*

</b></dt>
<dd>

In both *<history\_table\_definition\>* and *<system\_versioned\_table\_definition\>*, this column defines the column that holds the end time of the validity period. Note that in *<system\_versioned\_table\_definition\>*, an additional option GENERATED ALWAYS AS ROW END is added. This is the mechanism by which the system automatically updates the TIMESTAMP value in the column.

If the clause GENERATED ALWAYS AS ROW COMMIT is present, then the timestamp values will be determined at the end of the database transaction. Otherwise the timestamps will be generated at transaction start. Notice that if GENERATED ALWAYS AS ROW COMMIT is specified, then the *<sys\_validfrom\_column\_name\>* in the *<system\_versioned\_table\_definition\>* must be defined as GENERATED ALWAYS AS ROW START COMMIT.



</dd><dt><b>

PERIOD FOR SYSTEM\_TIME \( *<sys\_validfrom\_column\_name\>*, *<valid\_to\_column\_name\>* \)

</b></dt>
<dd>

Specifies the validity period columns, and is for multi-column unique constraints, which may be defined as secondary unique index or primary key.



</dd><dt><b>

WITH SYSTEM VERSIONING HISTORY TABLE *<history\_table\_name\>*

</b></dt>
<dd>

Enables system-versioning for the table. *<history\_table\_name\>* must already exist and not be associated with any other system-versioned table. If you create the table without this clause, system versioning is not enabled; you must subsequently execute an ALTER TABLE statement to add the clause and enable system versioning.



</dd><dt><b>

\[ \[ NOT \] VALIDATED \]

</b></dt>
<dd>

Specifies whether to check if *<history\_table\_name\>* is empty. If VALIDATED is specified \(the default\), an exception is raised if *<history\_table\_name\>* is not empty. If NOT VALIDATED is specified, no emptiness check is performed on *<history\_table\_name\>*, and no exception is raised even if the history table has data in it.



</dd>
</dl>



</dd><dt><b>

*<application\_time\_period\_spec\>*

</b></dt>
<dd>

Creates an application-time period table. This option is only supported for column store tables.

```
<application_time_period_spec> ::= ( <column_definition_list>,
 <validfrom_column_name> <date_type> NOT NULL,
 <validto_column_name> <date_type> NOT NULL,
 PERIOD FOR APPLICATION_TIME ( <validfrom_column_name>, <validto_column_name> )
)
```


<dl>
<dt><b>

*<column\_definition\_list\>*

</b></dt>
<dd>

Specifies the column definition for the table. See the definition for *<column\_definition\>* earlier in this topic for more information about *<column\_definition\>*.

```
<column_definition_list> ::= <column_definition> [, <column_definition> [,…] ]
```



</dd><dt><b>

*<validfrom\_column\_name\>* and *<validto\_column\_name\>*

</b></dt>
<dd>

Specifies the names of the columns that will hold the period start and end times.



</dd><dt><b>

*<datetime\_type\>*

</b></dt>
<dd>

Specifies the datetime type of *<validfrom\_column\_name\>* and *<validto\_column\_name\>*.



</dd><dt><b>

PERIOD FOR APPLICATION\_TIME

</b></dt>
<dd>

Specifies the validity period columns. The period adds an implicit constraint that *<validfrom\_column\_name\>* must be less than *<validto\_column\_name\>*.



</dd>
</dl>



</dd><dt><b>

*<bi\_temporal\_table\_spec\>*

</b></dt>
<dd>

Creates a bi-temporal table, which is a table that has both system-versioning and an application-time period defined on it. The syntax for creating a bi-temporal table combines the syntax elements from both types of table. The following syntax block shows this combination. However, see the *<system\_versioning\_spec\>* and *<application\_time\_period\_spec\>* definitions in this topic for descriptions of the syntax elements.

```
<bi_temporal_table_spec> ::= { <bi_temporal_history_table_definition> | <bi_temporal_system_versioned_table_definition> }

<bi_temporal_history_table_definition> ::= ( 
 <column_definition_list>,
 <sys_validfrom_column_name> TIMESTAMP NOT NULL,
 <sys_validto_column_name> TIMESTAMP NOT NULL, 
 <validfrom_column_name> DATE NOT NULL, 
 <validto_column_name> DATE NOT NULL 
 )
                                       
<bi_temporal_system_versioned_table_definition> ::= ( 
  <column_definition_list>,
  <sys_valid_from_column_name> TIMESTAMP NOT NULL GENERATED ALWAYS AS ROW START, 
  <sys_valid_to_column_name> TIMESTAMP NOT NULL GENERATED ALWAYS AS ROW END,
  <validfrom_column_name> DATE NOT NULL, 
  <validto_column_name> DATE NOT NULL, 
  PERIOD FOR APPLICATION_TIME ( <validfrom_column_name>, <validto_column_name> ),
  PERIOD FOR SYSTEM_TIME ( <sys_validfrom_column_name>, <sys_validto_column_name> ),
  PRIMARY KEY ( <column_name> [, <column_name> [,…] ] )
  [ WITH SYSTEM VERSIONING HISTORY TABLE <bi_temporal_history_table_name> ]
 )
```



</dd><dt><b>

*<with\_association\_clause\>*

</b></dt>
<dd>

Creates a relationship between the table being created and one or more existing tables.

```
<with_association_clause> ::= 
 WITH ASSOCIATIONS ( <association_def_list> )

<association_def_list> ::= <association_def>, ...
```


<dl>
<dt><b>

*<association\_def\>*

</b></dt>
<dd>

Specifies the association relationship, including the join cardinality and DDL statement. Associations are checked at runtime, not creation time.

```
<association_def> ::= 
 [ <join_cardinality> ] JOIN <table_name> [ AS <identifier > ] ON <predicate> WITH DEFAULT FILTER <predicate>

<join_cardinality> ::= 
 MANY TO ONE
 | MANY TO MANY
 | ONE TO ONE
 | ONE TO MANY

<table_name> ::= <identifier>
```

Use the WITH DEFAULT FILTER clause to specify a default predicate to filter column values.



</dd>
</dl>



</dd><dt><b>

*<with\_mask\_clause\>*

</b></dt>
<dd>

Adds data masking to the contents of the specified columns. Data masking transforms confidential data so that it appears meaningless to users who don't have the privileges required to view it.

```
<with_mask_clause> ::= WITH MASK ( <column_name> USING <mask_expression> [,…] )

<column_name> ::= <identifier>

<mask_expression> ::= <expression>
```

Masking behavior is supported on row and column tables, and SQL row and calculation views. It is not supported on any other type of tables \(virtual tables, extended tables, temporary tables etc.\) and views \(Join/Olap/Hierarchy views\). Only one masking behavior, definer owner-based \(DEFAULT MASK\) or session user based masking \(SESSION USER MASK\), is supported on a table or view with masked columns. You can combine both masking behaviors in an object hierarchy. For example, a view with session user based masking can be created on a table with owner-based masking. If masking is enforced on lower-level objects, results for higher-level objects, for unauthorized users, may be incorrect because some results data is masked; no error is returned indicating lower-level objects are masked. If not specified, DEFAULT is the default.

*<mask\_expression\>* can be any type of expression, including a user-defined function, that returns the same data type and length as the original column. For more information on data masking, see the *SAP HANA Cloud, SAP HANA Database Security Guide*.



</dd><dt><b>

*<logging\_option\>*

</b></dt>
<dd>

Specifies logging options for the created table.

```
<logging_option> ::= { LOGGING | NO LOGGING }
```

This clause is not available for TEMPORARY tables, where the clause is automatically set to NO LOGGING and cannot be modified.


<dl>
<dt><b>

LOGGING

</b></dt>
<dd>

Activates table logging. This is the default logging option for ROW, COLUMN, and VIRTUAL tables.



</dd><dt><b>

NO LOGGING

</b></dt>
<dd>

Deactivates logging. A NO LOGGING table means that the definition of the table is persistent and globally available with data that is temporary and global.



</dd>
</dl>



</dd><dt><b>

*<auto\_merge\_option\>*

</b></dt>
<dd>

Specifies that an automatic delta merge is triggered; this is the default.

```
<auto_merge_option> ::= [NO] AUTO MERGE
```

NO AUTO MERGE disables automatic delta merging.



</dd><dt><b>

*<unload\_priority\_clause\>*

</b></dt>
<dd>

Specifies the priority of the table to be unloaded from memory.

```
<unload_priority_clause> ::= UNLOAD PRIORITY <unload_priority>
```

*<unload\_priority\>* is a number from 0 and 9, inclusive, where 0 means not-unloadable and 9 means earliest unload.



</dd><dt><b>

*<partition\_clause\>*

</b></dt>
<dd>

For clauses for creating heterogeneous and non-heterogeneous partitions, see the topics on *Non-heterogeneous Create Partition Clauses* *Heterogeneous Create Partition Clauses* in this guide.

[Non-Heterogeneous Create Partition Clauses](non-heterogeneous-create-partition-clauses-ca6a99b.md)

[Heterogeneous Create Partition Clauses](heterogeneous-create-partition-clauses-d496e58.md)



</dd><dt><b>

*<persistent\_memory\_spec\_clause\>*

</b></dt>
<dd>

Enables or disables persistent memory storage preference at the table, range partition, or column level, depending on where the clause is situated in the CREATE statement. For example, when specified inside the *<column\_definition\>* clause, it enables or disables persistent memory storage for the column.

```
<persistent_memory_spec_clause> ::= PERSISTENT MEMORY <pm_preference>

<pm_preference> ::= { ON | OFF }
```



</dd><dt><b>

*<load\_unit\>*

</b></dt>
<dd>

Specifies how to load data into memory when the table is queried. Specifying the load unit is only supported on column-store tables. *<load\_unit\>* can be set at column, table, and partition levels.

```
<load_unit> ::= { COLUMN | PAGE } LOADABLE
```


<dl>
<dt><b>

COLUMN LOADABLE

</b></dt>
<dd>

In-memory loading - the entire column is loaded into memory. COLUMN LOADABLE boosts performance at the cost of higher memory usage. This is the default behavior unless another value is inherited.



</dd><dt><b>

PAGE LOADABLE

</b></dt>
<dd>

In-buffer cache loading - column data is loaded by page into the buffer cache. PAGE LOADABLE reduces memory usage for specific columns by not requiring those columns to be fully memory resident.



</dd>
</dl>

In the case of competing or unspecified *<load\_unit\>* settings, the following logic is applied.

-   If there is a load unit preference specified for a column, apply that value.

-   Else if there is a load unit preference specified for the parent partition, apply that value.

-   Else if there is a load unit specified for the parent table, apply that value.

-   Else apply the default \(COLUMN LOADABLE\).




</dd><dt><b>

*<group\_option\_list\>*

</b></dt>
<dd>

Specifies the group type, subtype, and name, and whether the table is the leader of the table group.

```
<group_option_list> ::= <group_option> [ <group_option> ...]

<group_option> ::= 
 GROUP TYPE <identifier> 
 | GROUP SUBTYPE <identifier> 
 | GROUP NAME <identifier>
 | GROUP LEAD 
```

GROUP LEAD sets the table as the leader of the table group it belongs to.



</dd><dt><b>

*<replica\_clause\>*

</b></dt>
<dd>

Creates a table replica at the same time the source table is created.

To create a column-wise replica that is based on an existing table \(CREATE TABLE LIKE syntax\), see the *<like\_table\_replica\_specification\>* syntax in this topic.

```
<replica_clause> ::= 
 [ <sync_or_async> ] [ <column_or_row> ] REPLICA [ ( <src_table_column_list> ) ] [ <replica_partition> ]
 [ AT <replica_locations> ]
```


<dl>
<dt><b>

*<sync\_or\_async\>*

</b></dt>
<dd>

Specifies when to activate and populate the replica. The default is SYNCHRONOUS, which means the replica is created, populated with data, and enabled when the source table is created.

```
<sync_or_async> ::= { SYNCHRONOUS | ASYNCHRONOUS }
```

Replicas created as ASYNCHRONOUS are created empty and disabled; you must execute an ALTER SYSTEM ENABLE ALL ASYNCHRONOUS TABLE REPLICAS statement to enable them.



</dd><dt><b>

*<column\_or\_row\>*

</b></dt>
<dd>

Specifies whether the replica is a column or row table. If *<column\_or\_row\>* is not specified, then the type is the same as that of the source table.

```
<column_or_row> ::= { COLUMN | ROW }
```



</dd><dt><b>

*<replica\_partition\>*

</b></dt>
<dd>

Specifies the partitions for the replicated table.

```
<replica_partition> ::= <partition_clause>
```

The *<replica\_partition\>* clause supports all partition types not using time selection. See [*<partition\_clause\>*](create-table-statement-data-definition-20d58a5.md#loio20d58a5f75191014b2fe92141b7df228__create_table_partition_clause) in this topic.



</dd><dt><b>

*<src\_table\_column\_list\>*

</b></dt>
<dd>

Specifies a subset of the columns in the source table. A replica that has a subset of the columns from the source table is called a **column-wise replica**.

```
<src_column_list> ::= <src_column_name> [, <src_column_name> [,…] ]
```

Although you can specify the columns in any order, the order of the columns in the replica will match the order of columns in the source table.



</dd><dt><b>

*<replica\_locations\>*

</b></dt>
<dd>

Creates replicas at the specified locations.

```
<replica_locations> ::= AT { <indexserver_host_port> | ( <indexserver_host_port>, … )}

<indexserver_host_port> ::= '<hostname>:<port_number>'
```

If you do not specify a location, then the replica table is created based on the table placement rule. If no table placement rule is also defined, then the first replica table is created on one of secondary nodes that is not the source table location.



</dd>
</dl>



</dd><dt><b>

*<with\_replica\_list\>*

</b></dt>
<dd>

Creates one or more table replicas at the same time the source table is created. Optionally, the replica tables can be grouped.

```
<with_replica_list> ::= <with_replica_clause> [...]

```

```
<with_replica_clause> ::= WITH [ <sync_or_async> ] [ <column_or_row> ] 
   REPLICA [ ( <src_table_column_list> ) ] [ <replica_partition> ]
   [ <set_group_option> ][ AT <replica_locations> ]
```



</dd><dt><b>

*<location\_clause\>*

</b></dt>
<dd>

Specifies the index servers on which the partitions are created in a round-robin scheme.

```
<location_clause> ::= [ [ NOT ] MOVABLE ]
 AT [LOCATION] ('<hostname>:<port_number>')
```

A table can be created in the specified location with *<hostname\>*:*<port\_number\>*. *<location\_clause\>* can be specified when creating partitioned tables that are distributed on multiple instances. When *<location\_clause\>* is provided without *<partition\_clause\>*, the table is created on the first location specified. If location information is not provided, then the table is automatically assigned to one node. This option can be used for both row-store and column-store tables in a distributed environment.

Use the \[NOT\] MOVABLE clause to control whether the table can be moved to another location. When a table is set to NOT MOVABLE, it cannot be moved to another location. By default, tables are movable.



</dd><dt><b>

*<global\_temporary\_option\>*

</b></dt>
<dd>

Sets data availability of global temporary tables within session or transaction level. Only global temporary tables can use this option.

```
<global_temporary_option> ::= 
 <global_temporary_preserve> 
 | <global_temporary_delete>
```


<dl>
<dt><b>

*<global\_temporary\_preserve\>*

</b></dt>
<dd>

Causes data to remain available within a session. The data is deleted when the session is terminated.

```
<global_temporary_preserve> ::= ON COMMIT PRESERVE ROWS
```

PRESERVE is the default value. Therefore, global temporary tables use session data without this option.



</dd><dt><b>

*<global\_temporary\_preserve\>*

</b></dt>
<dd>

Causes data to remain available within a transaction. The data is deleted when the transaction is committed.

```
<global_temporary_delete> ::= ON COMMIT DELETE ROWS
```



</dd>
</dl>



</dd><dt><b>

*<unused\_retention\_period\_option\>*

</b></dt>
<dd>

Defines the retention period for a table or table partitions in seconds.

```
<unused_retention_period_option><retention_period> | ( <retention_period>, ...) }

<retention_period> ::= <unsigned_integer>
```

A single value specifies the retention period at table-level, including all of the table partitions. Multiple values specify individual retention periods for each of the table partitions. If multiple values are specified, then the number of values must match the number of table partitions.

The default value and behavior of UNUSED\_RETENTION\_PERIOD is 0 \(inactive\) seconds. To activate UNUSED\_RETENTION\_PERIOD, change the value to something other than 0. However, use of the UNUSED\_RETENTION\_PERIOD setting on a table requires that the global unused\_retention\_period setting in the `global.ini` configuration file be set to something other than 0.



</dd><dt><b>

*<record\_commit\_timestamp\_clause\>*

</b></dt>
<dd>

Specifies that the COMMIT timestamp of a row is tracked. If this option is enabled, then every row is associated with the COMMIT timestamp of the last transaction that performed a DML operation on the row.

```
<record_commit_timestamp_clause> ::= RECORD COMMIT TIMESTAMP
```

You cannot use the RECORD COMMIT TIMESTAMP clause when creating the following tables:

-   Temporary tables

-   Virtual tables

-   Multi-store tables

-   Proxy tables

-   Asynchronous/synchronous replicated tables


Synchronous replicated tables and tables created with the RECORD COMMIT TIMESTAMP clause cannot be updated together or the COMMIT operation fails.

Depending on the table type, DDL statements, such as ALTER TABLE or CREATE TABLE LIKE, can affect the value returned by the RECORD\_COMMIT\_TIMESTAMP\(\) function:

-   For column store tables, the returned value is zero if the result of a CREATE TABLE LIKE statement, otherwise the value is unaffected by the DDL.

-   For row store tables, the returned value is changed to the COMMIT timestamp of the transaction that performed the DDL operation.


You cannot use RECORD COMMIT TIMESTAMP with keys or indexes if you are creating a row store table.

For example, the following CREATE TABLE statements cannot be executed:

```
CREATE ROW TABLE ROWCTS_LIMIT (X INT PRIMARY KEY) RECORD COMMIT TIMESTAMP;
CREATE ROW TABLE ROWCTS_LIMIT (X INT UNIQUE) RECORD COMMIT TIMESTAMP; 
```

The following ALTER TABLE statements cannot be executed for row store tables that have been created with the RECORD COMMIT TIMESTAMP clause:

```
ALTER TABLE ROWCTS_LIMIT ADD (B INT PRIMARY KEY);
ALTER TABLE ROWCTS_LIMIT ALTER (X INT PRIMARY KEY);
ALTER TABLE ROWCTS_LIMIT ADD CONSTRAINT UK UNIQUE (X);
ALTER TABLE ROWCTS_LIMIT ADD (c INT UNIQUE);
ALTER TABLE ROWCTS_LIMIT ALTER (X INT CONSTRAINT X_UNIQ UNIQUE);
```

You cannot create an index on the table ROWCTS\_LIMIT since it was created with the RECORD COMMIT TIMESTAMP clause.

The following statements cannot be executed if the column table ROWCTS\_CS \(created with RECORD COMMIT TIMESTAMP\) has a primary key or unique index:

```
ALTER TABLE ROWCTS_CS ROW;
```

```
CREATE TABLE ROWCTS_RS LIKE ROWCTS_CS;
```



</dd><dt><b>

*<table\_comment\_string\>*

</b></dt>
<dd>

Specifies a descriptive comment for the table.

```
<table_comment_string> ::= COMMENT <string_literal>
```

Specifying *<table\_comment\_string\>* saves you from having to execute a separate COMMENT ON statement later.



</dd><dt><b>

*<numa\_node\_preference\_clause\>*

</b></dt>
<dd>

Sets the NUMA node preferences. This clause can be set in various locations such as range partition definitions \(not hash or round-robin\) and column definitions.

```
<numa_node_preference_clause> ::= NUMA NODE ( <numa_node_index_spec> )

<numa_node_index_spec> :: = <numa_node_spec> [, <numa_node_spec> [,…] 

<numa_node_spec> ::= { <integer_const> | <integer_const> TO <integer_const> }
```


<dl>
<dt><b>

*<numa\_node\_spec\>*

</b></dt>
<dd>

Specify one or more single NUMA nodes \(*<single\_node\_spec\>*\), or one or more NUMA node ranges \(*<range\_node\_spec\>*\), or a mixture of both.

NUMA node indexes should be specified in the range of 0 to one less than max\_numa\_node\_count, where max\_numa\_node\_count is the number of NUMA nodes configured for the system. If the NUMA node index specified is greater than or equal to max\_numa\_node\_count, then a random NUMA node in the range of 0 to one less than max\_numa\_node\_count is selected for allocation. For example, on a system where max\_numa\_node\_count is set to 8, if you specify a NUMA node index of 10, then any node in the range of 0 to 7 \(inclusive\) is chosen randomly for allocation.



</dd><dt><b>

*<integer\_const\>*

</b></dt>
<dd>

*<integer\_const\>* is an integer that cannot be a negative number.



</dd>
</dl>



</dd><dt><b>

*<primary\_key\_update\_clause\>*

</b></dt>
<dd>

Specifies if UPDATE statements are allowed on primary key columns. This clause is only supported on tables with heterogeneous partitioning.

```
<primary_key_update_clause> ::= PRIMARY KEY UPDATE {ON | OFF};
```



</dd>
</dl>



<a name="loio20d58a5f75191014b2fe92141b7df228__sql_create_table_description"/>

## Description

Tables are created without data except when *<as\_subquery\>* or *<like\_table\_clause\>* is used with the WITH DATA option.

This statement is not for use with virtual tables. To create a virtual table, use the CREATE VIRTUAL TABLE statement.



<a name="loio20d58a5f75191014b2fe92141b7df228__sql_create_table_examples"/>

## Examples

```
CREATE ROW TABLE A (A INT PRIMARY KEY, B INT);
```

Create table T4 with group type and name.

```
CREATE ROW TABLE T4 (C1 INT PRIMARY KEY, C2 DATE) GROUP TYPE group_type1 GROUP NAME group_name1;
```

Create a history table and a column table with system versioning enabled:

```
CREATE COLUMN TABLE account_history (
  account_id INT,
  account_owner_id NVARCHAR(10),
  account_balance DOUBLE,
  valid_from timestamp NOT NULL,
  valid_to timestamp NOT NULL
 );

CREATE COLUMN TABLE account (
  account_id INT PRIMARY KEY,
  account_owner_id NVARCHAR(10),
  account_balance DOUBLE,
  valid_from TIMESTAMP NOT NULL GENERATED ALWAYS AS ROW START,
  valid_to TIMESTAMP NOT NULL GENERATED ALWAYS AS ROW END,
  PERIOD FOR SYSTEM_TIME (valid_from, valid_to)
 )
 WITH SYSTEM VERSIONING HISTORY TABLE account_history;
```

Create a history table and a column table with transactional system-time:

```
CREATE COLUMN TABLE my_table_history
(
  x INT,
  y DOUBLE,
  valid_from TIMESTAMP NOT NULL,
  valid_to TIMESTAMP NOT NULL GENERATED ALWAYS AS ROW COMMIT
);

CREATE COLUMN table my_table
(
  x INT PRIMARY KEY,
  y DOUBLE,
  valid_from TIMESTAMP NOT NULL GENERATED ALWAYS AS ROW START COMMIT,
  valid_to TIMESTAMP NOT NULL GENERATED ALWAYS AS ROW END,
  PERIOD FOR SYSTEM_TIME (valid_from, valid_to)
)
WITH SYSTEM VERSIONING HISTORY TABLE my_table_history;

```

Create table T5 with identity column B that has a start value of 100 and increments by 10.

```
CREATE COLUMN TABLE T (A INT, B INT GENERATED ALWAYS AS IDENTITY (START WITH 100 INCREMENT BY 10));
```

Create a table `MyData` that has an NVARCHAR\(10\) column called My\_Field, and specify a comment for both the table and the column.

```
CREATE COLUMN TABLE MyData ( My_Field NVARCHAR(10) COMMENT 'My data values') COMMENT 'Table for data';
```

Create a table by querying another table and including an ID column:

```
CREATE TABLE BASE_TABLE (a int, b nvarchar(10));
CREATE LOCAL TEMPORARY TABLE #TARGET_TABLE (RENAME_A, RENAME_B) ADD (ID INT GENERATED ALWAYS AS IDENTITY(START WITH 1 INCREMENT BY 1)) AS (SELECT * FROM BASE_TABLE);

```

The CREATE TABLE statements in the example below create tables with names that start with “ct” and demonstrate using the WITH clause to define the columns and the data to insert:

```
CREATE TABLE t1(a INT, b INT, c INT);  
CREATE TABLE t2(a INT, b INT, c INT);
INSERT INTO t1 VALUES(1,12,13);            
INSERT INTO t2 VALUES(2,120,130);
                
CREATE TABLE ct1 AS (WITH alias AS (SELECT * FROM t1) SELECT * FROM alias);
CREATE TABLE ct2 AS (WITH w1 AS (SELECT * FROM t1) SELECT * FROM w1);   
CREATE TABLE ct3 AS (WITH t1 AS (SELECT * FROM t2) SELECT * FROM t1);                                           
CREATE TABLE ct4 AS (WITH w1 AS (SELECT * FROM t2) SELECT w1.a, t2.b FROM w1,t2);
CREATE TABLE ct5 AS (WITH w1 AS (SELECT * FROM t2), w2 AS (SELECT * FROM t1 INNER JOIN t2 ON t1.a=t2.a) SELECT w1.a FROM w1,w2);
CREATE TABLE ct6 AS (WITH d AS (SELECT 1 AS val FROM dummy) SELECT val FROM d);
```

Creates a table, t1, with annotations:

```
CREATE COLUMN TABLE t1(c1 INT) WITH ANNOTATIONS(
    SET 't_k1' = 't_v1', 't_k2' = 't_v2'
    COLUMN c1 SET 'c_k1' = 'c_v1', 'c_k2' = 'c_v2');
```


<dl>
<dt><b>

Replication

</b></dt>
<dd>

Create table t1 with an asynchronous replica at indexserver seltera17:30040.

```
CREATE COLUMN TABLE t1(a INT) ASYNCHRONOUS REPLICA AT 'seltera17:30040';
```

Create table C1 that has the same definition as table A. Table C1 also has the same records as table A.

```
CREATE COLUMN TABLE C1 LIKE A WITH DATA;
```

Create table T5 with the replica grouping attributes NAME and TYPE.

```
CREATE COLUMN TABLE T5 (A INT, B INT) WITH REPLICA GROUP NAME GROUPB GROUP TYPE type1;
```

Create table T4 with replicas in all indexservers.

```
CREATE ROW TABLE T4 (C1 INT PRIMARY KEY) REPLICA AT ('host_name:30040', 'host_name:30042');
```

Create an asynchronous table replica REP\_SCHEMA.TAB1 from the existing table SRC\_SCHEMA.TAB1.

```
CREATE ROW TABLE REP_SCHEMA.TAB1 LIKE SRC_SCHEMA.TAB1 ASYNCHRONOUS REPLICA;
```

Create a table replica REP\_TABLE1 with an asymmetric partitioning scheme from source table SRC\_TABLE. All source columns are replicated. The partition scheme is HASH 8 and the partition key is C2.

```
CREATE COLUMN TABLE SRC_TABLE (C1 INT, C2 INT, C3 INT, primary key (C1, C2, C3)) PARTITION BY HASH (C1) PARTITIONS 32;

CREATE COLUMN TABLE REP_TABLE1 LIKE SRC_TABLE REPLICA PARTITION BY HASH (C2) PARTITIONS 8;
```

Create a replica table REP\_TABLE2 with an asymmetric partitioning scheme from the source table SRC\_TABLE. Only columns C1 and C3 are replicated. The partitioning scheme is RANGE and the partition key is C3.

```
CREATE COLUMN TABLE REP_TABLE2 LIKE SRC_TABLE REPLICA (C1, C3) PARTITION BY RANGE (C3) (PARTITION '1' <= VALUES < '100’, PARTITION OTHERS);
```

The following statements create a source table and a column-wise replica. You can specify a name for the replica that you can reference later to query, drop, or move the replica.

```
/* create a source table, and then create a column-wise replica based on the definition of the source table */
CREATE COLUMN TABLE srcSchema.srcTableName (A INT, B INT, C NVARCHAR(10), D CHAR(1), E BIGINT, PRIMARY KEY (A));
CREATE COLUMN TABLE repSchema.repName LIKE srcSchema.srcTableName SYNCHRONOUS REPLICA (A, C, D);
```

Creates table A1 with index index1 and then creates table A2 with index index2 like table A1 with index index1.

```
CREATE COLUMN TABLE a1(cola INT);
CREATE INDEX index1 ON A1 (cola);
REATE COLUMN TABLE A2 LIKE A1 WITH DATA WITH INDEX index1 AS INDEX2;
```



</dd>
</dl>


<dl>
<dt><b>

Non-heterogeneous Partitioning

</b></dt>
<dd>

Create a non-heterogeneous range partitioned table named P1 that has a DATE-type column A. Column U has a primary key constraint and is used as a range-partitioning column.

```
CREATE COLUMN TABLE P1 (A DATE PRIMARY KEY) PARTITION BY RANGE (A) 
   (PARTITION '2010-02-03' <= VALUES < '2011-01-01', PARTITION VALUE = '2011-05-01');
```

Create a non-heterogeneous hash partitioned table named P2, with primary key defined for columns A and B.

```
CREATE COLUMN TABLE P2 (A INT, B INT, C INT, PRIMARY KEY(A, B)) 
   PARTITION BY HASH (A, B) PARTITIONS 2;
```

Create a non-heterogeneous hash-hash partitioned table named P3, with primary key defined for columns A and B.

```
CREATE COLUMN TABLE P3 (A INT, B INT, C INT, PRIMARY KEY(A, B)) 
   PARTITION BY HASH (A, B) PARTITIONS 2 SUBPARTITION BY HASH (C) PARTITIONS 2;
```

Create a non-heterogeneous hash-range partitioned table named P4 where columns A and B define the hash partition and column C defines the range subpartition.

```
CREATE COLUMN TABLE P4 (A INT, B INT, C INT) PARTITION BY HASH (A, B) PARTITIONS 2 
   SUBPARTITION BY RANGE (C) (PARTITION 10 <= VALUES < 20);
```

Create a non-heterogeneous range-range partitioned table named P5. The OTHERS partition is defined on the first level. PERSISTENT MEMORY is enabled on both levels. The NUMA node preference is set on the first partition only.

```
CREATE COLUMN TABLE P5 (A INT, B INT) PARTITION BY RANGE (A) 
   (PARTITION 10 <= VALUES < 20 PERSISTENT MEMORY ON NUMA NODE ('3'), PARTITION OTHERS PERSISTENT MEMORY ON)
      SUBPARTITION BY RANGE (B) (PARTITION VALUES=100 PERSISTENT MEMORY ON);
```

Create a non-heterogeneous partitioned table with movable partitions.

```
CREATE COLUMN TABLE P6 (C1 INT, C2 INT) PARTITION BY RANGE (C1)
   (PARTITION VALUE = 1) 
   SUBPARTITION BY RANGE (C2) (PARTITION VALUE = 1, PARTITION VALUE = 2 MOVABLE, PARTITION VALUE = 3 NOT MOVABLE);
```



</dd><dt><b>

Heterogeneous Partitioning

</b></dt>
<dd>

Create a single level range partitioned heterogeneous table. This table has no subpartitions defined.

```
CREATE COLUMN TABLE A1 (I INT, J INT, K INT, PRIMARY KEY(I, J)) 
   PARTITION BY RANGE (I) ((PARTITION 10 <= VALUES < 20, PARTITION 20 <= VALUES < 30));
```

Create a multi-level range-range partitioned heterogeneous table.

```
CREATE COLUMN TABLE A2 (I INT, J INT, K INT, PRIMARY KEY(I, J)) 
   PARTITION BY RANGE (I) ((PARTITION 10 <= VALUES < 20, PARTITION 20 <= VALUES < 30)
      SUBPARTITION BY RANGE (J) (PARTITION 100 <= VALUES < 150, PARTITION VALUE = 200));
```

Create a heterogeneous multi-level partitioned table. The table has three first-level partitions. The first partition has the ranges 10-20 and 20-30. The second partition has the target value 40. The final partition is OTHERS for any values outside the scope of the first to partitions. The first two partitions each have a subpartition defined. Each range or target value of the first-level partitions has its own properties defined. The two subpartitions are same type \(range\) and reference the same column \(B\). The subpartitions also have dynamic range partitioning enabled.

```
CREATE COLUMN TABLE A3 (A INT, B INT NOT NULL, C INT) PARTITION BY RANGE (A)
   ((PARTITION 10 <= VALUES < 20 GROUP NAME 'GRP 1' INSERT OFF, PARTITION 20 <= VALUES < 30 GROUP NAME 'GRP 1' INSERT OFF) 
      SUBPARTITION BY RANGE(B) (PARTITION 0 <= VALUES < 10 PAGE LOADABLE GROUP SUBTYPE 'GRP 1a', PARTITION 10 <= VALUES < 
           100 GROUP SUBTYPE 'GRP 1b' INSERT OFF PAGE LOADABLE, PARTITION OTHERS DYNAMIC THRESHOLD 2),
    (PARTITION VALUES = 40 GROUP NAME 'GRP 2' INSERT OFF COLUMN LOADABLE)
      SUBPARTITION BY RANGE(B) (PARTITION 0 <= VALUES < 10 GROUP SUBTYPE 'GRP 2a', PARTITION OTHERS DYNAMIC THRESHOLD 2),
    (PARTITION OTHERS));

```

Create a heterogeneous partitioned table with dynamic range partitioning enabled. This table has two first-level ranges. The first partition has a range of 10-20. The second partition has a target value of 30. Each partition has it own subpartition. The first subpartition has a range of 100-150. The second subpartition has a target value of 200. Both subpartitions have dynamic range partitioning enabled with a threshold of 3.

```
CREATE COLUMN TABLE T4 (A INT, B INT NOT NULL) PARTITION BY RANGE (A)
   ((PARTITION 10 <= VALUES < 20) SUBPARTITION BY RANGE (B) (PARTITION 100 <= VALUES < 150, PARTITION OTHERS DYNAMIC THRESHOLD 3),
    (PARTITION VALUES = 30) SUBPARTITION BY RANGE (B) (PARTITION VALUES = 200, PARTITION OTHERS DYNAMIC THRESHOLD 3));
```

Create a heterogeneous partitioned table. There are three first-level \(10-20, 30, and 40-50\), each with different properties defined. The first two partitions share the same subpartition. There are two second-level hash partitions, each referencing the same group of columns \(A, C\). On the first subpartition, column A has a DATE data type, with the precision YEAR applied at the subpartition level.

```
CREATE COLUMN TABLE A5 (A DATE, B INT, C INT) PARTITION BY RANGE (B) 
   ((PARTITION 10 <= VALUES < 20 INSERT ON PAGE LOADABLE, PARTITION VALUES = 30 COLUMN LOADABLE GROUP NAME 'HR') 
       SUBPARTITION BY HASH (YEAR(a), c) PARTITIONS 4,
    (PARTITION 40 <= VALUES < 50 PAGE LOADABLE GROUP NAME 'HR') 
       SUBPARTITION BY HASH (YEAR(a), c) PARTITIONS 4);
```

Create a multilevel heterogeneous partitioned table and then applies the *<load\_unit\>* attribute first by partition number \(1\) and then to partition range \(10 to 20\).

```
CREATE COLUMN TABLE T6 (a INT, b INT) PARTITION BY RANGE(a) 
   ((PARTITION 10 <= VALUES < 20) SUBPARTITION BY RANGE (b) (PARTITION VALUES=100));

ALTER TABLE T4 ALTER PARTITION 1 COLUMN LOADABLE;
ALTER TABLE T4 ALTER PARTITION RANGE (a) ((PARTITION 10 <= VALUES < 20) 
   SUBPARTITION BY RANGE (b) (PARTITION VALUES = 100)) PAGE LOADABLE;
```

Creates a heterogeneous partitioned table with a dynamic distance interval of 200.

```
CREATE TABLE A7 (A int NOT NULL, B int) PARTITION BY RANGE (A) (
  PARTITION 1 <= VALUES < 100,
  PARTITION 100 <= VALUES < 200,
  PARTITION OTHERS DYNAMIC DISTANCE 200 PAGE LOADABLE);
```

Creates a table with decreasing numbered dynamic ranges.

```
CREATE TABLE A8 (C1 INT NOT NULL) PARTITION BY RANGE (C1) (
  PARTITION OTHERS DYNAMIC DECREASING THRESHOLD 2);
```

Creates a table with dynamic range numbers that both increase and decrease.

```
CREATE TABLE A9 (C1 INT NOT NULL) PARTITION BY RANGE (C1) (
  PARTITION OTHERS DYNAMIC BIDIRECTIONAL INTERVAL 2);
```

Create a dynamic range table with a check interval of 20 minutes:

```
CREATE TABLE A10 (C1 INT NOT NULL) PARTITION BY RANGE (C1) (
  (PARTITION 1 <= VALUES < 100, PARTITION OTHERS DYNAMIC INTERVAL 10)) DYNAMIC RANGE CHECK INTERVAL 20;
```

Created a partitioned table with some partitions movable and some not.

```
CREATE COLUMN TABLE A11 (C1 INT, C2 INT) PARTITION BY RANGE (C1) (
  (PARTITION VALUE = 1) SUBPARTITION BY RANGE (C2) (PARTITION VALUE = 1, PARTITION VALUE = 2 MOVABLE, PARTITION VALUE = 3 NOT MOVABLE),
  (PARTITION VALUE = 2 MOVABLE) SUBPARTITION BY RANGE (C2) (PARTITION VALUE = 1, PARTITION VALUE = 2 MOVABLE, PARTITION VALUE = 3 NOT MOVABLE),
  (PARTITION VALUE = 3 NOT MOVABLE) SUBPARTITION BY RANGE (C2) (PARTITION VALUE = 1, PARTITION VALUE = 2 MOVABLE, PARTITION VALUE = 3 NOT MOVABLE)
  );
```

Create a heterogeneous partitioned table with a distance of 200.

```
CREATE TABLE A6 (C1 INT NOT NULL, C2 INT) PARTITION BY RANGE (C1) 
   ((PARTITION 1 <= VALUES < 100, PARTITION 100 <= VALUES < 200, PARTITION OTHERS DYNAMIC DISTANCE 200 PAGE LOADABLE ));
```



</dd>
</dl>


<dl>
<dt><b>

Data masking

</b></dt>
<dd>

Create a table that masks the data in the SSN column:

```
CREATE ROW TABLE PERSONAL_INFO (SSN NVARCHAR(20)) WITH MASK (SSN USING '****');
```

Create a table that masks the data in the SSN column by session user:

```
CREATE TABLE PERSONAL_INFO (SSN VARCHAR(20)) WITH SESSION USER MASK ( SSN USING '****' );
```



</dd><dt><b>

Constraints

</b></dt>
<dd>

Create table C2 that has the same column data types and NOT NULL constraints as table A without any data.

```
CREATE ROW TABLE C2 AS (SELECT * FROM A) WITH NO DATA;
```

Create table F that has a foreign key that references column A of table R with update cascade option.

```
CREATE ROW TABLE R (A INT PRIMARY KEY, B NVARCHAR(10));
 CREATE ROW TABLE F (FK INT, B NVARCHAR(10), FOREIGN KEY(FK) REFERENCES R ON UPDATE CASCADE);
```

Create a self-referencing foreign key.

```
CREATE ROW TABLE SELF(A INTEGER PRIMARY KEY, B INTEGER);
ALTER TABLE SELF ADD CONSTRAINT FK_T1 FOREIGN KEY(B) REFERENCES SELF(A);
```

Create a cyclic foreign key.

```
CREATE ROW TABLE GRAND_PARENT (A INT, I INT, B INT, PRIMARY KEY (A) );
CREATE ROW TABLE PARENT (A INT, I INT, B INT, PRIMARY KEY (A) );
ALTER TABLE PARENT ADD CONSTRAINT FK_CONSTRAINT_FROM_PARENT_TO_GRAND_PARENT FOREIGN KEY (B) REFERENCES GRAND_PARENT (A) ON DELETE CASCADE;
ALTER TABLE GRAND_PARENT ADD CONSTRAINT FK_CONSTRAINT_FROM_GRAND_PARENT_TO_PARENT FOREIGN KEY (B) REFERENCES PARENT (A) ON DELETE CASCADE;
```



</dd><dt><b>

Fuzzy searching

</b></dt>
<dd>

Create table T2 with a fuzzy search index and a fuzzy search mode.

```
CREATE COLUMN TABLE T2 (KEY INT, COL1 NVARCHAR(10) FUZZY SEARCH INDEX ON, COL2 NVARCHAR(10) FUZZY SEARCH MODE 'POSTCODE');
```



</dd>
</dl>


<dl>
<dt><b>

Temporary tables

</b></dt>
<dd>

Create a session-level global temporary table.

```
CREATE GLOBAL TEMPORARY TABLE T (C1 INT, C2 INT) ON COMMIT PRESERVE ROWS;
```

Create a transaction-level global temporary table.

```
CREATE GLOBAL TEMPORARY TABLE T (C1 INT, C2 INT) ON COMMIT DELETE ROWS;
```

Create a session-level global temporary table.

```
CREATE GLOBAL TEMPORARY TABLE T (C1 INT, C2 INT) ON COMMIT PRESERVE ROWS;
```

Create transaction-level global temporary table.

```
CREATE GLOBAL TEMPORARY TABLE T (C1 INT, C2 INT) ON COMMIT DELETE ROWS;
```



</dd><dt><b>

Arrays

</b></dt>
<dd>

Create a new column table with an ARRAY column.

```
CREATE COLUMN TABLE T1 ( ID INT PRIMARY KEY, C1 INT ARRAY );
```

```
CREATE COLUMN TABLE T2 ( ID INT PRIMARY KEY, C1 INT ARRAY (1, 10) );
```

Create a new column table with an ARRAY column that restricts the maximum number\(10\) of elements.

```
CREATE COLUMN TABLE T3 ( ID INT PRIMARY KEY, C1 INT ARRAY (10) );
```

Create a new column table with an ARRAY column that restricts the minimum number\(1\) of elements.

```
CREATE COLUMN TABLE T4 ( ID INT PRIMARY KEY, C1 INT ARRAY (1, *) );
```

Create a new column table with an ARRAY column that doesn't allow duplicates of non-NULL values.

```
CREATE COLUMN TABLE T5 ( ID INT PRIMARY KEY, C1 INT ARRAY (1, 5) WITHOUT DUPLICATES );
```

Create a new column table with an ARRAY column that has a default value.

```
CREATE COLUMN TABLE T6 ( ID INT PRIMARY KEY, C1 INT ARRAY DEFAULT ARRAY() );
```



</dd><dt><b>

Persistent memory

</b></dt>
<dd>

Create a table with PERSISTENT MEMORY enabled at the table level:

```
CREATE COLUMN TABLE myTable1 (C1 INT, C2 NVARCHAR (10)) PERSISTENT MEMORY ON;
```

Create a table with PERSISTENT MEMORY enabled for the specified range partitions:

```
CREATE COLUMN TABLE myTable2 (C1 INT) PARTITION BY RANGE (C1) (PARTITION '0' <= VALUES < '10' PERSISTENT MEMORY ON, PARTITION OTHERS PERSISTENT MEMORY OFF);
```

Create a table with PERSISTENT MEMORY enabled for the specified columns:

```
CREATE COLUMN TABLE PMTABLE (C1 INT PERSISTENT MEMORY ON, C2 NVARCHAR (10), C3 INT PERSISTENT MEMORY OFF);
```



</dd><dt><b>

NUMA node preferences examples

</b></dt>
<dd>

Creates a column table with its NUMA-node preference set at the table level on NUMA node indexes 1, 3-5. Table T1 and all its data are allocated with a preferred NUMA allocation type on NUMA node index 1. If node 1 has an insufficient amount of memory, then SAP HANA uses the node index from the range 3-5 with the shortest distance to node 1. The preferred list of NUMA node indexes is updated in the catalog when the table is created:

```
CREATE COLUMN TABLE T1(colint INT, colnvarchar NVARCHAR(10)) NUMA NODE ('1', '3' TO '5');
```

Creates a column table with its NUMA-node preference set for a partition on node index 2, and with the partition data allocated on NUMA node index 2. Data that does not belong to this partition is allocated on the node determined by the current HASH scheme available in the attribute engine:

```
CREATE COLUMN TABLE T1(colint INT, colnvarchar NVARCHAR(10)) PARTITION BY RANGE (colint) (PARTITION '0' <= VALUES < '20' NUMA NODE ('2'))
```

Creates a column table with its NUMA-node preference set for an integer column on node index 3, and with the data for this column allocated to node 3. Columns that do not have their NUMA node preference set inherit their preference from the table- or partition-level settings, if any partitions are set on that column. Otherwise, data is allocated with the current HASH scheme that is avail

```
CREATE COLUMN TABLE T1(colint INT NUMA NODE(3), colnvarchar NVARCHAR(10)) NUMA NODE ('5');
```

able in the attribute engine. The column colvarchar inherits NUMA node preference from the table-level settings \(in this example, node index 5\):

Creates table T1 with a configuration that is similar to existing table T2, which has a NUMA NODE preference for node index 3:

```
CREATE COLUMN TABLE T1 LIKE T2; 
```

Creates table T1 with a configuration that is similar to existing table T2 but does not include a NUMA node, so NUMA NODE preferences are not be created on T1:

```
CREATE COLUMN TABLE T1 LIKE T2 WITHOUT NUMA NODE;
```



</dd><dt><b>

LOAD UNIT examples

</b></dt>
<dd>

Create a table, T, that is page loadable:

```
CREATE COLUMN TABLE T (C1 INT, C2 NVARCHAR (10)) PAGE LOADABLE;
```



</dd><dt><b>

WITH ASSOCIATION

</b></dt>
<dd>

These examples demonstrate the creation of a table with associations to other tables.

Execute the following statements to create and populate a table called t1:

```
CREATE TABLE t1(x1 INT, y1 INT);
INSERT INTO t1 VALUES(0, 0);
INSERT INTO t1 VALUES(1, 1);
INSERT INTO t1 VALUES(2, 2);
INSERT INTO t1 VALUES(3, 3);
```

Next, create and populate table t2 and set up an association from t2 to t1 and use the WITH DEFAULT FILTER clause to set the predicate filter to y1< 3:

```
CREATE TABLE t2(x2 INT, y2 INT) WITH ASSOCIATIONS 
(JOIN t1 AS a ON a.x1 = x2 WITH DEFAULT FILTER y1 < 3);
INSERT INTO t2 VALUES(2, 0);
INSERT INTO t2 VALUES(3, -1);
INSERT INTO t2 VALUES(4, -2);
INSERT INTO t2 VALUES(5, -3);
```

Now, the following two statements return the same result \(2, 2\), as we have set the default predicate filter to y1<3:

```
SELECT * FROM t2:a;
SELECT * FROM t2:a[y1<3];
```

However, if you run the following statement, the result is \(3, 3\), as the specified filter overrides the default:

```
SELECT * FROM t2:a[y1>1];
```

Similarly, the following two statements return the same result, \(2; None; None; None\):

```
SELECT a.x1 FROM t2;
SELECT a[y1<3].x1 FROM t2;
```

However, the following statement overrides the default filter and returns \(2; 3; None; None\):

```
SELECT a[y1>1].x1 FROM t2;
```

Execute the following statements to create and populate table t1:

```
CREATE TABLE t1(x1 INT, y1 INT);
INSERT INTO t1 VALUES(0, 0);
INSERT INTO t1 VALUES(1, 1);
INSERT INTO t1 VALUES(2, 2);
INSERT INTO t1 VALUES(3, 3);
```

Execute the following statements to create and populate table t2 with associations to table t1 and with the default filter set to filter column values to values less than 3:

```
CREATE TABLE t2(x2 INT, y2 INT) WITH ASSOCIATIONS (JOIN t1 AS a ON a.x1 = x2 WITH DEFAULT FILTER y1 < 3);
INSERT INTO t2 VALUES(2, 0);
INSERT INTO t2 VALUES(3, -1);
INSERT INTO t2 VALUES(4, -2);
INSERT INTO t2 VALUES(5, -3);

```

Now, executing ***SELECT \* FROM t2:a;*** returns the following:

```
2,2
```

However, executing ***SELECT \* FROM t2:a\[y1\>1\];*** overrides the default filter to return the following values:

```
2,2
3,3
```

If you execute ***SELECT a.x1 FROM t2;***, the following values are returned:

```
2,
--None
--None
--None
```

Executing ***SELECT a\[y1\>1\].x1 FROM t2;*** returns the following values:

```
2,
3,
--None
--None
```



</dd>
</dl>

**Related Information**  


[Non-Heterogeneous Create Partition Clauses](non-heterogeneous-create-partition-clauses-ca6a99b.md "Defines the various partitioning clauses available for non-heterogeneous partitions when creating a new table.")

[Heterogeneous Create Partition Clauses](heterogeneous-create-partition-clauses-d496e58.md "Defines the various partitioning clauses available for heterogeneous partitions when creating a new table.")

[CREATE SEQUENCE Statement \(Data Definition\)](create-sequence-statement-data-definition-20d5092.md "Creates a sequence that generates primary key values that are unique across multiple tables, and for generating default values for a table.")

[SELECT Statement \(Data Manipulation\)](select-statement-data-manipulation-20fcf24.md "Queries data from the database.")

[ALTER TABLE Statement \(Data Definition\)](alter-table-statement-data-definition-20d329a.md "Alters a base or temporary table. See the ALTER VIRTUAL TABLE statement for altering virtual tables.")

[CREATE VIRTUAL TABLE Statement \(Data Definition\)](create-virtual-table-statement-data-definition-d2a0406.md "Creates a virtual table at a remote source.")

[SAP HANA Native Storage Extension](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2024_3_QRC/en-US/4efaa94f8057425c8c7021da6fc2ddf5.html "SAP HANA native storage extension is a general-purpose, built-in warm data store in SAP HANA that lets you manage less-frequently accessed data without fully loading it into memory. It integrates disk-based or flash-drive based database technology with the SAP HANA in-memory database for an improved price-performance ratio.") :arrow_upper_right:

[Table Partitioning](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2024_3_QRC/en-US/c2ea130bbb571014b024ffeda5090764.html "The partitioning feature of the SAP HANA database splits column-store tables horizontally into disjunctive sub-tables or partitions. In this way, large tables can be broken down into smaller, more manageable parts. Partitioning is typically used in multiple-host systems, but it may also be beneficial in single-host systems.") :arrow_upper_right:

[Table Placement](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2024_3_QRC/en-US/22888f9344954f258284d2dd936d0d0a.html "Table classification and table placement configuration, enhanced by partitioning, build the foundation for controlling the data distribution in a SAP HANA scale-out environment.") :arrow_upper_right:

[Introduction to SQL](../introduction-to-sql-209f502.md "This chapter describes the SAP HANA database implementation of Structured Query Language (SQL).")

[Predicates](../predicates-20a2ab2.md "")

[Hybrid LOBs (Large Objects)](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2024_3_QRC/en-US/61ab21a1972846e0aa0b9a989ce4867a.html "To save memory you can store LOB data on disk, in this case the data is only loaded into memory when it is needed. Alternatively, you can use the configurable Hybrid LOB feature which is flexible and stores LOBs either on disk or in memory depending on their size.") :arrow_upper_right:

[CREATE REMOTE SOURCE Statement \(Access Control\)](create-remote-source-statement-access-control-20d4834.md "Defines an external data source that can connect to the SAP HANA database.")

[Data Types](../data-types-20a1569.md "A data type defines the characteristics of a data value. A special value of NULL is included in every data type to indicate the absence of a value.")

[TABLES System View](../../020-System-Views-Reference/021-System-Views/tables-system-view-2101973.md "Provides information about tables in the database.")

[TABLE\_COLUMNS System View](../../020-System-Views-Reference/021-System-Views/table-columns-system-view-2100d33.md "Provides information about available table columns.")

[SAP HANA Cloud Configuration Parameter Reference](https://help.sap.com/viewer/138dcf7d779543608917a2307a6115f2/2024_3_QRC/en-US/4b4d88980622427ab2d6ca8c05448166.html "Reference documentation for public configuration parameters in SAP HANA Cloud.") :arrow_upper_right:

[SAP HANA Cloud, SAP HANA Database Security Guide](https://help.sap.com/viewer/a1317de16a1e41a6b0ff81849d80713c/2024_3_QRC/en-US/c3d9889e3c9843bdb834e9eb56f1b041.html#loioc3d9889e3c9843bdb834e9eb56f1b041 "The SAP HANA Cloud, SAP HANA Database Security Guide is the entry point for all information relating to the secure operation and configuration of SAP HANA Cloud, SAP HANA database.") :arrow_upper_right:

