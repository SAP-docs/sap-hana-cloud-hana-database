<!-- loio20d329a6751910149d5fdbc4800f92ff -->

# ALTER TABLE Statement \(Data Definition\)

Alters a base or temporary table. See the ALTER VIRTUAL TABLE statement for altering virtual tables.



<a name="loio20d329a6751910149d5fdbc4800f92ff__sql_alter_table_syntax"/>

## Syntax

```
ALTER TABLE <table_name>
   | <column_clauses>
   | <system_versioning_configuration>
   | <add_drop_application_time_period>
   | <lob_reorganize_clause>
   | <clear_column_join_data_statistics_clause>
   | <constraint_clauses>
   | <primary_key_clauses>
   | <preload_clause>
   | <table_conversion_clause>
   | <association_clauses>
   | <with_annotation_clause>
   | <partition_clauses>
   | <table_load_unit_clause>
   | <alter_persistent_memory_spec_clause>
   | <replica_clauses>
   | <auto_merge_option>
   | <unload_priority>
   | <trigger_option>
   | <group_option_clauses> 
   | <unset_group_option>
   | <row_order_clauses>
   | <unused_retention_period>
   | <reclaim_data_space_clause>
   | <owner_to_clause>
   | <alter_mask_settings_clause>
   | <set_movable_clause>
   | <convert_index_type>
   | <numa_node_preference_clause>
```



<a name="loio20d329a6751910149d5fdbc4800f92ff__sql_alter_table_syntax_elements"/>

## Syntax Elements


<dl>
<dt><b>

*<table\_name\>*

</b></dt>
<dd>

Specifies the identifier of the table to be altered, with optional schema name.

```
<table_name> ::= [ <schema_name>.]<identifier>

<schema_name> ::= <identifier>
```



</dd><dt><b>

*<column\_clauses\>*

</b></dt>
<dd>

Defines the column operations you can perform.

```
   [<add_columns_clause>]
   [<alter_columns_clause>] 
   [<drop_columns_clause>] 
```


<dl>
<dt><b>

*<add\_columns\_clause\>*

</b></dt>
<dd>

Adds one or more columns to the specified table.

```
<add_columns_clause> ::= ADD ( <column_list > )

<column_list> ::= <column_specification> [,...] [ ONLINE [ PREFERRED ] ]

<column_specification> ::=  
 <column_name> { [ <column_definition> ] [ <column_constraint_short> ] [ COMMENT <string_literal> ] }
      [ <add_column_load_unit> ] 

<add_column_load_unit> ::= <column_name> <add_load_unit>
```


<dl>
<dt><b>

*<column\_definition\>*

</b></dt>
<dd>

Specifies a definition for a column.

```
<column_definition> ::=  
 [ { <data_type> | <lob_data_type> } <ddic_data_type> ] 
 [ <default_value_clause> ]
 [ <col_gen_as_expression> | <col_gen_as_ident> ]
 [ <col_calculated_field> ]
 [ <fuzzy_search_index> ] 
 [ <fuzzy_search_mode> ] 
 [ <alter_persistent_memory_spec_clause> ]
```


<dl>
<dt><b>

*<data\_type\>*

</b></dt>
<dd>

Specifies the column data types.

```
<data_type> ::= 
 DATE 
 | TIME 
 | SECONDDATE 
 | TIMESTAMP 
 | TINYINT 
 | SMALLINT 
 | INTEGER 
 | BIGINT 
 | SMALLDECIMAL 
 | REAL 
 | DOUBLE 
 | NVARCHAR [ (<unsigned_integer>) ] 
 | VARBINARY [ (<unsigned_integer>) ] 
 | DECIMAL [ (<unsigned_integer> [, <unsigned_integer> ] ) ] 
 | FLOAT [ (<unsigned_integer>) ] 
 | BOOLEAN
```

For tables with time-selection partitioning, the data type for the time-selection column must be NVARCHAR\(8\).



</dd><dt><b>

*<lob\_data\_type\>*

</b></dt>
<dd>

Specifies a LOB data type.

```
<lob_data_type> ::= 
<lob_type_name> [MEMORY THRESHOLD <memory_threshold_value>] 

<lob_type_name> ::= 
 BLOB 
 | NCLOB 
```

*<memory\_threshold\_value\>* controls whether LOB data should be stored in memory, according to the following conditions:

-   If *<memory\_threshold\_value\>* is not provided, then a hybrid LOB with a memory threshold of 1000 bytes is created by default.

-   If *<memory\_threshold\_value\>* is provided and its LOB size is bigger than the memory threshold value, then LOB data is stored on disk.

-   If *<memory\_threshold\_value\>* is provided and its LOB size is equal or less than the memory threshold value, then LOB data is stored in memory.

-   If *<memory\_threshold\_value\>* is NULL, then all LOB data is stored in memory.

-   If *<memory\_threshold\_value\>* is 0, then all LOB data is stored on disk.




</dd><dt><b>

*<ddic\_data\_type\>*

</b></dt>
<dd>

Specifies a DDIC data type.

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

*<default\_value\_clause\>*

</b></dt>
<dd>

Specifies a value to be assigned to the column if an INSERT statement does not provide a value for the column.

```
<default_value_clause> ::= DEFAULT <default_value_exp>

<default_value_exp> ::= 
 NULL 
 | <string_literal><signed_numeric_literal> 
 | <unsigned_numeric_literal> 
 | <datetime_value_function>
 | <string_value_function>

<datetime_value_function> ::= 
CURRENT_DATE 
 | CURRENT_TIME 
 | CURRENT_TIMESTAMP 
 | CURRENT_UTCDATE 
 | CURRENT_UTCTIME 
 | CURRENT_UTCTIMESTAMP

<string_value_function> ::=
 SYSUUID
 | CURRENT_USER
 | CURRENT_SCHEMA
 | SESSION_USER
```



</dd><dt><b>

*<col\_gen\_as\_expression\>*

</b></dt>
<dd>

Specifies the expression to generate the column value in runtime.

```
<col_gen_as_expression> ::= GENERATED ALWAYS AS <expression>
```

Generated columns are only supported in column store table definitions, and can only reference base columns that are defined prior to them in the DDL statement \(that is, to the left of them\). You cannot define a default for a generated column, and they cannot be used as part of a primary key or unique constraint. *<expression\>* must not contain a non-deterministic function.

You cannot drop a base column that is referenced by a generated column.



</dd><dt><b>

*<col\_gen\_as\_ident\>*

</b></dt>
<dd>

Specifies an identity column. Only one identity column is allowed per table.

```
<col_gen_as_ident> ::= GENERATED { ALWAYS | BY DEFAULT } AS IDENTITY [(<sequence_option>)]

<sequence_option> ::= {
   <sequence_param_list>
   | RESET BY <subquery>
   | <sequence_param_list>
   RESET BY <subquery> }

<sequence_param_list> ::= <sequence_parameter> [, <sequence_parameter> ] [,...]

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
 RESET BY <subquery>
```

There are two types of IDENTITY columns: GENERATED ALWAYS, and GENERATED BY DEFAULT:


<dl>
<dt><b>

GENERATED ALWAYS

</b></dt>
<dd>

A GENERATED ALWAYS AS IDENTITY column increments based solely on the sequence parameter settings \(*<sequence\_param\_list\>*\). With the exception of changes to the RESET BY definition, the sequence defined for a GENERATED ALWAYS IDENTITY column cannot be altered or reset after it has been set, and inserting a value into a GENERATED ALWAYS identity column fails and returns an error.



</dd><dt><b>

GENERATED BY DEFAULT

</b></dt>
<dd>

A GENERATED BY DEFAULT IDENTITY column increments using the sequence parameter settings \(*<sequence\_param\_list\>*\) only when no identity value is specified in the INSERT statement \(that is, the identity column is left out of the insert column list\). When a value is specified for the identity column during the INSERT, then the specified value is inserted \(assuming the value does not already exist\) and the following behavior occurs with respect to the value of the identity column:

-   If the specified value is higher than the existing identify value with a positive increment, then this resets the current sequence value to an allowable sequence value that is equal to the specified value, or the next one lower than the specified value.

-   If the specified value is lower than the existing value with a negative increment, then this resets the current sequence value to an allowable sequence value that is equal to the specified value, or the next one higher than the specified value.

-   Otherwise, the current sequence value is not reset.




</dd>
</dl>

Identity columns are supported in global and local temporary tables, both for row store and column store tables. They can be added to, or dropped from, a table. However, they cannot be altered.

If RESET BY *<subquery\>* is specified, then during the restart of the database, the database automatically executes the subquery and restarts the sequence value with the returned value. If RESET BY is not specified, then the sequence value is stored persistently in database. During the restart of the database, the next value of the sequence is generated from the saved sequence value.

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

The data type of a calculated field column can be a default value. Also, calculated field columns can reference base columns and other calculated field columns.

The maximum value of a recursive calculated field is 16.

Dropping or altering the base columns of a calculated field is not possible.



</dd><dt><b>

*<fuzzy\_search\_index\>*

</b></dt>
<dd>

Turns a fuzzy search index on or off. OFF is the default.

```
<fuzzy_search_index> ::= FUZZY SEARCH INDEX [ON | OFF]
```



</dd><dt><b>

*<fuzzy\_search\_mode\>*

</b></dt>
<dd>

Sets the fuzzy search mode with the value of *<string\_literal\>*. If NULL is specified, then the fuzzy search mode is reset.

```
<fuzzy_search_mode> ::= FUZZY SEARCH MODE [ <string_literal> | NULL ]
```



</dd>
</dl>



</dd><dt><b>

*<column\_constraint\_short\>*

</b></dt>
<dd>

The description of the syntax for *<column\_constraint\_short\>* and *<column\_constraint\>* are the same except that *<column\_constraint\_short\>* does not include syntax for specifying *<unique\_specification\>*, and is used specifically when adding a column \(*<add\_columns\_clause\>*\).

```
<column_constraint_short> ::= 
 NULL 
 | NOT NULL 
 | [<constraint_name_definition>] <references_specification>
```



</dd><dt><b>

*<column\_constraint\>*

</b></dt>
<dd>

Specifies constraints on a column.

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

Allows NULL values in the column. If NULL is specified it is not considered a constraint, it represents that a column that may contain a null value. The default is NULL.



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

For *<references\_specification\>*, see [References Specification](alter-table-statement-data-definition-20d329a.md#loio20d329a6751910149d5fdbc4800f92ff__references_specification).



</dd><dt><b>

*<add\_load\_unit\>*

</b></dt>
<dd>

When adding a column to the specified table, specifies how to load data into memory when the table is queried. Specifying the load unit is only supported on column-store tables.

```
<add_load_unit> ::= { COLUMN | PAGE } LOADABLE
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



</dd>
</dl>



</dd>
</dl>



</dd><dt><b>

*<alter\_columns\_clause\>*

</b></dt>
<dd>

Alters one or more column definitions.

```
<alter_columns_clause> ::= ALTER { <column_list > | <alter_column_load_unit> }

<column_list> ::= ( <column_specification> [, <column_specification> [,...] ] ) [ ONLINE [ PREFERRED ] ]

<column_specification> ::=  
 <column_name> { [ <column_definition> ] [ <column_constraint> ] [ COMMENT <string_literal> ] }

<alter_column_load_unit> ::= ( <column_name> ALTER <alter_load_unit> [ ,...] )
```


<dl>
<dt><b>

ONLINE \[ PREFERRED \]

</b></dt>
<dd>

Allows alter column operations that do not serialize with concurrent DML operations. ONLINE is only supported for column-store, non-replicated tables when altering a column to a LOB type without adding a NOT NULL constraint, or when altering only the default value and/or the nullability of a column. Altering a column in a supported case results in an alter column operation that only acquires a shared table lock. The operation is not serialized with concurrent DML operations, but is serialized with any other concurrent DDL on the table, including other ONLINE DDL. The default value must be a constant value and not a function.

When PREFERRED is specified, if ONLINE execution is not supported, then a SQL warning message appears, and the alter operation executes in table x-lock mode.



</dd><dt><b>

*<alter\_load\_unit\>*

</b></dt>
<dd>

When altering a column definition, specifies how to load data into memory when the table is queried. Specifying the load unit is only supported on column-store tables.

```
<alter_load_unit> ::= { COLUMN | PAGE | DEFAULT } LOADABLE
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



</dd><dt><b>

DEFAULT LOADABLE

</b></dt>
<dd>

If you specify DEFAULT, then there is no explicit preference for the loading unit that is used when the results are loaded from the table. If there is an inherited loading unit from another object, then that loading unit is used.



</dd>
</dl>



</dd>
</dl>



</dd><dt><b>

*<drop\_columns\_clause\>*

</b></dt>
<dd>

Removes one or more columns from the specified table.

```
<drop_columns_clause> ::= DROP ( <column_name> [, ...] ) [ ONLINE [ PREFERRED ] ]
```


<dl>
<dt><b>

ONLINE \[ PREFERRED \]

</b></dt>
<dd>

Allows drop column operations that do not serialize with concurrent DML operations. ONLINE is only supported for column-store, non-replicated tables when dropping a non-paged column to a LOB type.

When PREFERRED is specified, if ONLINE execution is not supported, then a SQL warning message appears, and the drop operation executes in table x-lock mode.



</dd>
</dl>



</dd>
</dl>



</dd><dt><b>

*<with\_annotation\_clause\>*

</b></dt>
<dd>

Alters table-, column-, and parameter-level annotations. You can reference annotations in subsequent queries to filter results.

```
<with_annotation_clause> ::= 
 WITH ANNOTATIONS ( { [ <alter_table_annotations> ] [ <alter_column_annotations> ] [ <alter_parameter_annotations> ] } )

<alter_table_annotations> ::= { [ <key_set_operation> ] [ <key_unset_operation> ] } ] 

<alter_column_annotations> ::= <column_annotation> [ <]column_annotation> […] ]
<column_annotation> ::= COLUMN <column_ref> { <key_set_operation> | <key_unset_operation> }

<alter_parameter_annotations> ::= <parameter_annotation> [ <parameter_annotation> […] ]
<parameter_annotation> ::= PARAMETER <column_ref> { <key_set_operation> | <key_unset_operation> }

<key_set_operation> ::= SET <key_value_pair_list> 
<key_unset_operation> ::= UNSET <key_list>

<key_value_pair_list> ::= <key_value_pair> [, <key_value_pair> [,…] ]
<key_value_pair> ::= '<key>'='<value>'
<key_list> ::= { '<key>'[,'<key>'[,…]] | ALL }

<column_ref> ::= <identifier>
<key> ::= <string>
<value> ::= <string>
```

While you must specify annotation on at least one object with the WITH ANNOTATION clause \(table, column, or parameter\), there is no limit on the number of annotations or types of annotations you can specify.

*<key\>* and *<value\>* represent the annotations you are configuring for the object \(table, column, or parameter\).



</dd><dt><b>

*<system\_versioning\_configuration\>*

</b></dt>
<dd>

Alters system-versioning settings for a table.

```
<system_versioning_configuration> ::= { 
<add_generated_always_column>
 | <convert_column_to_generated_always_column>
 | <add_drop_periods>
 | <add_drop_system_versioning> 
}

<add_generated_always_column> ::= {
ADD ( <valid_from_column_name> TIMESTAMP NOT NULL GENERATED ALWAYS AS ROW START [ COMMIT ] )
 | ADD ( <valid_to_column_name> TIMESTAMP NOT NULL GENERATED ALWAYS AS ROW END )
}

<convert_column_to_generated_always_column> ::= {
ALTER ( <valid_from_column_name> TIMESTAMP NOT NULL GENERATED ALWAYS AS ROW START [ COMMIT ] )
 | ALTER ( <valid_to_column_name> TIMESTAMP NOT NULL GENERATED ALWAYS AS ROW END )
 | ALTER ( <valid_to_column_name> TIMESTAMP NOT NULL GENERATED ALWAYS AS ROW COMMIT )
}

<add_drop_periods> ::= {
ADD PERIOD FOR SYSTEM_TIME ( <valid_from_column_name>, <valid_to_column_name> )
 | DROP PERIOD FOR SYSTEM_TIME
}
                           
<add_drop_system_versioning> :: = {
 ADD SYSTEM VERSIONING HISTORY TABLE <history_table_name> [ [ NOT ] VALIDATED ]
 | DROP SYSTEM VERSIONING  
}
```


<dl>
<dt><b>

*<valid\_from\_column\_name\>*

</b></dt>
<dd>

In both *<history\_table\_definition\>* and *<system\_versioned\_table\_definition\>*, this column defines the column that holds the start time of the validity period. Defining a column as a ROW START column initializes the column with the timestamp of the start of the current transaction. If a column is defined as ROW START COMMIT the column is initialized with a timestamp determined at transaction commit. GENERATED ALWAYS is the mechanism by which the system automatically updates the TIMESTAMP value in the column.



</dd><dt><b>

*<valid\_to\_column\_name\>*

</b></dt>
<dd>

In both *<history\_table\_definition\>* and *<system\_versioned\_table\_definition\>*, this column defines the column that holds the end time of the validity period. Defining a column as a ROW END column initializes the column with the timestamp value '9999-12-31 23:59:59.9999999'. Defining a *<valid\_to\_column\_name\>* in *<history\_table\_definition\>* as ROW COMMIT initializes the column with a timestamp determined at transaction commit.



</dd><dt><b>

ADD PERIOD FOR SYSTEM\_TIME \( *<valid\_from\_column\_name\>*, *<valid\_to\_column\_name\>* \) | DROP PERIOD FOR SYSTEM\_TIME

</b></dt>
<dd>

Adds or drops a validity period.

For the ADD syntax, *<valid\_from\_column\_name\>* is the column containing the start time value, and *<valid\_to\_column\_name\>* is the column containing the end time value.



</dd><dt><b>

ADD SYSTEM VERSIONING HISTORY TABLE *<history\_table\_name\>* | DROP SYSTEM VERSIONING

</b></dt>
<dd>

Enables or disable system-versioning for the table.

For the ADD syntax, *<history\_table\_name\>* must already exist and not be associated with any other system-versioned table.



</dd><dt><b>

\[ \[ NOT \] VALIDATED \]

</b></dt>
<dd>

Specifies whether to check if *<history\_table\_name\>* is empty. If VALIDATED is specified \(the default\), an exception is raised if *<history\_table\_name\>* is not empty. If NOT VALIDATED is specified, no emptiness check is performed on *<history\_table\_name\>*, and no exception is raised even if the history table has data in it.

After you import a system-versioned table and its associated history table, you execute an ALTER TABLE statement to enable system-versioning. Since the history table is not empty, you must specify NOT VALIDATED to bypass the emptiness check.



</dd>
</dl>



</dd><dt><b>

*<add\_drop\_application\_time\_period\>*

</b></dt>
<dd>

Defines the application-time period for the table, or drops the existing one.

```
ADD PERIOD FOR APPLICATION_TIME ( <validfrom_column_name>, <validto_column_name> )
| DROP PERIOD FOR APPLICATION_TIME
```

Adding a period adds an implicit constraint that *<validfrom\_column\_name\>* must be less than *<validto\_column\_name\>*.



</dd><dt><b>

*<lob\_reorganize\_clause\>*

</b></dt>
<dd>

Applies the midsizelob\_threshold system property to the specified LOB column or to all LOB columns in the specified table.

```
<lob_reorganize_clause> ::= 
 LOB REORGANIZE [(<column-list>)] [ ONLINE [ PREFERRED ] ]Clears the join data statistics
                     for the specified table.
```

If a comma-separated list is not provided, then the midsizelob\_threshold system property is applied to any LOB column in the specified table.


<dl>
<dt><b>

ONLINE

</b></dt>
<dd>

Allows LOB reorganize operations that do not serialize with concurrent DML operations. ONLINE is only supported for column-store, non-multistore tables, where specifying ONLINE performs a LOB reorganize operation that only acquires a shared table lock. The operation is still serialized with other concurrent DDL operations on the table, including other ONLINE DDL operations



</dd><dt><b>

PREFERRED

</b></dt>
<dd>

When specified with the ONLINE option, if ONLINE execution is not supported, then a SQL warning message appears, and the add operation executes in table x-lock mode.



</dd>
</dl>



</dd><dt><b>

*<clear\_column\_join\_data\_statistics\_clause\>*

</b></dt>
<dd>

```
<clear_column_join_data_statistics_clause> ::= CLEAR COLUMN JOIN DATA STATISTICS
```



</dd><dt><b>

*<constraint\_clauses\>*

</b></dt>
<dd>

Defines the constraint operations you can perform.

```
   [<add_constraint_clause>Clears the join data statistics] 
   [<drop_constraint_clause>] 
   [<alter_constraint_enforcement_clause>]
```


<dl>
<dt><b>

*<add\_constraint\_clause\>*

</b></dt>
<dd>

Adds a table constraint.

```
<add_constraint_clause> ::= 
 ADD [CONSTRAINT <constraint_name>] <table_constraint>

<constraint_name> ::= <identifier>
```


<dl>
<dt><b>

*<table\_constraint\>*

</b></dt>
<dd>

Specifies either a unique constraint, a referential constraint, or a check constraint.

```
<table_constraint> ::= 
 <unique_constraint_definition> 
 | <referential_constraint_definition> 
 | <check_constraint_definition>
```



</dd><dt><b>

*<unique\_constraint\_definition\>*

</b></dt>
<dd>

Specifies a unique constraint.

```
<unique_constraint_definition> ::= 
<unique_specification> (<unique_column_name_list>)
```

For more information about unique constraints, see the CREATE TABLE statement.



</dd><dt><b>

*<unique\_column\_name\_list\>*

</b></dt>
<dd>

Specifies the unique column name list, which can have one or more column names.

```
<unique_column_name_list> ::= 
 <unique_column_name>[{, <unique_column_name>}...]

<unique_column_name> ::= <identifier>
```



</dd><dt><b>

*<referential\_constraint\_definition\>*

</b></dt>
<dd>

Specifies a referential constraint.

```
<referential_constraint_definition> ::= 
FOREIGN KEY (<referencing_column_name_list>) <references_specification>
```

To ensure uniqueness, the target of a foreign key constraint must be either a full primary key or a unique column. Self-referencing foreign key constraints are supported.


<dl>
<dt><b>

*<referencing\_column\_name\_list\>*

</b></dt>
<dd>

Specifies the target column\(s\) of the foreign key constraint.

```
<referencing_column_name_list> ::= <referencing_column_name>[{, <referencing_column_name>}...]
```



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

Specifies the referenced table, with optional column name list and trigger action.

```
<references_specification> ::=  
 REFERENCES <referenced_table> [ ( <referenced_column_name_list> ) ] 
 [ <referential_triggered_action> ]
 [ <constraint_enforcement> ]
 [ <constraint_check_time> ]

<constraint_enforcement> ::= <enforcement_option>
| <validation_option>
| <enforcement_option> <validation_option>

<enforcement_option> ::= [ NOT ] ENFORCED
<validation_option> ::= [ NOT ] VALIDATED

<constraint_check_time> ::=  INITIALLY { IMMEDIATE | DEFERRED }
```

Specifying NOT VALIDATED means that existing data will not be checked to determine whether it violates the foreign key constraint.

Specifying NOT ENFORCED means that new or modified rows will not be checked to determine whether they violate the foreign key constraint.

Enable or disable constraint enforcement rather than dropping and recreating the constraint.

The default *<enforcement\_option\>* is ENFORCED and the default *<validation\_option\>* is VALIDATED.



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

```
<referenced_column_name_list> ::= <referenced_column_name> [, <referenced_column_name> [,…] ]
```

*<referenced\_column\_name\>* specifies the identifier of the column name to be referenced.

If *<referenced\_column\_name\_list\>* is specified, then there is a one-to-one correspondence between *<column\_name\>* of *<column\_definition\>* \(see [column\_definition](alter-table-statement-data-definition-20d329a.md#loio20d329a6751910149d5fdbc4800f92ff__column_definition)\) and *<referenced\_column\_name\>*. If it is not specified, then there is a one-to-one correspondence between *<column\_name\>* of *<column\_definition\>* and the column name of the referenced table's primary key.



</dd><dt><b>

*<referential\_triggered\_action\>*

</b></dt>
<dd>

Specifies an update rule with optional delete rule or a delete rule with optional update rule.

```
<referential_triggered_action> ::= 
   <update_rule> [ <delete_rule> ]
   | <delete_rule> [ <update_rule> ]
```

The order that you specify the rules in provides an order of precedence for execution.



</dd><dt><b>

*<update\_rule\>*

</b></dt>
<dd>

Specifies the behavior to perform when data in the column is updated.

```
<update_rule> ::= ON UPDATE <referential_action>

<referential_action> ::= { RESTRICT | CASCADE | SET NULL | SET DEFAULT }
```


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

If a record is updated in the referenced table, then the corresponding records in the referencing table are also updated with the same values.



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

If a record is updated in the referenced table, then the corresponding records in the referencing table are also updated with their default values.



</td>
</tr>
</table>



</dd><dt><b>

*<delete\_rule\>*

</b></dt>
<dd>

Specifies the behavior to perform when data in the column is deleted.

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

If a record in the referenced table is deleted, then the corresponding records in the referencing table are also deleted.



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



</dd>
</dl>



</dd><dt><b>

*<check\_constraint\_definition\>*

</b></dt>
<dd>

Specifies a condition to check for in the column.

```
<check_constraint_definition> ::= CHECK ( <search_condition> )
```

A table check constraint is satisfied if *<search\_condition\>* evaluates to true.



</dd><dt><b>

*<constraint\_check\_time\>*

</b></dt>
<dd>

Specifies when to check constraints. The default is INITIALLY IMMEDIATE.

-   IMMEDIATE - referential constraints are checked immediately during statement execution. If a referential constraint is violated, then the statement fails.

-   DEFERRED - referential constraints are checked at commit time. If a referential constraint is violated, then the transaction is rolled back. Also, if *<referential\_triggered\_action\>* is set to something other than RESTRICT, then the referential constraint check on the parent \(referencing\) table is not deferred and instead is checked immediately.




</dd>
</dl>



</dd><dt><b>

*<drop\_constraint\_clause\>*

</b></dt>
<dd>

Drops a unique or referential constraint.

```
<drop_constraint_clause> ::= DROP CONSTRAINT <constraint_name>

<constraint_name> ::= <identifier>
```



</dd><dt><b>

*<alter\_constraint\_enforcement\_clause\>*

</b></dt>
<dd>

Alters enforcement for a table constraint.

```
<alter_constraint_enforcement_clause> ::= ALTER CONSTRAINT <constraint_name> <constraint_enforcement>

<constraint_enforcement> ::= <enforcement_option>
 | <validation_option>
 | <enforcement_option> <validation_option>

<enforcement_option>  ::= [NOT] ENFORCED

<validation_option> ::= [NOT] VALIDATED
```

When you specify NOT VALIDATED, existing data is not checked to determine whether it violates the foreign key constraint.

When you specify NOT ENFORCED, means that new or modified rows are not checked to determine whether they violate the foreign key constraint.

Enable or disable constraint enforcement rather than dropping and recreating the constraint.

The default *<enforcement\_option\>* is ENFORCED and the default *<validation\_option\>* is VALIDATED.



</dd>
</dl>



</dd><dt><b>

*<convert\_index\_type\>*

</b></dt>
<dd>

Converts a unique index, unique table constraint, or a primary key on a column store table to an INVERTED index type.

```
ALTER CONSTRAINT <constraint_name> UNIQUE <cs_inverted_type_index>
| ALTER PRIMARY KEY <cs_inverted_type_index>
```


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

*<primary\_key\_clauses\>*

</b></dt>
<dd>

Defines the primary key operations that you can perform.

```
<primary_key_clauses> ::=
   <add_primary_key_clause> 
   | <drop_primary_key_clause>
   | <primary_key_update_clause>
```


<dl>
<dt><b>

*<add\_primary\_key\_clause\>*

</b></dt>
<dd>

Adds a primary key on a column.

```
<add_primary_key_clause> ::= 
   ADD PRIMARY KEY [ <rs_tree_type_index> | <cs_inverted_type_index> ] ( <column_name> [, <column_name> [,...] ] )
   | ADD PRIMARY KEY USING INDEX <index_name>
```


<dl>
<dt><b>

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



</dd><dt><b>

USING INDEX *<index\_name\>*

</b></dt>
<dd>

Specifies a unique index to promote to the primary key. All columns of the index must have the NOT NULL constraint. The table must not use table replication.



</dd>
</dl>



</dd><dt><b>

*<drop\_primary\_key\_clause\>*

</b></dt>
<dd>

Drops the primary key.

```
<drop_primary_key_clause> ::= DROP PRIMARY KEY 
```



</dd><dt><b>

*<primary\_key\_update\_clause\>*

</b></dt>
<dd>

Specifies if UPDATE statements are allowed on primary key columns. This clause is only supported on tables with heterogeneous partitioning.

```
<primary_key_update_clause> ::= PRIMARY KEY UPDATE {ON | OFF};
```


<dl>
<dt><b>

PRIMARY KEY UPDATE \{ ON | OFF \}

</b></dt>
<dd>

Specifies if UPDATE statements are allowed on primary key columns.



</dd>
</dl>



</dd>
</dl>



</dd><dt><b>

*<preload\_clause\>*

</b></dt>
<dd>

Sets or removes the preload flag of the given tables or columns. Drops the primary key constraint.

```
<preload_clause> ::= 
 PRELOAD ALL 
 | PRELOAD ( <column_name> ) 
 | PRELOAD NONE
```

When the preload flag is set, tables are automatically loaded into memory after an index server start. This setting is available for column store tables.

The current status of the preload flag is visible in the system table TABLES in the IS\_PRELOAD and IS\_PARTIAL\_PRELOAD columns and in the system table TABLE\_COLUMNS in the PRELOAD column. Possible values are TRUE, FALSE, and NULL. Preload information can be NULL in the case of a row store table.

Using PRELOAD with ALL sets preload flags of all columns in the table.

PRELOAD \(*<column\_name\>*\) sets the flags of the specified column.

PRELOAD NONE removes the preload flag from all columns.



</dd><dt><b>

*<table\_conversion\_clause\>*

</b></dt>
<dd>

Converts the table storage from ROW to COLUMN or from COLUMN to ROW.

```
<table_conversion_clause> ::= [ALTER TYPE] {
   ROW [THREADS <number_of_threads>] 
   | COLUMN [ THREADS <number_of_threads> [ BATCH <batch_size>Drops the primary key ] ]
}
```


<dl>
<dt><b>

THREADS *<number\_of\_threads\>*

</b></dt>
<dd>

Specifies how many parallel execution threads should be used for the table conversion.

```
THREADS <number_of_threads>
 <number_of_threads> ::= <unsigned_integer>
```

The optimal value for the number of threads is the number of available CPU cores. If THREADS is not provided, then the default value of the number of CPU cores specified in the `indexserver.ini` file is used.



</dd><dt><b>

BATCH *<batch\_size\>*

</b></dt>
<dd>

Specifies the number of rows to be inserted in a batch.

```
BATCH <batch_size>
 <batch_size> ::= <unsigned_integer>
```

If BATCH is not specified, then the default value of 2,000,000 is used. Inserts into column tables are immediately committed after every *<batch\_size\>* records have been inserted. You can only use the BATCH option when a table is converted from ROW to COLUMN storage.



</dd>
</dl>



</dd>
</dl>

Defines the association operations you can perform.

```
   [<add_association_clause>Converts the table storage from ROW to COLUMN or
                     from COLUMN to ROW.]
   [Converts the table storage from ROW to COLUMN or
                     from COLUMN to ROW.<drop_association_clause>]
```


<dl>
<dt><b>

*<add\_association\_clause\>*

</b></dt>
<dd>

Adds an association clause. Associations are checked at runtime.

```
<add_association_clause> ::= ADD ASSOCIATION ( <association_def> )
<association_def> ::= [ <join_cardinality> ] JOIN <table_name> [ AS <identifier> ] ON <predicate> WITH DEFAULT FILTER <predicate>
<join_cardinality> ::=
 MANY TO ONE
 | MANY TO MANY
 | ONE TO ONE
 | ONE TO MANY

<table_name> ::= <identifier>
```

The WITH DEFAULT FILTER clause specifies a default predicate to filter column values.



</dd><dt><b>

*<drop\_association\_clause\>*

</b></dt>
<dd>

Drops an association clause

```
<drop_association_clause> ::= DROP ASSOCIATION <identifier>
```



</dd>
</dl>


<dl>
<dt><b>

*<partition\_clauses\>*

</b></dt>
<dd>

For clauses to alter heterogeneous and non-heterogeneous partitions, see the topic *Non-heterogeneous Partition Clauses* or *Heterogeneous Partition Clauses* in this guide.

-   [Non-Heterogeneous Alter Partition Clauses](non-heterogeneous-alter-partition-clauses-f7ae27c.md).
-   [Heterogeneous Alter Partition Clauses](heterogeneous-alter-partition-clauses-a4258b8.md).



</dd><dt><b>

*<table\_load\_unit\_clause\>*

</b></dt>
<dd>

Specifies how to load data into memory when the table is queried. Specifying the load unit is only supported on column-store tables.

```
<table_load_unit_clause> ::= { COLUMN | PAGE | DEFAULT } LOADABLE [ CASCADE ]
```

In the case of competing or unspecified *<load\_unit\>* settings, the logic described in CREATE TABLE for *<load\_unit\>* is applied.


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



</dd><dt><b>

DEFAULT LOADABLE

</b></dt>
<dd>

If you specify DEFAULT, then there is no explicit preference for the loading unit that is used when the results are loaded from the table. If there is an inherited loading unit from another object, then that loading unit is used.



</dd><dt><b>

CASCADE

</b></dt>
<dd>

Specify CASCADE when you want the loading unit to apply to all objects below the specified object in the object hierarchy, so table loading units apply to partitions.



</dd>
</dl>



</dd><dt><b>

*<alter\_persistent\_memory\_spec\_clause\>*

</b></dt>
<dd>

Alters the persistent memory storage preference at the table, partition, or column level, depending on where the clause is situated in the ALTER statement. For example, when specified inside *<column\_definition\>*, it enables or disables persistent memory for the column. When specified inside *<add\_range\_partition\_clause\>*, it enables or disables persistent memory for the new partition.

> ### Note:  
> This clause is not supported for heterogeneous range partitions.

```
<alter_persistent_memory_spec_clause> ::= PERSISTENT MEMORY <alter_pm_preference> [ IMMEDIATE | DEFERRED ] [ CASCADE ]

<alter_pm_preference> ::= { ON | OFF | DEFAULT }
```


<dl>
<dt><b>

ON IMMEDIATE

</b></dt>
<dd>

Enables persistent memory usage and populates the underlying PERSISTENT MEMORY storage.



</dd><dt><b>

ON or ON DEFERRED

</b></dt>
<dd>

Enables persistent memory usage without populating the underlying PERSISTENT MEMORY storage. PERSISTENT MEMORY storage population happens as part of next load from disk or delta merge. DEFERRED is the default behavior when ON is specified without IMMEDIATE or DEFERRED.



</dd><dt><b>

OFF IMMEDIATE

</b></dt>
<dd>

Disables persistent memory usage and reloads data into DRAM. Cleanup of underlying persistent memory is handled asynchronously.



</dd><dt><b>

OFF or OFF DEFERRED

</b></dt>
<dd>

Disables persistent memory usage without switching in memory data to DRAM. Data is loaded into DRAM as part of next delta merge or reload. Deletion of persistent memory is driven via delta merge cleanup and subsequent savepoint. DEFERRED is the default behavior when OFF is specified without IMMEDIATE or DEFERRED. Cleanup of underlying persistent memory is handled asynchronously.



</dd><dt><b>

DEFAULT

</b></dt>
<dd>

No explicit preference is set for persistent memory usage at the specified object level \(table, partition or column\). Instead, the SAP server, falls back to default behavior, which is to use the inherited persistent memory preference, if any.

IMMEDIATE and DEFERRED actions are not supported when DEFAULT is specified.



</dd><dt><b>

CASCADE

</b></dt>
<dd>

The user-specified persistent memory preference is applied to all objects below the specified object in the object hierarchy. CASCADE is not supported at the partition level, and is meaningless at the column level.



</dd>
</dl>



</dd><dt><b>

*<replica\_clauses\>*

</b></dt>
<dd>

Defines the alter operations you can perform with regards to replicas.

```
<replica_clauses> ::= 
   <add_replica_clause>
   | <alter_replica_group_clause>
   | <drop_replica_clause>
   | <enable_disable_replica_clause>
   | <move_replica_clause>
   | <set_replica_source_clause>
```


<dl>
<dt><b>

*<add\_replica\_clause\>*

</b></dt>
<dd>

Adds a replica.

```
<add_replica_clause> ::= ADD [ <sync_or_async> ] [ <column_or_row> ] 
   REPLICA [ ( <src_table_column_list> ) ] [ <replica_partition> ]
   [ <set_group_option> ] [ AT <replica_locations> ]
```


<dl>
<dt><b>

*<column\_or\_row\>*

</b></dt>
<dd>

Replica type is specified by *<column\_or\_row\>*. If it is not specified, then the type is the same as that of table.

```
<column_or_row> ::= { COLUMN | ROW }
```



</dd><dt><b>

*<sync\_or\_async\>*

</b></dt>
<dd>

Specifies whether the replica is immediately activated.

```
<sync_or_async> ::= { SYNCHRONOUS | ASYNCHRONOUS }
```

SYNCRONOUS replicas are activated immediately. ASYNCRONOUS replicas are created in an empty state; execute an ALTER SYSTEM ENABLE ALL ASYNCHRONOUS TABLE REPLICAS statement to activate them.



</dd><dt><b>

*<src\_table\_column\_list\>*

</b></dt>
<dd>

Specifies a subset of the columns in the source table. A replica that has a subset of the columns from the source table is called a **column-wise replica**.

```
<src_table_column_list> ::= <column_name> [, <column_name> [,…] ]
```

Although you can specify the columns in any order, the order of the columns in the replica matches the order of columns in the source table.

If you specify all of the columns from the source table, then the replica that is created is no longer considered a column-wise replica.



</dd><dt><b>

*<replica\_partition\>*

</b></dt>
<dd>

Specifies the partitions for the replicated table.

```
<replica_partition> ::= <partition_clause>
```

The *<replica\_partition\>* clause supports all partition types not using time selection. See [*<partition\_clauses\>*](alter-table-statement-data-definition-20d329a.md#loio20d329a6751910149d5fdbc4800f92ff__partition_clauses).



</dd><dt><b>

*<replica\_locations\>*

</b></dt>
<dd>

Adds the replica to the specified locations.

```
<replica_locations> ::= { <indexserver_host_port> | ( <indexserver_host_port>, … ) }

<indexserver_host_port> ::= '<host_name>:<port_number>'
```

If *<replica\_locations\>* is not specified, then the replica table is added based on the table placement rule. If no table placement rule is also defined, then the replica table is added one of the secondary nodes that is not a source table location and where there is not already an existing replica of the table. If there are no more replica nodes to add a replica table, then an error is returned.



</dd>
</dl>



</dd><dt><b>

*<alter\_replica\_group\_clause\>*

</b></dt>
<dd>

Changes the group attributes for a replica.

```
<alter_replica_group clause> ::= 
   ALTER REPLICA SET <set_group_option> [ CASCADE ] [ AT <replica_locations> ]
   | ALTER REPLICA UNSET GROUP [ CASCADE ] [ AT <replica_locations> ]
   | ALTER REPLICA UNSET GROUP LEAD [ AT <replica_locations> ]
```



</dd><dt><b>

*<drop\_replica\_clause\>*

</b></dt>
<dd>

Drops a replica at the specified locations.

```
<drop_replica_clause> ::= **DROP REPLICA AT <replica_locations>
```



</dd><dt><b>

*<enable\_disable\_replica\_clause\>*

</b></dt>
<dd>

Enables or disables the replication operation for the specified table.

```
<enable_disable_replica_clause> ::= 
<source_schema_name>.<source_table_name> { ENABLE | DISABLE } [ SYNCHRONOUS | ASYNCHRONOUS ] REPLICA

<source_schema_name> ::= <identifier>
<source_table_name> ::= <identifier>
```

If \[SYNCHRONOUS | ASYNCHRONOUS\] is not specified, the default is SYNCHRONOUS.

SYNCHRONOUS is not supported for remote table replication.



</dd><dt><b>

*<move\_replica\_clause\>*

</b></dt>
<dd>

Moves replicas from one index server to another.

```
<move_replica_clause> ::= 
 MOVE REPLICA [ PARTITION <partition_number> ] FROM [ LOCATION ] <from_location> TO [ LOCATION ] <to_location>
 
<from_location> ::= <indexserver_host_port>
<to_location> ::= <indexserver_host_port>
<indexserver_host_port> ::= '<host_name>:<port_number>'
```



</dd><dt><b>

*<set\_replica\_source\_clause\>*

</b></dt>
<dd>

Swaps the source and replica for replication, so that the replica becomes the source and the source becomes the replica.

This clause is only supported if the columns in the source table and replica are the same.

```
<set_replica_source_clause> ::= SET REPLICA SOURCE AT '<host_name>:<port_number>'
```



</dd>
</dl>



</dd><dt><b>

*<group\_option\_clauses\>*

</b></dt>
<dd>

Defines the group option operations that you can set.

```
<group_option_clauses> ::= 
   <set_group_option>
   | <unset_group_option> 
```


<dl>
<dt><b>

*<set\_group\_option\>*

</b></dt>
<dd>

Sets one or more table group option for the table. Table group settings are stored in the TABLE\_GROUPS system view.

```
<set_group_option> ::= SET <group_option> [...]

<group_option> ::= 
 GROUP TYPE <identifier> 
 | GROUP SUBTYPE <identifier> 
 | GROUP NAME <identifier>
 | GROUP LEAD
```



</dd><dt><b>

*<unset\_group\_option\>*

</b></dt>
<dd>

Unsets \(removes\) all table group attributes for the table \(type, subtype, name, and so on\).

```
<unset_group_option> ::= UNSET GROUP [ LEAD ]
```



</dd>
</dl>



</dd><dt><b>

*<auto\_merge\_option\>*

</b></dt>
<dd>

Enables or disables automatic delta merge on the specified table.

```
<auto_merge_option> ::= {ENABLE | DISABLE} AUTOMERGE
```

The delta merge feature is only supported on column store tables.



</dd><dt><b>

*<unload\_priority\>*

</b></dt>
<dd>

Sets the priority of table to be unloaded from memory.

```
<unload_priority_option> ::= UNLOAD PRIORITY <unload_priority>

<unload_priority> ::= <digit>
```

*<unload\_priority\>* are can be 0 ~ 9, where 0 means not-unloadable and 9 means earliest unload.



</dd><dt><b>

*<trigger\_option\>*

</b></dt>
<dd>

Enables or disables the specified trigger on the specified table.

```
<trigger_option> ::= { ENABLE | DISABLE } TRIGGER [<trigger_name>]
```

If *<trigger\_name\>* is not specified, then this setting enables or disables all triggers on the specified table.



</dd><dt><b>

*<row\_order\_clauses\>*

</b></dt>
<dd>

Defines the row order clauses you can set.

```
   [<set_row_order>] 
   [<unset_row_order>] 
```


<dl>
<dt><b>

*<set\_row\_order\>*

</b></dt>
<dd>

Sets the row order and type.

```
<set_row_order> ::= SET <row_order_definition>

<row_order_definition> ::= <row_order_specification> (<unique_column_name_list>)

<row_order_specification> ::= ROW ORDER [BY VALUE]

<unique_column_name_list> ::= <unique_column_name> [,…] 
```

Rows are sorted exactly by value for a given set of columns. BY VALUE is the default.



</dd><dt><b>

*<unset\_row\_order\>*

</b></dt>
<dd>

Unsets the row order and type.

```
<unset_row_order> ::= UNSET ROW ORDER
```



</dd>
</dl>



</dd><dt><b>

*<unused\_retention\_period\>*

</b></dt>
<dd>

Unloads a table or table partition from memory if it was not accessed for the number of seconds defined as the retention period.

```
<unused_retention_period> ::= UNUSED RETENTION PERIOD { <retention_period> | ( <retention_period> [,…] )}

<retention_period> ::= <unsigned_integer>
```

A single value specifies the retention period at table-level, including all of the table partitions. Multiple values specify specific retention periods for each of the table partitions. If multiple values are specified, then the number of values must match the number of table partitions.

The default value and behavior of UNUSED\_RETENTION\_PERIOD is 0 \(inactive\). To activate UNUSED\_RETENTION\_PERIOD, change the value to something other than 0. However, use of the UNUSED\_RETENTION\_PERIOD setting on a table requires that the global unused\_retention\_period setting in the `global.ini` configuration file be set to something other than 0.



</dd><dt><b>

*<reclaim\_data\_space\_clause\>*

</b></dt>
<dd>

Reclaims data space of the specified table. This clause is only for use on row store tables.

```
<reclaim_data_space_clause> ::= RECLAIM DATA SPACE
```

This statement has the same effect as defragmentation by restructuring table data space. However, this behavior does not always guarantee that restructured data space uses less memory than before. In some optimized cases, restructured data space uses much memory.



</dd><dt><b>

*<owner\_to\_clause\>*

</b></dt>
<dd>

Specifies a new owner for the table.

```
<owner_to_clause> ::= OWNER TO <user_name>
```

The new owner becomes the grantor for all of the privileges on the table that were granted by the old owner. Also, the old owner is granted all privileges for the table by the new owner so that they can continue running jobs on the table.



</dd><dt><b>

*<alter\_mask\_settings\_clause\>*

</b></dt>
<dd>

Add a new mask expression or changes or drops an existing mask expression. Data masking transforms confidential data so that it appears meaningless to users who don't have the privileges required to view it. *<alter\_mask\_settings\_clause\>* does not change the table's column definitions.

```
<alter_mask_settings_clause> ::=
 { ADD | ALTER } [{ DEFAULT | SESSION USER }] MASK ( <columns_name> USING <mask_expression> [,…] )
 | ALTER MASK ( <columns_name> USING <mask_expression> [,…] )
 | DROP MASK ( <column_name_list> )

<mask_expression> ::= <expression>

<column_name_list> ::= <column_name>[,…]
```

When adding a mask expression, the mask behavior is defined for the object. New column masks must use the same mask mode. When altering, you can change the mask expression, but not the mode. Once all existing masks are dropped, you can add new masks using a different mask mode.

Masking behavior is supported on row and column tables, and SQL row and calculation views. It is not supported on any other type of tables \(virtual tables, extended tables, temporary tables etc.\) and views \(Join/Olap/Hierarchy views\).

Only one masking behavior, definer owner-based \(DEFAULT MASK\) or session user based masking \(SESSION USER MASK\), is supported on a table or view with masked columns. You can combine both masking behaviors in an object hierarchy. For example, a view with session user based masking can be created on a table with owner-based masking.

If not specified, DEFAULT is the default.

*<mask\_expression\>* can be any type of expression, including a user-defined function, that returns the same data type and length as the original column.

For more information on data masking, see the *SAP HANA Cloud, SAP HANA Database Security Guide*.



</dd><dt><b>

*<set\_movable\_clause\>*

</b></dt>
<dd>

Controls whether the table can be moved to another location.

```
<set_movable_clause> ::= SET [NOT] MOVABLE
```

When a table is set to NOT MOVABLE, it cannot be moved to another location. By default, tables are movable.



</dd><dt><b>

*<numa\_node\_preference\_clause\>*

</b></dt>
<dd>

Alters the NUMA node preferences. Although this clause is defined here at the table level, *<numa\_node\_preference\_clause\>* can be set in various locations such as range partition definitions \(not hash or round-robin\) and column definitions, as indicated in the syntax within the topic. *<numa\_node\_preference\_clause\>* is not supported for heterogeneous partitions.

```
<numa_node_preference_clause> ::= NUMA NODE { ( <numa_node_index_spec> ) | NULL } [ IMMEDIATE | DEFERRED ]

<numa_node_index_spec> :: = <numa_node_spec> [, <numa_node_spec> [,…] ]

<numa_node_spec> ::= { <single_node_spec> | <range_node_spec> }

<single_node_spec> :: =  <integer_const>
<range_node_spec> :: =  <integer_const> TO <integer_const>
```


<dl>
<dt><b>

NULL

</b></dt>
<dd>

To unset existing NUMA node preferences on the associated object \(table, column, partition, or replica\), specify NUMA NODE NULL.



</dd><dt><b>

IMMEDIATE, DEFERRED

</b></dt>
<dd>

Specify whether to apply the NUMA node preferences immediately \(IMMEDIATE\) or to defer applying the preferences until the next time the table is reloaded \(DEFERRED\). If you specify IMMEDIATE, then the associated table, column, or table partition is immediately moved according to the altered preference settings.



</dd><dt><b>

*<integer\_const\>*

</b></dt>
<dd>

*<integer\_const\>* cannot be a negative number.



</dd><dt><b>

*<numa\_node\_spec\>*

</b></dt>
<dd>

Specify one or more single NUMA nodes \(*<single\_node\_spec\>*\), or one or more NUMA node ranges \(*<range\_node\_spec\>*\), or a mixture of both.

NUMA node indexes should be specified in the range of 0 to one less than max\_numa\_node\_count, where max\_numa\_node\_count is the number of NUMA nodes configured for the system. If the NUMA node index specified is greater than or equal to max\_numa\_node\_count, then a random NUMA node in the range of 0 to one less than max\_numa\_node\_count is selected for allocation. For example, on a system where max\_numa\_node\_count is set to 8, if you specify a NUMA node index of 10, then any node in the range of 0 to 7 \(inclusive\) is chosen randomly for allocation.



</dd>
</dl>



</dd>
</dl>



<a name="loio20d329a6751910149d5fdbc4800f92ff__sql_description"/>

## Description

This statement is not for use with virtual tables. To alter a virtual table, use the ALTER VIRTUAL TABLE statement.



<a name="loio20d329a6751910149d5fdbc4800f92ff__section_qhh_qqp_zsb"/>

## Permissions

In general, you must have the ALTER object privilege on a table to alter it.

Some non-destructive partitioning clauses can be executed with the PARTITION ADMIN system privilege. For all other partitioning clauses, you must have the ALTER object privilege on a table to alter a partition. For details, see [Non-Heterogeneous Alter Partition Clauses](non-heterogeneous-alter-partition-clauses-f7ae27c.md) and [Heterogeneous Alter Partition Clauses](heterogeneous-alter-partition-clauses-a4258b8.md).

For the clauses listed below, only the TABLE ADMIN system privilege is required. These clauses are administrative in nature and do not change the structure of the table and do not allow access to table data either explicitly or implicitly.

-   \[[*<lob\_reorganize\_clause\>*](alter-table-statement-data-definition-20d329a.md#loio20d329a6751910149d5fdbc4800f92ff__lob_reorganize_clause)\]
-   \[[*<clear\_column\_join\_data\_statistics\_clause\>*](alter-table-statement-data-definition-20d329a.md#loio20d329a6751910149d5fdbc4800f92ff__clear_column_join_data_statistics_clause)\]
-   \[[*<preload\_clause\>*](alter-table-statement-data-definition-20d329a.md#loio20d329a6751910149d5fdbc4800f92ff__preload_clause)\]
-   \[[*<table\_conversion\_clause\>*](alter-table-statement-data-definition-20d329a.md#loio20d329a6751910149d5fdbc4800f92ff__table_conversion_clause)\]
-   \[[*<table\_load\_unit\_clause\>*](alter-table-statement-data-definition-20d329a.md#loio20d329a6751910149d5fdbc4800f92ff__load_unit)\]
-   \[[*<alter\_persistent\_memory\_spec\_clause\>*](alter-table-statement-data-definition-20d329a.md#loio20d329a6751910149d5fdbc4800f92ff__alter_persistent_memory_spec_clause)\]
-   \[[*<auto\_merge\_option\>*](alter-table-statement-data-definition-20d329a.md#loio20d329a6751910149d5fdbc4800f92ff__auto_merge_option)\]
-   \[[*<unload\_priority\>*](alter-table-statement-data-definition-20d329a.md#loio20d329a6751910149d5fdbc4800f92ff__unload_priority)\]
-   \[[*<group\_option\_clauses\>*](alter-table-statement-data-definition-20d329a.md#loio20d329a6751910149d5fdbc4800f92ff__group_option_clauses)\]
-   \[[*<row\_order\_clauses\>*](alter-table-statement-data-definition-20d329a.md#loio20d329a6751910149d5fdbc4800f92ff__row_order_clauses)\]
-   \[[*<unused\_retention\_period\>*](alter-table-statement-data-definition-20d329a.md#loio20d329a6751910149d5fdbc4800f92ff__unused_retention_period)\]
-   \[[*<reclaim\_data\_space\_clause\>*](alter-table-statement-data-definition-20d329a.md#loio20d329a6751910149d5fdbc4800f92ff__reclaim_data_space_clause)\]
-   \[[*<set\_movable\_clause\>*](alter-table-statement-data-definition-20d329a.md#loio20d329a6751910149d5fdbc4800f92ff__set_movable_clause)\]
-   \[[*<convert\_index\_type\>*](alter-table-statement-data-definition-20d329a.md#loio20d329a6751910149d5fdbc4800f92ff__convert_index_type)\]
-   \[[*<numa\_node\_preference\_clause\>*](alter-table-statement-data-definition-20d329a.md#loio20d329a6751910149d5fdbc4800f92ff__alter_numa_node_preference_clause_1)\]



<a name="loio20d329a6751910149d5fdbc4800f92ff__sql_examples"/>

## Examples


<dl>
<dt><b>



</b></dt>
<dd>

Create Table t, and then alter default value of column b to 10.

```
CREATE ROW TABLE t (a INT, b INT, c INT);
 ALTER TABLE t ALTER (b INT DEFAULT 10);
```

Alter table t adding a new column d.

```
ALTER TABLE t ADD (d NVARCHAR(10) DEFAULT 'NCHAR');
```

Create a primary key constraint, prim\_key, on columns a and b of table t.

```
ALTER TABLE t ADD CONSTRAINT prim_key PRIMARY KEY (a, b);
```

Drop a primary key on an existing table t.

```
ALTER TABLE t DROP PRIMARY KEY;
```

Add a primary key on table t to columns c and d.

```
ALTER TABLE t ADD PRIMARY KEY (c,d);
```

Change the table type of table t to COLUMN storage.

```
ALTER TABLE t COLUMN;
```

Set the preload flags of column b and c on table t.

```
ALTER TABLE t PRELOAD (b, c);
```

Change the unload priority of table t to 2:

```
ALTER TABLE t UNLOAD PRIORITY 2;
```

Apply the midsize LOB threshold system property to the data column of the t table.

```
ALTER TABLE t LOB REORGANIZE (a);
```

Apply the midsize LOB threshold system property to all LOB columns on the t table.

```
ALTER TABLE t LOB REORGANIZE;
```

Create table T3 with page loadable columns C3, C4 and C5. Then, C3 becomes column loadable and C6 page loadable.

```
CREATE COLUMN TABLE T3 (C1 INT PRIMARY KEY, C2 DATE, C3 NVARCHAR(80) PAGE LOADABLE NOT NULL,
   C4 NVARCHAR(5000) PAGE LOADABLE, C5 NVARCHAR(5000) PAGE LOADABLE NOT NULL, C6 NVARCHAR(5000)); 
 ALTER TABLE T3 ALTER (C3 NVARCHAR(80) COLUMN LOADABLE, C6 NVARCHAR(5000) PAGE LOADABLE);
```

Set group type and name of T3, and then unset it:

```
ALTER TABLE T3 SET GROUP TYPE group_type1 GROUP NAME group_name1; 
ALTER TABLE T3 UNSET GROUP;
```

Execute the following statements to create and populate table t1 and then perform a drop operation on column a that does not serialize with concurrent DML operations:

```
CREATE TABLE t1 (a INT, b INT);
ALTER TABLE t1 DROP (a) ONLINE;
```

Alter the primary key index on Table T1 to an inverted HASH type.

```
ALTER TABLE T1 ALTER PRIMARY KEY INVERTED HASH;
```

Create table T and unique index IDX, then promote IDX to the primary key of T.

```
CREATE COLUMN TABLE T (I INT NOT NULL);
CREATE UNIQUE INDEX IDX ON T (I);
ALTER TABLE T ADD PRIMARY KEY USING INDEX IDX;

```



</dd><dt><b>

JOIN

</b></dt>
<dd>

Retrieve, display, and delete column join data statistics.

```
DROP TABLE A;
CREATE COLUMN TABLE A ( NVARCHAR(2), ab INT);
DROP TABLE B;
CREATE COLUMN TABLE B (b1 INT, b2 NVARCHAR(1));
INSERT INTO A (, ab) VALUES ('', 1);
INSERT INTO A (, ab) VALUES ('BB', 2);
INSERT INTO B (b1, b2) VALUES (1, 'a');
INSERT INTO B (b1, b2) VALUES (3, 'f');
MERGE DELTA OF A;
MERGE DELTA OF B;
```

Perform a join on tables A and B.

```
SELECT * FROM A INNER JOIN B ON A.ab = B.b1;
```

View the column join data statistics for tables A and B.

```
SELECT COUNT(*) FROM M_JOIN_DATA_STATISTICS WHERE schema_name1 = 'SYSTEM' AND table_name1 IN ('A', 'B');
SELECT * FROM M_JOIN_DATA_STATISTICS;
```

Clear the column join data statistics from the system.

```
ALTER SYSTEM CLEAR COLUMN JOIN DATA STATISTICS;
```

Clear the column join data statistics from table A.

```
ALTER TABLE A CLEAR COLUMN JOIN DATA STATISTICS;
```



</dd><dt><b>

Fuzzy searching

</b></dt>
<dd>

Create table T2 with a fuzzy search index and fuzzy search mode. You then switch off the fuzzy search index of COL1 and finally reset fuzzy search mode of COL2.

```
CREATE COLUMN TABLE T2 (KEY INT, COL1 NVARCHAR(10) FUZZY SEARCH INDEX ON, COL2 NVARCHAR(10) FUZZY SEARCH MODE 'postcode');
 ALTER TABLE T2 ALTER (COL1 NVARCHAR(10) FUZZY SEARCH INDEX OFF);
 ALTER TABLE T2 ALTER (COL2 NVARCHAR(10) FUZZY SEARCH MODE NULL);
```



</dd><dt><b>

Identity columns

</b></dt>
<dd>

Create table T5, and add an identity column B with starting value of 100 and an increment of 10.

```
CREATE COLUMN TABLE T5 (A INT);
 ALTER TABLE T5 ADD (B INT GENERATED ALWAYS AS IDENTITY (START WITH 100 INCREMENT BY 10));
```

Create table T\_ALWAYS with identity column B that has a start value of 100 and increments by 10.

```
CREATE COLUMN TABLE T_ALWAYS (A INT);
ALTER TABLE T_ALWAYS ADD (B INT GENERATED ALWAYS AS IDENTITY (START WITH 100 INCREMENT BY 10));
INSERT INTO T_ALWAYS (A) VALUES (1);
INSERT INTO T_ALWAYS (A) VALUES (2);
SELECT * FROM T_ALWAYS;
```


<table>
<tr>
<th valign="top">

A



</th>
<th valign="top">

B



</th>
</tr>
<tr>
<td valign="top">

1



</td>
<td valign="top">

100



</td>
</tr>
<tr>
<td valign="top">

2



</td>
<td valign="top">

110



</td>
</tr>
</table>

Create table T\_DEFAULT with identity column B that has a start value of 100 and increments by 10.

```
CREATE COLUMN TABLE T_DEFAULT (A INT);
ALTER TABLE T_DEFAULT ADD (B INT GENERATED ALWAYS AS IDENTITY (START WITH 100 INCREMENT BY 10));
INSERT INTO T_DEFAULT (A) VALUES (1);
INSERT INTO T_DEFAULT (A) VALUES (2);
INSERT INTO T_DEFAULT (A, B) VALUES (3, 105);
INSERT INTO T_DEFAULT (A) VALUES (4);
INSERT INTO T_DEFAULT (A, B) VALUES (5, 205);
INSERT INTO T_DEFAULT (A) VALUES (6);
SELECT * FROM T_DEFAULT;
```

In the results table below, the Description column isn't part of the results, it is provided to explain the values in column B.


<table>
<tr>
<th valign="top">

A



</th>
<th valign="top">

B



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

1



</td>
<td valign="top">

100



</td>
<td valign="top">

The START WITH value



</td>
</tr>
<tr>
<td valign="top">

2



</td>
<td valign="top">

110



</td>
<td valign="top">

The next INCREMENT value



</td>
</tr>
<tr>
<td valign="top">

3



</td>
<td valign="top">

105



</td>
<td valign="top">

A specified value that is lower than the current sequence



</td>
</tr>
<tr>
<td valign="top">

4



</td>
<td valign="top">

120



</td>
<td valign="top">

The next INCREMENT value



</td>
</tr>
<tr>
<td valign="top">

5



</td>
<td valign="top">

205



</td>
<td valign="top">

The specified value that resets the internal sequence to 200



</td>
</tr>
<tr>
<td valign="top">

6



</td>
<td valign="top">

210



</td>
<td valign="top">

The next INCREMENT value



</td>
</tr>
</table>



</dd><dt><b>

Table replication

</b></dt>
<dd>

Create an additional asynchronous table replica for table SRC\_SCHEMA.TAB1.

```
ALTER TABLE SRC_SCHEMA.TAB1 ADD ASYNCHRONOUS REPLICA;
```

Drop the table replicas of SRC\_SCHEMA.TAB1 in all locations.

```
ALTER TABLE SRC_SCHEMA.TAB1 DROP REPLICA AT ('hosta:30040', 'hostb:30301', 'hostc:30301');
```

Drop the table replica of SRC\_SCHEMA.TAB1 on hostb:30301.

```
ALTER TABLE SRC_SCHEMA.TAB1 DROP REPLICA AT 'hostb:30301';
```

Enable asynchronous table replication for the table SRC\_SCHEMA.TAB1.

```
ALTER TABLE SRC_SCHEMA.TAB1 ENABLE ASYNCHRONOUS REPLICA;
```

Disable asynchronous table replication for the table SRC\_SCHEMA.TAB1.

```
ALTER TABLE SRC_SCHEMA.TAB1 DISABLE ASYNCHRONOUS REPLICA;
```

Create table T4 with replicas in all indexservers. Then, you drop all replicas and create a replica at the specific indexserver. Then, you move the replica to the other indexserver.

```
CREATE ROW TABLE T4 (C1 INT PRIMARY KEY) REPLICA AT ('host_name:30040', 'host_name:30042');
 ALTER TABLE T4 DROP REPLICA AT ('host_name:30040', 'host_name:30042');
 ALTER TABLE T4 ADD REPLICA AT 'host_name:30040';
 ALTER TABLE T4 MOVE REPLICA FROM 'host_name:30040' TO 'host_name:30042';
```

Add a replica to table SRC\_TABLE.

```
CREATE COLUMN TABLE SRC_TABLE (C1, C2, C3) PARTITION BY HASH (C1) PARTITIONS 32;
ALTER TABLE SRC_TABLE ADD REPLICA PARTITION BY HASH (C2) PARTITIONS 8;
```



</dd><dt><b>

Data masking

</b></dt>
<dd>

Alter the Personal\_Information table to use masking for the SSN column:

```
ALTER TABLE PERSONAL_INFORMATION ADD MASK (SSN USING '****');
```

Alter the Personal\_Information table to drop masking from the SSN column:

```
ALTER TABLE PERSONAL_INFORMATION DROP MASK (SSN);
```



</dd><dt><b>

Constraints

</b></dt>
<dd>

Create two tables and then add a foreign key constraint to table REFERENCING\_T.

```
CREATE COLUMN TABLE REFERENCED_T ( A INT PRIMARY KEY, B INT);
CREATE COLUMN TABLE REFERENCING_T (A INT, B INT);
ALTER TABLE REFERENCING_T ADD CONSTRAINT fk1 FOREIGN KEY(A) REFERENCES REFERENCED_T(A);
```

Populate the tables REFERENCED\_T and REFERENCING\_T.

```
INSERT INTO REFERENCED_T VALUES (1, 1);
INSERT INTO REFERENCING_T VALUES (1, 1);
```

Executing the following statement fails with a foreign key constraint violation:

```
INSERT INTO REFERENCING_T VALUES (2, 1);
```

Alter table REFERENCING\_T so that the foreign key constraint is not enforced.

```
ALTER TABLE REFERENCING_T ALTER CONSTRAINT fk1 NOT ENFORCED;
```

Now, running the following statement succeeds:

```
INSERT INTO REFERENCING_T VALUES (2, 1);
```

If you then run the following statement, it fails as the constraint is violated by the value that was just inserted:

```
ALTER TABLE REFERENCING_T ALTER CONSTRAINT fk1 ENFORCED;
```

However, if you add NOT VALIDATED to the statement above and re-run it, it succeeds.

```
ALTER TABLE REFERENCING_T ALTER CONSTRAINT fk1 ENFORCED NOT VALIDATED;
```

Running the same INSERT statement as above now fails because the ENFORCED NOT VALIDATED clause means that only existing data is not checked, but modified rows cannot violate the constraint.

```
INSERT INTO REFERENCING_T VALUES (2, 1);
```

Create a table and add a unique constraint UK.

```
CREATE ROW TABLE R (A INT PRIMARY KEY, B NVARCHAR(10));
 ALTER TABLE R ADD CONSTRAINT UK UNIQUE (B);
```

Drop the unique constraint UK from table R.

```
ALTER TABLE R DROP CONSTRAINT UK;
```

Create table S. You add a referential constraint FK to table S that references column A of table R with delete cascade option.

```
CREATE ROW TABLE S (FA INT, B NVARCHAR(10));
 ALTER TABLE S ADD CONSTRAINT FK FOREIGN KEY(FA) REFERENCES R(A) ON DELETE CASCADE;
```

The following example creates a column table, creates a history table, and then alters the column table to configure and enable system versioning:

```
CREATE COLUMN TABLE account (
  account_id INT PRIMARY KEY,
  account_owner_id NVARCHAR(10),
  account_balance DOUBLE
 );

CREATE COLUMN TABLE account_history (
  account_id INT,
  account_owner_id NVARCHAR(10),
  account_balance DOUBLE,
  valid_from TIMESTAMP NOT NULL,
  valid_to TIMESTAMP NOT NULL
 );

ALTER TABLE account ADD (valid_from TIMESTAMP NOT NULL GENERATED ALWAYS AS ROW START);
ALTER TABLE account ADD (valid_to TIMESTAMP NOT NULL GENERATED ALWAYS AS ROW END);
ALTER TABLE account ADD PERIOD FOR SYSTEM_TIME(valid_from, valid_to);
ALTER TABLE account ADD SYSTEM VERSIONING HISTORY TABLE account_history;
```



</dd><dt><b>

Persistent memory

</b></dt>
<dd>

Alter a table’s PERSISTENT MEMORY specification and cascade the setting to partitions and columns:

```
ALTER TABLE myTable1 PERSISTENT MEMORY ON IMMEDIATE CASCADE;
```

Alter a column’s PERSISTENT MEMORY specification:

```
ALTER TABLE myTable2 ALTER (C1 INT PERSISTENT MEMORY DEFAULT);
```

Add a partition with a PERSISTENT MEMORY specification:

```
ALTER TABLE myTable3 ADD RANGE (C1) (PARTITION '0' <= VALUES < '10', PARTITION OTHERS PERSISTENT MEMORY ON DEFERRED);
```

Partition a table with a PERSISTENT MEMORY specification for selected partitions:

```
ALTER TABLE myTable4 PARTITION BY RANGE (C1) (PARTITION '0' <= VALUES < '10' PERSISTENT MEMORY ON IMMEDIATE, PARTITION OTHERS);
```

Alter a partition’s PERSISTENT MEMORY specification:

```
ALTER TABLE myTable5 ALTER PARTITION 10 PERSISTENT MEMORY DEFAULT;
```



</dd><dt><b>

Non-heterogeneous partitions

</b></dt>
<dd>

Convert a non-partitioned column store table named T1 to a range partitioned table.

```
CREATE COLUMN TABLE T1 (a INT, b INT);
ALTER TABLE T1 PARTITION BY RANGE (a) (PARTITION 10 <= VALUES < 20);
```

Add a new second-level partition to an existing range-partitioned table, making it a range-range partitioned table.

```
ALTER TABLE T1 PARTITION BY 
   RANGE (a) (PARTITION 10 <= VALUES < 20) SUBPARTITION BY RANGE (b) (PARTITION 100 <= VALUES < 150);
```

Redefine the existing first-level partition to ranges 10 - 15 and 15 - 20.

```
ALTER TABLE T1 PARTITION BY 
   RANGE (a) (PARTITION 10 <= VALUES < 15, PARTITION 15 <= VALUES < 20) 
   SUBPARTITION BY RANGE (b) (PARTITION 100 <= VALUES < 150);
```

Add a new partition to the second-level partition.

```
ALTER TABLE T1 ADD PARTITION (b) 150 <= VALUES < 200;
```

Move a partition.

```
ALTER TABLE T1 MOVE PARTITION 1 TO 'myhost:30201';
```

Move multiple partitions to new locations.

```
ALTER TABLE T2 MOVE PARTITION 1,2 TO 'myhost2:34240', PARTITON 3,4 TO 'myhost3:34242’ ONLINE;
```

Drop the partition range 10 - 15.

```
ALTER TABLE T1 DROP PARTITION (a) 10 <= VALUES < 15;
```

Merge all partitions into a single non-partitioned table.

```
ALTER TABLE T1 MERGE PARTITIONS; 
```

```
ALTER TABLE T1 PARTITION BY RANGE (a) (PARTITION 15 <= VALUES < 20 NUMA NODE ('3') DEFERRED);
```

Alter column table T1, setting the NUMA node preference at the partition level on NUMA node index 3. Since DEFERRED is specified, it sets only the NUMA preference for the partition; the actual allocations are made when the table is reloaded. IMMEDIATE alters column table T1, setting the NUMA node preference on partition 1, which already exists. The allocations are made immediately, and the table partition is reloaded to node 4.

```
ALTER TABLE T1 ALTER PARTITION 1 NUMA NODE ('4') IMMEDIATE;
```

Create a non-partitioned table named T2, convert the table to a range partitioned table, and then add an additional partition.

```
CREATE COLUMN TABLE T2 (a INT, b INT);
ALTER TABLE T2 PARTITION BY RANGE (a) (PARTITION VALUE = 1, PARTITION OTHERS);
ALTER TABLE T2 ADD PARTITION (a) 2 <= VALUES < 10;
```

Create a non-partitioned table named T3 and then convert the table to a range-range partitioned table.

```
CREATE COLUMN TABLE T3 (a INT, b INT);
ALTER TABLE T2 PARTITION BY RANGE (a) (PARTITION VALUE = 1, PARTITION OTHERS) 
SUBPARTITION BY RANGE (b) (PARTITION VALUE = 2);
```

Convert an existing hash partitioned table named T4 to a range partitioned table.

```
CREATE TABLE T4 (A INT, B INT) PARTITION BY HASH (A) PARTITIONS 2;
ALTER TABLE T4 PARTITION BY RANGE (A) (PARTITION 10 <= values < 20, PARTITION OTHERS);
```

Convert an existing range partitioned table named T5 to a hash partitioned table.

```
CREATE TABLE T5 (A INT, B INT) PARTITION BY RANGE (A) (PARTITION 10 <= values < 20, PARTITION OTHERS);
ALTER TABLE T5 PARTITION BY HASH (A) PARTITIONS 2;
```


<dl>
<dt><b>

Dynamic Range Partitioning

</b></dt>
<dd>

These examples are based on table A1 using this CREATE TABLE statement.

```
CREATE COLUMN TABLE A1 (A INT, B INT NOT NULL) PARTITION BY RANGE (A) (PARTITION VALUES = 10) 
   SUBPARTITION BY RANGE (B) (PARTITION VALUES = 20, PARTITION OTHERS);
```

Enable dynamic range partitioning on the OTHERS partition with a DYNAMIC TRHRESHOLD of 100.

```
ALTER TABLE A1 PARTITION OTHERS DYNAMIC THRESHOLD 100;
```

Add another partition from OTHERS.

```
ALTER TABLE A1 ADD PARTITION FROM OTHERS;
```

Drop any empty partitions except OTHERS.

```
ALTER TABLE A1 DROP EMPTY PARTITIONS;
```

Disable dynamic range partitioning on the OTHERS partition.

```
ALTER TABLE A1 PARTITION OTHERS NO DYNAMIC;
```



</dd>
</dl>



</dd><dt><b>

Heterogeneous partitions

</b></dt>
<dd>

Convert the non-partitioned table T1 to a range-range partitioned table. The table has four first-level partitions \(10-20,20-30,40,OTHERS\). Range 10-20 has three subpartition ranges \(0-10, 10-100, others\). Range 40 has two subpartitions ranges \(0-10, OTHERS\). Both subpartitions have dynamic range partitioning enabled.

```
CREATE COLUMN TABLE T1 (a INT, b INT NOT NULL);

ALTER TABLE T1 PARTITION BY RANGE (a)
   ((PARTITION 10 <= VALUES < 20 INSERT OFF, PARTITION 20 <= VALUES < 30 INSERT OFF) 
       SUBPARTITION BY RANGE (b) (PARTITION 0 <= VALUES < 10, PARTITION 10 <= VALUES < 100, PARTITION OTHERS DYNAMIC THRESHOLD 2),
    (PARTITION VALUES = 40)
       SUBPARTITION BY RANGE(B) (PARTITION 0 <= VALUES < 10, PARTITION OTHERS DYNAMIC THRESHOLD 2),
    (PARTITION OTHERS));
```

Convert the non-partitioned table T2 to a range-hash partitioned table. The first level has two partition ranges \(10-20, 20-30\). The INSERT OFF property means you can't add data to the partitions. The second level is a hash with two partitions.

```
CREATE COLUMN TABLE T2 (a INT, b INT);

ALTER TABLE T2 PARTITION BY RANGE (a) ((PARTITION 10 <= VALUES < 20 INSERT OFF, PARTITION 20 <= VALUES < 30 INSERT OFF) 
   SUBPARTITION BY HASH (b) PARTITIONS 2);
```

Add a new first-level range partition 41-50 to table T1. The new partition has a subpartition with one range 0-10.

```
ALTER TABLE T1 ADD PARTITION RANGE (a) ((PARTITION 41 <= VALUES < 50)
   SUBPARTITION by RANGE (b) (PARTITION 0 <= VALUES < 10));
```

Redefine the existing first-level partition range 10-20 to ranges 5-10 and 15-20. Each redefined range retains its original subpartition. All existing range values must be accounted for in the redefined structure or they will be dropped if they do not contain data.

```
ALTER TABLE T1 PARTITION BY RANGE (a)
   ((PARTITION 5 <= VALUES < 10, PARTITION 10 <= VALUES < 20 INSERT OFF, PARTITION 20 <= VALUES < 30 INSERT OFF)
        SUBPARTITION BY RANGE (b) (PARTITION 0 <= VALUES < 10, PARTITION 10 <= VALUES < 100, PARTITION OTHERS DYNAMIC THRESHOLD 2),
    (PARTITION VALUES = 40) SUBPARTITION BY RANGE(B) (PARTITION 0 <= VALUES < 10, PARTITION OTHERS DYNAMIC THRESHOLD 2),
    (PARTITION 41 <= VALUES < 50) SUBPARTITION by RANGE (b) (PARTITION 0 <= VALUES < 10),
    (PARTITION OTHERS));
```

Move partition 1 \(range 5-10\) on table T1 to host myhost on port 30203.

```
ALTER TABLE T1 MOVE PARTITION 1 TO 'myhost:30203';
```

Move range 5-10 with subpartition range 0 - 10 on table T1 to host myhost on port 30203.

```
ALTER TABLE T1 MOVE RANGE (a) ((PARTITION 5 <= VALUES < 10) SUBPARTITION BY RANGE (b) (PARTITION 0 <= VALUES < 10)) TO 'myhost:30203';
```

Move the hash subpartition of range 10-20 on table T2 to host myhost1 port 30203 and myhost2 port 30203.

```
ALTER TABLE T2 MOVE SUBPARTITIONS OF RANGE (a) ((PARTITION 10 <= VALUES < 20) to ('myhost1:30203', 'myhost2:30203);
```

Drop the first-level partition range 5-10 on table 1. The subpartitions for that range only are dropped. The subpartition ranges 10-20 and 20-30 remain.

```
ALTER TABLE T1 DROP PARTITION RANGE (a) ((PARTITION 5 <= VALUES < 10));
```

Drop subpartition range 10-100 in range 10-20 on table T1.

```
ALTER TABLE T1 ALTER PARTITION RANGE (a) ((PARTITION 10 <= VALUES < 20)) DROP PARTITION RANGE (b) ((PARTITION 10 <= VALUES < 100));
```

Assign the group name GROUP1 to partition 2 on table T1.

```
ALTER TABLE T1 ALTER PARTITION 2 SET GROUP NAME "GROUP1";
```

Assign the group name GROUP2 to partitions 1 and 2 on table T1.

```
ALTER TABLE T1 ALTER PARTITION (1,2) SET GROUP NAME "GROUP2";

```

Assign the group name GROUP2 and the group type HR to the partition range 10 - 20 and all its subpartitions on table T1.

```
ALTER TABLE T1 ALTER PARTITION RANGE (a) ((PARTITION 20 <= VALUES < 30)) SET GROUP NAME "GROUP2" GROUP TYPE "HR" CASCADE;
```

Remove the GROUP value from partition 2 on table T1.

```
ALTER TABLE T1 ALTER PARTITION 2 UNSET GROUP;
```

Remove the GROUP value from partitions 1 and 2 on table T1.

```
ALTER TABLE T1 ALTER PARTITION (1,2) UNSET GROUP;
```

Remove the GROUP value from the partition range 10 -20 and its subpartitions on table T1.

```
ALTER TABLE T1 ALTER PARTITION RANGE (a) ((PARTITION 20 <= VALUES < 30)) UNSET GROUP CASCADE;
```

This example creates a multilevel heterogeneous partitioned table and then applies the *<load\_unit\>* attribute first by partition number \(1\) and then to partition range \(10 to 20\).

```
CREATE COLUMN TABLE T4 (a INT, b INT) PARTITION BY RANGE(a) 
   ((PARTITION 10 <= VALUES < 20) SUBPARTITION BY RANGE (b) (PARTITION VALUES=100));

ALTER TABLE T4 ALTER PARTITION 1 COLUMN LOADABLE;
ALTER TABLE T4 ALTER PARTITION RANGE (a) ((PARTITION 10 <= VALUES < 20) 
   SUBPARTITION BY RANGE (b) (PARTITION VALUES = 100)) PAGE LOADABLE;
```


<dl>
<dt><b>

Dynamic Range Partitioning

</b></dt>
<dd>

These examples are based on table A1 using this CREATE TABLE statement.

```
CREATE COLUMN TABLE A1 (A INT, B INT NOT NULL) PARTITION BY RANGE (A) 
   ((PARTITION 10 <= VALUES < 20) 
      SUBPARTITION BY RANGE (B) (PARTITION 15 <= VALUES < 20, PARTITION OTHERS),
    (PARTITION VALUES = 30) 
      SUBPARTITION BY RANGE (B) (PARTITION VALUES=20, PARTITION OTHERS),
    (PARTITION OTHERS));
```

Enable dynamic range partitioning on range 10-20, subpartition 15-20 on table A1.

```
ALTER TABLE A1 PARTITION BY RANGE (A) 
   ((PARTITION 10 <= VALUES < 20) 
      SUBPARTITION BY RANGE (B) (PARTITION 15 <= VALUES < 20, PARTITION OTHERS DYNAMIC),
    (PARTITION VALUES = 30) 
      SUBPARTITION BY RANGE (B) (PARTITION VALUES=20, PARTITION OTHERS),
    (PARTITION OTHERS));
```

Add another partition from OTHERS on table A1.

```
ALTER TABLE A1 ADD PARTITION FROM OTHERS;
```

Drop any empty partitions except OTHERS on table A1.

```
ALTER TABLE A1 DROP EMPTY PARTITIONS;
```

Set the threshold to 2 for dynamic range partitioning on the subpartition of range 10-20 on table A1.

```
ALTER TABLE A1 PARTITION BY RANGE (A) 
   ((PARTITION 10 <= VALUES < 20) 
      SUBPARTITION BY RANGE (B) (PARTITION 15 <= VALUES < 20, PARTITION OTHERS DYNAMIC THRESHOLD 2),
    (PARTITION VALUES = 30) 
      SUBPARTITION BY RANGE (B) (PARTITION VALUES = 20, PARTITION OTHERS),
    (PARTITION OTHERS));
```

Disable dynamic range partitioning on the subpartition on range 10-20 on table A1.

```
ALTER TABLE A1 PARTITION BY RANGE (A) 
   ((PARTITION 10 <= VALUES < 20) 
      SUBPARTITION BY RANGE (B) (PARTITION 15 <= VALUES < 20, PARTITION OTHERS),
    (PARTITION VALUES = 30) 
      SUBPARTITION BY RANGE (B) (PARTITION VALUES = 20, PARTITION OTHERS),
    (PARTITION OTHERS));
```


<dl>
<dt><b>

Redefine Partitions

</b></dt>
<dd>

Alter the load unit of any range partition in default storage:

```
ALTER TABLE A1 PARTITION BY RANGE (A)
   (PARTITION 0 <= VALUES < 10 PAGE LOADABLE,
    PARTITION OTHERS COLUMN LOADABLE);
```



</dd>
</dl>



</dd>
</dl>



</dd><dt><b>

Altering annotations

</b></dt>
<dd>

The following example creates a table with annotations and then alters the annotations:

```
CREATE COLUMN TABLE t1(c1 INT) WITH ANNOTATIONS(
    SET 't_k1'='t_v1', 't_k2'='t_v2'
    COLUMN c1 SET 'c_k1'='c_v1', 'c_k2' = 'c_v2');

ALTER TABLE t1 WITH ANNOTATIONS(
    UNSET ALL SET 'k1' = 'v1', 'k2'='v2'
    COLUMN c1 UNSET ALL SET 'k1'='v1', 'k2'='v2');
```



</dd><dt><b>

NUMA node preferences

</b></dt>
<dd>

This example immediately unsets the NUMA node preference at the table level. The table is reloaded and allocations are performed by using the HASH scheme available in the attribute engine.

```
ALTER TABLE T1 NUMA NODE NULL IMMEDIATE;
```

This example alters column table T1, setting the NUMA node preference at the partition level on NUMA node index 3. Since DEFERRED is specified, it sets only the NUMA preference for the partition; the actual allocations are made when the table is reloaded.

```
ALTER TABLE T1 PARTITION BY RANGE (colint) (PARTITION '0' <= VALUES < '20' NUMA NODE ('3') DEFERRED);
```

This example immediately alters column table T1, setting the NUMA location preference to partition P0, which already exists. The allocations are made immediately, and the table partition is reloaded to node 4.

```
ALTER TABLE T1 ALTER PARTITION P0 NUMA NODE ('4') IMMEDIATE;
```

This example moves table T1 to NUMA node index 4, immediately allocating the entire table to NUMA node index 4:

```
ALTER TABLE T1 NUMA NODE ('4') IMMEDIATE;
```



</dd><dt><b>

Load unit

</b></dt>
<dd>

Alter the load unit for a table:

```
ALTER TABLE T PAGE LOADABLE CASCADE;
```

Add a range partition and specify the load unit:

```
ALTER TABLE T ADD RANGE (C1) (
   PARTITION 0 <= VALUES < 10,
   PARTITION OTHERS COLUMN LOADABLE);
```

Alter the load unit for a range partition:

```
ALTER TABLE T ALTER PARTITION 10 DEFAULT LOADABLE;
```

Altering the load unit for a column:

```
ALTER TABLE T ALTER (C1 INT DEFAULT LOADABLE);
```



</dd>
</dl>

**Related Information**  


[Table Partitioning](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2023_2_QRC/en-US/c2ea130bbb571014b024ffeda5090764.html "The partitioning feature of the SAP HANA database splits column-store tables horizontally into disjunctive sub-tables or partitions. In this way, large tables can be broken down into smaller, more manageable parts. Partitioning is typically used in multiple-host systems, but it may also be beneficial in single-host systems.") :arrow_upper_right:

[Non-Heterogeneous Alter Partition Clauses](non-heterogeneous-alter-partition-clauses-f7ae27c.md "Modifies the partitions of an existing table with a non-heterogeneous partitioning schema.")

[Heterogeneous Alter Partition Clauses](heterogeneous-alter-partition-clauses-a4258b8.md "Modifies the partitions of an existing table with a heterogeneous partitioning schema.")

[CREATE SEQUENCE Statement \(Data Definition\)](create-sequence-statement-data-definition-20d5092.md "Creates a sequence that generates primary key values that are unique across multiple tables, and for generating default values for a table.")

[SELECT Statement \(Data Manipulation\)](select-statement-data-manipulation-20fcf24.md "Queries data from the database.")

[REFERENTIAL\_CONSTRAINTS System View](../../020-System-Views-Reference/021-System-Views/referential-constraints-system-view-20ccc0a.md "Provides information about referential constraints.")

[CREATE TABLE Statement \(Data Definition\)](create-table-statement-data-definition-20d58a5.md "Creates a base or temporary table. See the CREATE VIRTUAL TABLE statement for creating virtual tables.")

[CREATE VIRTUAL TABLE Statement \(Data Definition\)](create-virtual-table-statement-data-definition-d2a0406.md "Creates a virtual table at a remote source.")

[TABLE\_PARTITIONS System View](../../020-System-Views-Reference/021-System-Views/table-partitions-system-view-c81d9be.md "Partition-specific information for partitioned tables.")

[SAP HANA Native Storage Extension](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2023_2_QRC/en-US/4efaa94f8057425c8c7021da6fc2ddf5.html "SAP HANA native storage extension is a general-purpose, built-in warm data store in SAP HANA that lets you manage less-frequently accessed data without fully loading it into memory. It integrates disk-based or flash-drive based database technology with the SAP HANA in-memory database for an improved price-performance ratio.") :arrow_upper_right:

[Table Placement](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2023_2_QRC/en-US/22888f9344954f258284d2dd936d0d0a.html "Table classification and table placement configuration, enhanced by partitioning, build the foundation for controlling the data distribution in a SAP HANA scale-out environment.") :arrow_upper_right:

[Predicates](../predicates-20a2ab2.md "")

[TABLES System View](../../020-System-Views-Reference/021-System-Views/tables-system-view-2101973.md "Provides information about tables in the database.")

[TABLE\_COLUMNS System View](../../020-System-Views-Reference/021-System-Views/table-columns-system-view-2100d33.md "Provides information about available table columns.")

[SAP HANA Cloud Configuration Parameter Reference](https://help.sap.com/viewer/138dcf7d779543608917a2307a6115f2/2023_2_QRC/en-US/4b4d88980622427ab2d6ca8c05448166.html "Reference documentation for public configuration parameters in SAP HANA Cloud.") :arrow_upper_right:

[SAP HANA Cloud, SAP HANA Database Security Guide](https://help.sap.com/viewer/a1317de16a1e41a6b0ff81849d80713c/2023_2_QRC/en-US/c3d9889e3c9843bdb834e9eb56f1b041.html#loioc3d9889e3c9843bdb834e9eb56f1b041 "The SAP HANA Cloud, SAP HANA Database Security Guide is the entry point for all information relating to the secure operation and configuration of SAP HANA Cloud, SAP HANA database.") :arrow_upper_right:

