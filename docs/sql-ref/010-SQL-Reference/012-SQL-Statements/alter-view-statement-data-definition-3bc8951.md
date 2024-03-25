<!-- loio3bc89515b93d4844bd700b3492673270 -->

# ALTER VIEW Statement \(Data Definition\)

Alters the definition, restrictions, or options on a view.



## Syntax

```
ALTER VIEW <view_name> {
   { [ ( <column_name_list> ) ] AS <subquery> [ <view_option_list> ] [ <view_cache> ]
   | <cache_clause>
   | <mask_clause>
   | <expression_macros>
   | <view_access_modes>
   | WITH ANONYMIZATION ( ALGORITHM <algorithm_name> { [ <view_level_parameters> ] [ <column_level_parameters> ] } ) }
   [ WITH [ NO ] STRUCTURED FILTER CHECK ]
```



## Syntax Elements


<dl>
<dt><b>

*<view\_name\>*

</b></dt>
<dd>

Creates the specified view, with an optional schema name.

```
<view_name> ::= [ <schema_name>.]<identifier>

<schema_name> ::= <unicode_name>
```



</dd><dt><b>

*<column\_list\>*

</b></dt>
<dd>

Specifies the column names for the view.

```
<column_list> ::= <column_name> [, <column_name> [,…] ]
```

When a column name is specified along with the view name, a query result is displayed with that column name. If a column name is omitted, then a query result gives an appropriate name to the column automatically. The number of column names must be the same as the number of columns returned from *<subquery\>*.



</dd><dt><b>

AS *<subquery\>*

</b></dt>
<dd>

Specifies the subquery to use for populating the view with data.



</dd><dt><b>

*<view\_option\_list\>*

</b></dt>
<dd>

```
<view_option_list> ::= 
   <associations_clause> <annotations_clause>
```


<dl>
<dt><b>

*<association\_clause\>*

</b></dt>
<dd>

Defines a relationship between the view and one or more tables \(or views, in the case of JOIN\).

```
<association_clause> ::= 
   WITH ASSOCIATIONS ( <association_def_list> )

<association_def_list> ::= 
   <association_def> [,<association_def> [,…] ]

<association_def> ::= 
   { <join_definition> | <column_def>  }

<join_definition> ::= 
   <join_cardinality> JOIN <table_or_view_identifier> [ AS <table_alias> ] ON { <condition> | <column_def> }

<join_cardinality> ::= 
   { MANY TO ONE
   | MANY TO MANY
   | ONE TO ONE
   | ONE TO MANY }

<column_def> ::= [ [ <schema_name>.]<table_ref>.]<column_name> [ AS <column_name> ]
```



</dd><dt><b>

*<annotations\_clause\>*

</b></dt>
<dd>

Specifies view-, column-, and parameter-level annotations in the form of key/value pairs. You can reference annotations in subsequent queries to filter results.

```
<annotations_clause> ::= 
   WITH ANNOTATIONS ( 
      { [ <set_view_annotations> ]
      | [ <set_column_annotations> ] 
      | [ <set_parameter_annotations> ]
   } )

<set_view_annotations> ::= <key_set_operation>

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

While you must specify annotation on at least one object with the WITH ANNOTATION clause \(view, column, or parameter\), there is no limit on the number of annotations or types of annotations you can specify. *<key\>* and *<value\>* represent the annotations you are configuring for the object \(view, column, or parameter\).



</dd>
</dl>



</dd><dt><b>

*<cache\_clause\>*

</b></dt>
<dd>

Changes result cache settings for a view.

```
<cache_clause> ::= 
   { <add_cache_clause> 
   | <alter_cache_clause>
   | <drop_cache_clause> }
```


<dl>
<dt><b>

*<add\_cache\_clause\>*

</b></dt>
<dd>

Caches the result of a table function with an optional projection list and filter conditions. A result cache can improve performance for subsequent queries on the view.

```
<add_cache_clause> ::= ADD [ <cache_type> ] CACHE [ NAME <cache_name> ]
   [ RETENTION <minute_value> ]
   [ OF <projection_list> ] 
   [ FILTER <filter_condition> ]
   [ <location_clause> ]
   [ FORCE ]
```


<dl>
<dt><b>

*<cache\_type\>*

</b></dt>
<dd>

Specify whether your result cache is static or dynamic.

```
<cache_type> ::= STATIC | DYNAMIC
```

A view has only one type of result cache. The default value is STATIC. Using a static result cache may result in stale data. A dynamic result cache ensures up-to-date data as it is partially or fully refreshed every time you run a query on the result cache.



</dd><dt><b>

*<cache\_name\>*

</b></dt>
<dd>

Specifies a unique name for the result cache. Multiple result caches for the same view are supported, but the properties of each result cache must be unique. If the cache name is not specified, an auto-generated result cache name is used \(\_SYS\_CACHE\#*<view\_name\>*\).



</dd><dt><b>

*<minute\_value\>*

</b></dt>
<dd>

Specifies the result cache retention period.

```
<minute_value> ::= <unsigned_integer>
```

Specifying a retention period ensures that data does not exceed the specified RETENTION period. Data that exceeds the retention period is refreshed and up-to-date data is returned. Since a dynamic result cache ensures up-to-date data, specifying a retention period of any value other than zero \(0\) generates an error. Dynamic result caches are only supported for SQL views that are defined as an aggregation on single-column tables.



</dd><dt><b>

*<projection\_list\>*

</b></dt>
<dd>

For static result caches, allows you to reduce the cached data by specifying a result cached projection list.

```
<projection_list> ::= <projection_name> [{, <projection_name>}] 

<projection_name> ::= <column_name> 
 | <aggr_type>(<column_name>) 

<aggr_type> ::= { SUM | MIN | MAX | COUNT | AVG}
```

If a column that is not part of the projection list is requested or included in the WHERE clause, then the result cache cannot be exploited. You can also direct an aggregation type of a specific column for the SQL view \(not supported for calculation view\). You specify a result cached projection list, and then the result cache includes aggregated results of that column and returns aggregated results only. This option is not supported for dynamic result caches.



</dd><dt><b>

*<filter\_condition\>*

</b></dt>
<dd>

Reduces the result cached data by specifying a filter condition.

```
<filter_condition> ::=
 <condition> OR <condition> 
 | <condition> AND <condition>
 | NOT <condition>
 | ( <condition> )
 | <predicate>

   
<predicate> ::= 
 <comparison_predicate>
 | <range_predicate>
 | <in_predicate> 
 | <like_predicate> 
 | <null_predicate>
 
<comparison_predicate> ::= 
 <table_expression> { = | != | <> | > | < | >= | <= } [ ANY | SOME | ALL ] ( <table_expression_list> )
 
<range_predicate> ::= 
 <table_expression> [ NOT ] BETWEEN <table_expression> AND <table_expression>
 
<in_predicate> ::= 
 <table_expression> [ NOT ] IN ( <table_expression_list> )
 

<like_predicate> ::= 
 <table_expression> [ NOT ] LIKE <table_expression> [ ESCAPE <table_expression> ]
 
<null_predicate> ::= 
 <table_expression> IS [ NOT ] NULL

<table_expression_list> ::= <table_expression> [, <table_expression> [,… ] ]
```

Only filtered results are cached. Predicates that contain subqueries are not supported.

For static result caches, all forms of non-parameterized query filters are supported. For parameterized query filters, only conjunctive forms are supported. For dynamic result caches, only parameterized query filters on string type columns in conjunctive forms are supported. For example:

```
column = ? [ AND <and_column = ?> ]
```



</dd><dt><b>

*<location\_clause\>*

</b></dt>
<dd>

Specifies the location where the result cache entry is created.

```
<location_clause> ::= AT [LOCATION] '<hostname>:<port_number>'[, ...]
```

By default, when you execute a query on a static or dynamic result cached view, the optimizer determines the result cache location. In some cases, the same result cache entry is created at multiple indexservers.



</dd><dt><b>

FORCE

</b></dt>
<dd>

For static result caches, forces the addition of a result cache without checking its cachability. This feature is only available for calculation views. This option is not supported for dynamic result caches.



</dd>
</dl>



</dd><dt><b>

*<alter\_cache\_clause\>*

</b></dt>
<dd>

Changes the result cache.

```
<alter_cache_clause> ::=  
   ALTER [ { STATIC | DYNAMIC  ] CACHE [ NAME <cache_name> ] 
   { RETENTION <minute_value> 
     | { { ADD | DROP } AT [ LOCATION ] '<hostname>:<port_number>'[, ...] 
       | { ADD | DROP } INDEX ON <column_name>
       }
   }
```

*<cache\_name\>* specifies the result cache being altered. If the cache name is not specified, the system uses the default cache name \_SYS\_CACHE\#*<function\_name\>*. If the default name doesn't exist, an error occurs.

For STATIC cache, you can change the retention value of the result cache of a view. For DYNAMIC cache, only the value 0 is supported.

Use LOCATION to change the location where the cache entry is created. By default, when you execute a query on a static or dynamic cached view, the optimizer determines the cache location. In some cases, the same cache entry is created at multiple indexservers. *<hostname\>*:*<port\_number\>* specifies the hostname and port of an currently running indexserver.

Use INDEX to create an index on a dynamic result cache to improve filter evaluation performance on the top of the dynamic result cache. INDEX is not supported for STATIC caches. DYNAMIC result cache indexes are restricted to single-node systems only.



</dd><dt><b>

*<drop\_cache\_clause\>*

</b></dt>
<dd>

Specifies to drop the result cache of a view.

```
<drop_cache_clause> ::= 
   DROP [ { STATIC | DYNAMIC } ] CACHE { NAME <cache_name> | ALL }
```

*<cache\_name\>* specifies the result cache being dropped.



</dd>
</dl>



</dd><dt><b>

*<mask\_clause\>*

</b></dt>
<dd>

Adds a new masking expression or changes or drops an existing mask expression. *<mask\_clause\>* does not change the view's column definitions. For an example of data masking, see the CREATE VIEW statement.

```
<mask_clause> ::=
   { ADD | ALTER } [{ DEFAULT | SESSION USER }] MASK (<column_mask_list>)
   | ALTER MASK ( <column_name> USING <mask_expression> [,…] )
   | DROP MASK ( <column_name>[,...] )

<mask_expression> ::= <expression>
```

When adding a mask expression, the mask behavior is defined for the object. New column masks must use the same mask mode. When altering, you can change the mask expression, but not the mode. Once all existing masks are dropped, you can add new masks using a different mask mode.

Masking behavior is supported on row and column tables, and SQL row and calculation views. It is not supported on any other type of tables \(virtual tables, extended tables, temporary tables etc.\) and views \(Join/Olap/Hierarchy views\). Only one masking behavior, definer owner-based \(DEFAULT MASK\) or session user based masking \(SESSION USER MASK\), is supported on a table or view with masked columns. You can combine both masking behaviors in an object hierarchy. For example, a view with session user based masking can be created on a table with owner-based masking. If masking is enforced on lower-level objects, results for higher-level objects, for unauthorized users, may be incorrect because some results data is masked; no error is returned indicating lower-level objects are masked. If not specified, DEFAULT is the default.

*<mask\_expression\>* can be any type of expression, including a user-defined function, that returns the same data type and length as the original column. For more information on data masking, see the *SAP HANA Cloud, SAP HANA Database Security Guide*.



</dd><dt><b>

*<expression\_macros\>*

</b></dt>
<dd>

Adds or drops one or more expression macros for the view.

Expression macros perform calculations on the results of a query on a view before the results are returned, and are called using the EXPRESSION\_MACRO function.

```
<expression_macros> ::=  
ADD EXPRESSION MACROS( <expression_macro_list> )
 | DROP EXPRESSION MACROS( <expression_macro_alias_list> )

<expression_macro_list> ::= <expression_macro> [, <expression_macro> [,…] ] 

<expression_macro> ::= <expression> AS <expression_macro_alias>

<expression_macro_alias_list> ::= <expression_macro_alias> [, <expression_macro_alias> [,…] ]
```

*<expression\>* can be any calculation or aggregation function expression on one or more columns in the query, including a call to the EXPRESSION\_MACRO function. A couple examples for *<expression\>* might be `AVG(columnA)`, or `EXPRESSION_MACRO(sum_colA)`, where `sum_colA` is another expression macro.

*<expression\_macro\_alias\>* is the name given to the expression macro. You cannot drop an expression macro if another expression macro references it; you must first drop the referring expression macro.



</dd><dt><b>

*<view\_access\_modes\>*

</b></dt>
<dd>

Specifies the access mode without recompiling the view query or propagating recompilations of dependent view.

```
<view_access_modes> ::= 
```


<dl>
<dt><b>

\[NO\] READ ONLY

</b></dt>
<dd>

Specifies whether the view is read only. If READ ONLY is specified, and one of the base objects is not updatable, then the view cannot be updated. If subsequently the base objects are changed to updatable, and the view is not READ ONLY, then the view becomes updatable without executing the ALTER VIEW statement again.



</dd>
</dl>


<dl>
<dt><b>

\[NO\] DDL ONLY

</b></dt>
<dd>

Controls whether users can query the view or update the underlying table. You can include views that are defined WITH DDL ONLY in other object definitions. Specifying WITH DDL ONLY prevents users from querying the view and from modifying the underlying table.



</dd>
</dl>



</dd><dt><b>

WITH ANONYMIZATION clause

</b></dt>
<dd>

Specifies data anonymization parameters for the view and its columns. You must execute a REFRESH VIEW statement after configuring anonymization parameters.

```
WITH ANONYMIZATION ( ALGORITHM <algorithm_name> { [ <view_level_parameters> ] [ <column_level_parameters> ] } )
```


<dl>
<dt><b>

*<algorithm\_name\>*

</b></dt>
<dd>

Specifies the algorithm to use to anonymize view data.

```
<algorithm_name> ::= { 'K-ANONYMITY' | 'DIFFERENTIAL_PRIVACY' | 'L-DIVERSITY' } 
```



</dd><dt><b>

*<view\_level\_parameters\>*

</b></dt>
<dd>

Specifies view-level anonymization parameters.

```
<view_level_parameters> ::= PARAMETERS <embedded_hierarchy_expression>
```

*<embedded\_hierarchy\_expression\>* is a string constant containing view-specific anonomization parameters.



</dd><dt><b>

*<column\_level\_parameters\>*

</b></dt>
<dd>

Specifies column-level anonymization parameters.

```
<column_level_parameters> ::= <column_spec> [ <column_spec> […] ]
<column_spec> ::= COLUMN <column_name> PARAMETERS <embedded_hierarchy_expression>
```

*<embedded\_hierarchy\_expression\>* is a string constant containing column-specific anonomization parameters.

*<column\_name\>* must be the name of a column previously specified in *<column\_name\_list\>*.



</dd>
</dl>

For more information, see the topics on data anonymization in the *SAP HANA Cloud, SAP HANA Database Administration Guide*.



</dd><dt><b>

STRUCTURED FILTER CHECK

</b></dt>
<dd>

Allows execution context to control access to rows in database objects. This clause is only supported for SQL and parameterized SQL views.



</dd>
</dl>



## Description

Alters the definition, restrictions, or options on a view.

To change the comment on a view, use the COMMENT ON statement.



<a name="loio3bc89515b93d4844bd700b3492673270__section_c5g_l3g_gcb"/>

## Examples

**Result caching examples**

The following example creates a table named TAB, and then creates a view, V, that selects all records from it:.

```
CREATE COLUMN TABLE TAB (COL1 INT PRIMARY KEY, COL2 INT);
CREATE VIEW V AS SELECT DISTINCT COL1, COL2 FROM TAB;
```

The following example changes the retention value of the result cache of the view V.

```
ALTER VIEW V ALTER STATIC CACHE RETENTION 20;
```

The following example drops the result cache of view V.

```
ALTER VIEW V DROP STATIC CACHE;
```

The following example enables dynamic result caching on view V.

```
ALTER V ADD DYNAMIC CACHE;
```

The following example removes the location specifications so that there are no restrictions on the cache entry location for `view_a`.

```
ALTER VIEW view_a ALTER STATIC CACHE DROP AT LOCATION 'myhost2:00002';
```

The following statements show how you can add, alter, or drop the RESULT CACHE on a view:

```
CREATE ROW TABLE TAB (COL1 INT PRIMARY KEY, COL2 INT);
CREATE VIEW V AS SELECT * FROM TAB;
ALTER VIEW V ADD STATIC CACHE RETENTION 10;
ALTER VIEW V ALTER STATIC CACHE RETENTION 20;
ALTER VIEW V DROP STATIC CACHE;
```

**Expression macros examples**

The following statements create a view with two expression macros \(`sum_a` and `count_a`\) and then alters the view to add another expression macro \(`avg_a`\) to it:

```
CREATE TABLE t1(a INT);
CREATE VIEW v1 AS SELECT * FROM t1 WITH EXPRESSION MACROS(SUM(a) AS sum_a, COUNT(a) AS count_a);
ALTER VIEW v1 ADD EXPRESSION MACROS(AVG(a) AS avg_a);
```

The following statement alters the view to add an expression macro \(`avg2_a`\) that also calculates the average of column `a` but by using two of the other expression macros in the calculation:

```
ALTER VIEW v1 ADD EXPRESSION MACROS(EXPRESSION_MACRO(sum_a) / EXPRESSION_MACRO(count_a) AS avg2_a);
```

The following example drops the two expression macros `avg_a` and `avg2_a`:

```
ALTER VIEW v1 DROP EXPRESSION MACROS( avg_a, avg2_a );
```

**WITH ANNOTATIONS examples**

The following statement alters annotations on the myView view:

```
ALTER VIEW myView WITH ANNOTATIONS (
 UNSET 'key1' SET 'key1' = 'value1'
 COLUMN column1 UNSET 'Key2' SET 'Key2' = 'value2' );
```

**WITH DDL ONLY examples**

The following statements show how to use the WITH DDL ONLY clause to control whether users can query a view:

```
CREATE TABLE t1 (a int, b int);
CREATE VIEW v1 AS SELECT * FROM t1 WITH DDL ONLY;

ALTER VIEW v1 AS SELECT * FROM t1 WITH NO DDL ONLY;
SELECT * FROM v1; -- OK
SELECT IS_DDL_ONLY FROM VIEWS WHERE VIEW_NAME = 'V1'; -- FALSE
 
ALTER VIEW v1 AS SELECT * FROM t1 WITH DDL ONLY;
SELECT * FROM v1; -- invalid view name: cannot select the DDL only mode view
```

**Related Information**  


[CREATE VIEW Statement \(Data Definition\)](create-view-statement-data-definition-20d5fa9.md "Creates a view on the database.")

[VIEW\_EXPRESSION\_MACROS System View](../../020-System-Views-Reference/021-System-Views/view-expression-macros-system-view-d163421.md "Describes the expression macros defined for views.")

[EXPRESSION\_MACRO Function \(Miscellaneous\)](../011-SQL-Functions/expression-macro-function-miscellaneous-a8d1145.md "Returns aggregated results from a query.")

[COMMENT ON Statement \(Data Definition\)](comment-on-statement-data-definition-20d3817.md "Adds a comment to an object in the database, or removes an existing comment.")

[ANNOTATE Statement \(Data Definition\)](annotate-statement-data-definition-534df83.md "Annotates SQL objects such as tables, views, columns, table functions, procedures, and parameters.")

[ANNOTATIONS System View](../../020-System-Views-Reference/021-System-Views/annotations-system-view-da2b930.md "Provides information about annotations that have been added to SQL objects.")

[REFRESH VIEW Statement \(Data Definition\)](refresh-view-statement-data-definition-81e1583.md "Refreshes an anonymized view.")

[Data Anonymization](https://help.sap.com/viewer/a1317de16a1e41a6b0ff81849d80713c/2024_1_QRC/en-US/6cf9d55f4d3d45b0bcdb41756d86629f.html "Anonymization methods available in the SAP HANA Cloud, SAP HANA database allow you to gain statistically valid insights from your data while protecting the privacy of individuals.") :arrow_upper_right:

[Predicates](../predicates-20a2ab2.md "")

[SAP HANA Cloud, SAP HANA Database Security Guide](https://help.sap.com/viewer/a1317de16a1e41a6b0ff81849d80713c/2024_1_QRC/en-US/c3d9889e3c9843bdb834e9eb56f1b041.html#loioc3d9889e3c9843bdb834e9eb56f1b041 "The SAP HANA Cloud, SAP HANA Database Security Guide is the entry point for all information relating to the secure operation and configuration of SAP HANA Cloud, SAP HANA database.") :arrow_upper_right:

