<!-- loio20d5fa9b75191014a33eee92692f1702 -->

# CREATE VIEW Statement \(Data Definition\)

Creates a view on the database.



<a name="loio20d5fa9b75191014a33eee92692f1702__sql_create_view_1sql_create_view_syntax"/>

## Syntax

```
CREATE [ OR REPLACE ] VIEW <view_name> [ COMMENT <string_literal> ]
   [ ( <column_name_list> ) ] [ ( <parameterized_view_clause> ) ] 
   <as_subquery> [ <with_association_clause> ]
   [ WITH EXPRESSION MACROS( <expression_macro_list> ) ]
   [ WITH <annotations> ]
   [ WITH STRUCTURED PRIVILEGE CHECK ]
   [ WITH ANONYMIZATION ( ALGORITHM <algorithm_name> { [ <view_level_parameters> ] [
<column_level_parameters> ] } ) ]
   [ WITH [ CHECK OPTION ][ <mask_clause> ] 
      | WITH [READ ONLY] [DDL ONLY] [ <mask_clause> ] ]
   [ <cache_clause> ]

```



<a name="loio20d5fa9b75191014a33eee92692f1702__sql_create_view_1sql_create_view_syntax_elements"/>

## Syntax Elements


<dl>
<dt><b>

OR REPLACE

</b></dt>
<dd>

Replaces the view if it already exists; otherwise, if the view does not exist, it is created.

A CREATE OR REPLACE operation does not change the ID of an existing view, and maintains any privileges associated with the view.

OR REPLACE cannot be specified if the WITH ANONYMIZATION clause is specified.



</dd><dt><b>

*<view\_name\>*

</b></dt>
<dd>

Creates the specified view, with an optional schema name.

```
<view_name> ::= [ <schema_name>.]<identifier>

<schema_name> ::= <unicode_name>
```



</dd><dt><b>

COMMENT *<string\_literal\>*

</b></dt>
<dd>

Specifies a descriptive comment for the view.

Specifying this clause saves you from having to execute a separate COMMENT ON statement for the view after it is created.



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

*<parameterized\_view\_clause\>*

</b></dt>
<dd>

Defines the view columns by using parameters that can take input when queried.

```
<parameterized_view_clause> ::= <parameter_definition> [,...]
<parameter_definition> ::= IN <parameter_name> <parameter_datatype> [ <default_value> ]
```

*<parameterized\_view\_clause\>* can be specified with or without a *<column\_name\_list\>* specification, as shown respectively below:

```
CREATE VIEW myView2 (c1, c2) (IN p1 int, IN p2 NVARCHAR(10)) AS SELECT col1, col2 FROM myTable1 WHERE col1=:p1 AND col2=:p2;

CREATE VIEW myView1 (IN p1 INT, IN p2 NVARCHAR(10)) AS SELECT col1, col2 FROM myTable1 WHERE col1=:p1 AND col2=:p2;
```

The parameter references in the WHERE clause must be preceded by a colon \(for example, **:p1**\) to differentiate the parameter reference from a column reference.

Parameterizing a view allows you to pass values to search for as parameters when querying the view. For example, `SELECT * FROM v1(1, 'abc');` is semantically equivalent to `SELECT * FROM (SELECT col1, col2 FROM myTable1 WHERE col1=1 AND col2='abc') v1;`.

*<default\_value\>* specifies the value to use, based on the *<parameter\_datatype\>*, if no value is specified.



</dd><dt><b>

*<as\_subquery\>*

</b></dt>
<dd>

The query that forms the definition for the data in the view.

```
<as_subquery> ::= { AS ( <subquery> ) | <with_clause> }
<with_clause> :: ( WITH <alias> AS ( <subquery> AS <alias> [,... ] ) SELECT <expression> FROM <alias>

```


<dl>
<dt><b>

*<with\_clause\>*

</b></dt>
<dd>

Defines the columns for the view by using a common table expression.



</dd>
</dl>



</dd><dt><b>

*<with\_association\_clause\>*

</b></dt>
<dd>

Defines a relationship between the view and one or more tables \(or views, in the case of JOIN\).

```
<with_association_clause> ::= WITH ASSOCIATIONS ( <association_def_list> )

<association_def_list> ::= <association_def> [,<association_def> [,…] ]
<association_def> ::= { <join_definition> | <column_def>  }

<join_definition> ::= 
 <join_cardinality> JOIN <table_or_view_identifier> [ AS <table_alias> ] ON { <condition> | <column_def> }

<join_cardinality> ::= 
 MANY TO ONE
 | MANY TO MANY
 | ONE TO ONE
 | ONE TO MANY

<column_def> ::= [ [ <schema_name>.]<table_ref>.]<column_name> [ AS <column_name> ]
```



</dd><dt><b>

*<mask\_clause\>*

</b></dt>
<dd>

Adds new masking expression or drops an existing mask expression.

```
<mask_clause> ::= [ { DEFAULT | SESSION USER } ] MASK (< column_name> USING <mask_expression> [,...] )

<column_name> ::= <identifier>

<mask_expression> ::= <expression>
```

Masking behavior is supported on row and column tables, and SQL row and calculation views. It is not supported on any other type of tables \(virtual tables, extended tables, temporary tables etc.\) and views \(Join/Olap/Hierarchy views\).

Only one masking behavior, definer owner-based \(DEFAULT MASK\) or session user based masking \(SESSION USER MASK\), is supported on a table or view with masked columns. You can combine both masking behaviors in an object hierarchy. For example, a view with session user based masking can be created on a table with owner-based masking.

If not specified, DEFAULT is the default.

*<mask\_expression\>* can be any type of expression, including a user-defined function, that returns the same data type and length as the original column.

For more information on data masking, see the *SAP HANA Cloud, SAP HANA Database Security Guide*.



</dd><dt><b>

WITH EXPRESSION MACROS \(*<expression\_macro\_list\>*\)

</b></dt>
<dd>

Creates one or more expression macros on the view that can be called later by using the EXPRESSION\_MACRO function in a query on the view.

```
WITH EXPRESSION MACROS( <expression_macro_list> )

<expression_macro_list> ::= <expression_macro> [, <expression_macro> [,…] ] 

<expression_macro> ::=
<expression> AS <alias>

<expression_macro> ::= 
{ <expression> | <expression_macro> } AS <alias>
| <expression_macro>
```


<dl>
<dt><b>

*<expression\_macro\_list\>*

</b></dt>
<dd>

Is a list of expression macros being created on the specified view.



</dd><dt><b>

*<expression\_macro\>*

</b></dt>
<dd>

Use *<expression\_macro\>* to reference an existing expression macro. When creating a macro expression that references another macro expression, the macro expression that is being referenced must be defined prior to the macro expression that references it.

When using *<expression\_macro\>* to reference an existing expression macro, then the AS clause is optional. Use the AS clause to give the new expression macro a different alias, or omit the AS clause to use the alias of the referenced expression macro.

An example for *<expression\_macro\>* is `sum_colA AS sum_colB` where `sum_colA` is a predefined expression macro.



</dd><dt><b>

*<expression\>*

</b></dt>
<dd>

*<expression\>* can be any calculation or aggregation function expression on one or more columns in the query. When using *<expression\>* to create a new expression macro, you must use the AS clause to specify an alias for the expression macro. An example for *<expression\>* that is a new expression macro is `AVG(columnA)`.



</dd><dt><b>

*<alias\>*

</b></dt>
<dd>

*<alias\>* is the name given to the expression macro.



</dd>
</dl>



</dd><dt><b>

WITH *<annotations\>*

</b></dt>
<dd>

Specifies view-, column-, and parameter-level annotations in the form of key/value pairs. You can reference annotations in subsequent queries to filter results.

```
<with_annotation_clause> ::= WITH ANNOTATIONS ( { [ <set_view_annotations> ] [ <set_column_annotations> ] [ <set_parameter_annotations> ] } )

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

While you must specify annotation on at least one object with the WITH ANNOTATION clause \(view, column, or parameter\), there is no limit on the number of annotations or types of annotations you can specify.

*<key\>* and *<value\>* represent the annotations you are configuring for the object \(view, column, or parameter\).



</dd><dt><b>

*<cache\_clause\>*

</b></dt>
<dd>

Controls whether the user can dynamically or statically cache the result of the view and get stale data. A result cache can improve performance for subsequent queries on the view.

```
<cache_clause> ::= [ WITH [ <cache_type> ] CACHE [ NAME <cache_name> ]
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

WITH DDL ONLY

</b></dt>
<dd>

Prevents users from querying the view and from updating the underlying table.



</dd><dt><b>

WITH READ ONLY

</b></dt>
<dd>

Prevents the user from updating the view.



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



</dd>
</dl>



## Description

The CREATE VIEW statement effectively creates a virtual table based on the results of an SQL statement. It is not a real table as it does not contain any data.

Update operations on views are supported when the following conditions are met:

-   Each column in the view maps to the column of a single table.

-   If a column in a view base table has a NOT NULL constraint without a default value, then the column must be included in view columns so that inserts can be performed.

-   The view cannot contain an aggregate or analytic function in a SELECT list. For example, the following functions are not allowed:

    -   TOP, SET, or DISTINCT operator in a SELECT list

    -   an ORDER BY clause.


-   The view cannot contain a subquery in a SELECT list

-   The view cannot contain a sequence value \(CURRVAL, NEXTVAL\)

-   The view cannot contain a column view as the base view


If the base views or tables are updatable, then a view on the base views or tables can also be updatable if the above conditions are met.

When WITH CHECK OPTION is specified, the WHERE clause cannot contain LOB data type columns, spatial data type columns, or GENERATED ALWAYS columns. When WITH CHECK OPTION is specified, the WHERE the clause of the subquery is checked against the values being inserted or updated.



<a name="loio20d5fa9b75191014a33eee92692f1702__section_k25_zdh_qbb"/>

## Permissions

To create or replace a view requires one of the following:

-   For views owned by self:
    -   If you own all underlying objects of the view, no additional privilege is required.

-   For views owned by others:
    -   To create a view, you need one of the following:
        -   CREATE ANY schema level privilege granted on the view.

    -   To replace an existing view, you need one of the following:
        -   CREATE ANY and DROP schema level privilege granted on the view.


-   Regardless of view ownership, you require the proper privilege on its base objects referenced by the view.



<a name="loio20d5fa9b75191014a33eee92692f1702__section_jj1_1nd_tfb"/>

## Examples

**WITH CHECK OPTION example:**

Create table A.

```
CREATE COLUMN TABLE A (A INT PRIMARY KEY, B INT);
```

Create a view, v, that selects all records from table A.

```
CREATE VIEW v AS SELECT * FROM A;
```

Create a view, v, with WITH CHECK OPTION. When WITH CHECK OPTION is specified, the WHERE the clause of the subquery is checked.

```
CREATE VIEW v AS SELECT * FROM A WHERE A > 0 WITH CHECK OPTION;
 INSERT INTO v VALUES(1); -- succeeds
 INSERT INTO v VALUES(0); -- fails
 UPDATE v set a = 0; -- fails
```

**Static and dynamic result cache examples:**

Create a view, V, with a static result cache retention period of 10 minutes.

```
CREATE VIEW V AS SELECT DISTINCT A, B FROM A  
WITH STATIC CACHE RETENTION 10;
```

Restrict the cache entry location for view\_a to the location myhost2:00002.

```
CREATE VIEW view_a AS SELECT DISTINCT A, B FROM A
   WITH STATIC CACHE
   AT LOCATION 'myhost2:00002';
```

Create a view with a dynamic result cache.

```
CREATE VIEW V AS SELECT DISTINCT A, B FROM A
WITH DYNAMIC CACHE;
```

The cache is refreshed whenever it is queried.

**Masking examples:**

Create the credit\_card\_mask function and then create a view on the fictional table credit\_card\_tab that uses the credit\_card\_mask function to mask sensitive data.

```
CREATE FUNCTION credit_card_mask(input NVARCHAR(19))
   RETURNS output NVARCHAR(19) 
   LANGUAGE SQLSCRIPT
   AS temp NVARCHAR(19);

BEGIN
   SELECT LEFT(input, 4) ||'-XXXX-XXXX-'||
   RIGHT(input, 4) INTO temp 
   FROM SYS.DUMMY;
   output:= temp;
END;
```

```
CREATE VIEW credit_card_view
   AS SELECT * FROM credit_card_tab
   WITH MASK (CREDIT_CARD USING credit_card_mask(credit_card));
```

In this example for data masking, execute the following statements to create three users.

```
CREATE USER mask_owner PASSWORD Password1234 NO FORCE_FIRST_PASSWORD_CHANGE;
CREATE USER data_owner PASSWORD Password1234 NO FORCE_FIRST_PASSWORD_CHANGE;
CREATE USER end_user PASSWORD Password1234 NO FORCE_FIRST_PASSWORD_CHANGE;
```

Connect as data\_owner and create a table called credit\_tab and populate it with sensitive data.

```
CONNECT data_owner PASSWORD Password1234;
CREATE ROW TABLE credit_tab (Name NVARCHAR(20), CREDIT_CARD NVARCHAR(19));
INSERT INTO credit_tab VALUES ('John', '1111-1111-1111-1111');
INSERT INTO credit_tab VALUES ('James', '2222-2222-2222-2222');
```

Connect as mask\_owner and create the user-defined function credit\_mask and grant execute permission on the function to data\_owner.

```
CONNECT mask_owner PASSWORD Password1234;
CREATE FUNCTION credit_mask(INPUT NVARCHAR(19))
RETURNS OUTPUT NVARCHAR(19) LANGUAGE SQLSCRIPT AS
    temp NVARCHAR(19);
BEGIN
     SELECT LEFT(INPUT,4) || '-XXXX-XXXX-' || RIGHT(INPUT,4) INTO temp FROM SYS.DUMMY;
     OUTPUT := temp;
END;
GRANT EXECUTE ON credit_mask TO data_owner;
```

Connect as data\_owner and create the view credit\_view using the credit\_mask function as the masking expression.

```
CONNECT data_owner PASSWORD Password1234;
CREATE VIEW credit_view AS SELECT * FROM credit_tab
WITH MASK (CREDIT_CARD USING mask_owner.credit_mask(credit_card));
GRANT SELECT ON credit_view TO end_user;
```

Connect as end\_user and query credit\_view.

```
CONNECT end_user PASSWORD Password1234;
SELECT * FROM data_owner.credit_view;
```

The query returns the following masked results:


<table>
<tr>
<th valign="top">

NAME

</th>
<th valign="top">

CREDIT\_CARD

</th>
</tr>
<tr>
<td valign="top">

John

</td>
<td valign="top">

1111-XXXX-XXXX-1111

</td>
</tr>
<tr>
<td valign="top">

James

</td>
<td valign="top">

2222-XXXX-XXXX-2222

</td>
</tr>
</table>

Connect as data\_owner and alter the masking definition for credit\_view.

```
CONNECT data_owner PASSWORD Password1234;
ALTER VIEW credit_view AS SELECT name, credit_card FROM credit_tab 
WITH MASK (NAME USING 'AAAA', CREDIT_CARD USING 'XXXX');
```

Connect as end\_user and query credit\_view again.

```
CONNECT end_user PASSWORD Password1234;
SELECT * FROM data_owner.credit_view;
```

The query returns the following masked results:


<table>
<tr>
<th valign="top">

NAME

</th>
<th valign="top">

CREDIT\_CARD

</th>
</tr>
<tr>
<td valign="top">

AAAA

</td>
<td valign="top">

XXXX

</td>
</tr>
<tr>
<td valign="top">

AAAA

</td>
<td valign="top">

XXXX

</td>
</tr>
</table>

Connect as data\_owner and drop masking for the name and credit\_card columns.

```
CONNECT data_owner PASSWORD Password1234;
ALTER VIEW credit_view DROP MASK (NAME, CREDIT_CARD);
```

Connect as end\_user and query credit\_view.

```
CONNECT end_user PASSWORD Password1234;
SELECT * FROM data_owner.credit_view;
```

Because data masking has been dropped, all data contained in the view is now visible.


<table>
<tr>
<th valign="top">

NAME

</th>
<th valign="top">

CREDIT\_CARD

</th>
</tr>
<tr>
<td valign="top">

John

</td>
<td valign="top">

1111-1111-1111-1111

</td>
</tr>
<tr>
<td valign="top">

James

</td>
<td valign="top">

2222-2222-2222-2222

</td>
</tr>
</table>

Connect as data\_owner and mask data in the credit\_card column by executing the following statement.

```
CONNECT data_owner password Password1234;
ALTER VIEW credit_view ADD MASK (CREDIT_CARD USING 'XXXX');
```

Connect as end\_user and query credit\_view.

```
CONNECT end_user PASSWORD Password1234;
SELECT * FROM data_owner.credit_view;
```

The data in the credit\_card column is masked in the result set as follows:


<table>
<tr>
<th valign="top">

NAME

</th>
<th valign="top">

CREDIT\_CARD

</th>
</tr>
<tr>
<td valign="top">

John

</td>
<td valign="top">

XXXX

</td>
</tr>
<tr>
<td valign="top">

James

</td>
<td valign="top">

XXXX

</td>
</tr>
</table>

Connect as data\_owner and alter the masking information on the credit card to once again use the credit\_mask function.

```
CONNECT data_owner PASSWORD Password1234;
ALTER VIEW credit_view ALTER MASK (CREDIT_CARD USING mask_owner.credit_mask(credit_card));
```

Connect as end\_user and query credit\_view.

```
CONNECT end_user PASSWORD Password1234;
SELECT * FROM data_owner.credit_view;
```

The data in the result set is once again masked by using the credit\_mask function.


<table>
<tr>
<th valign="top">

NAME

</th>
<th valign="top">

CREDIT\_CARD

</th>
</tr>
<tr>
<td valign="top">

John

</td>
<td valign="top">

1111-XXXX-XXXX-1111

</td>
</tr>
<tr>
<td valign="top">

James

</td>
<td valign="top">

2222-XXXX-XXXX-2222

</td>
</tr>
</table>

**WITH EXPRESSION MACROS examples:**

The following statements create a table, insert data, and create a view with two expression macros \(`sum_a` and `count_a`\) that calculate the sum and count of column `t1.a`, respectively:

```
CREATE TABLE t1(a INT);
INSERT INTO t1 VALUES(10);
INSERT INTO t1 VALUES(20);
CREATE VIEW v1 AS SELECT * FROM t1 WITH EXPRESSION MACROS(SUM(a) AS sum_a, COUNT(a) AS count_a);
```

The following statements create a view, v1, with two expression macros:

```
CREATE TABLE t(x INT, y INT);
CREATE VIEW v1 AS SELECT * FROM t WITH EXPRESSION MACROS (
   SUM(x) AS sum_x,
   AVG(y) AS avg_y
);
```

Now execute the following statements to create a second view, v2, with three expression macros.

```
CREATE VIEW v2 AS SELECT * FROM v1 WITH EXPRESSION MACROS (
   sum_x AS sum_x2,
   avg_y,
   COUNT(x) AS count_x
);
```

The first two expression macros are propagated from v1. sum\_x is renamed to sum\_x2 for v2, whereas avg\_y retains its alias. The third expression macro is newly created as count\_x.

**WITH ANNOTATIONS example:**

The following example creates a table with annotations and then creates a view that also has annotations:

```
CREATE TABLE t1(c1 INT) WITH ANNOTATIONS(
    SET 't_k1' = 't_v1', 't_k2' = 't_v2'
    COLUMN c1 SET 'c_k1' = 'c_v1', 'c_k2' = 'c_v2');

CREATE VIEW v1 AS SELECT * FROM t1 WITH ANNOTATIONS(
    SET 'v_k1' = 'v_v1', 'v_k2' = 'v_v2'
    COLUMN c1 SET 'c_k1' = 'c_v1', 'c_k2' = 'c_v2'
```

**WITH DDL ONLY example:**

The following statements show how you to use the WITH DDL ONLY clause to control whether users can query a view:

```
CREATE TABLE t1 (a int, b int);
CREATE VIEW v1 AS SELECT * FROM t1 WITH DDL ONLY;

SELECT * FROM v1; -- invalid view name: cannot select the view because it is in DDL-only mode
SELECT IS_DDL_ONLY from VIEWS where VIEW_NAME = 'V1'; -- returns TRUE

CREATE VIEW v2 AS SELECT * FROM v1; -- you can select from the view
```

**WITH ANONYMIZATION example:** 

The following statements create a table called `Illness` with sensitive data in a column called `Illness` \(illness-related\), and populate the table with data:

```
CREATE COLUMN TABLE Illness (
  -- Sequential Column 
  ID BIGINT NOT NULL PRIMARY KEY GENERATED ALWAYS AS IDENTITY,
  -- Identifiers
  Name NVARCHAR(10),
  -- Quasi Identifiers (QIDs) (to be generalized) 
  Gender NVARCHAR(1) NOT NULL,
  City NVARCHAR(10) NOT NULL,
  -- Sensitive Data
  Illness NVARCHAR(10) NOT NULL);

INSERT INTO ILLNESS VALUES ('Paul', 'M', 'Paris', 'BRONCHITIS');
INSERT INTO ILLNESS VALUES ('Martin', 'M', 'Munich', 'ANGINA');
INSERT INTO ILLNESS VALUES ('Nils', 'M', 'Nice', 'FLU');
INSERT INTO ILLNESS VALUES ('Annika', 'F', 'Munich', 'BROKEN LEG');
```

You can now create a view that anonymizes the data:

```
CREATE VIEW Illness_K_Anon (ID, Gender, Location, Illness)
            AS SELECT ID, Gender, City AS Location, Illness
            FROM Illness
            WITH ANONYMIZATION ( ALGORITHM 'K-ANONYMITY'
            PARAMETERS '{"data_change_strategy": "qualified", "k": 2}'
            COLUMN ID PARAMETERS '{"is_sequence": true}'
            COLUMN Gender PARAMETERS '{"is_quasi_identifier":true, "hierarchy":{"embedded": [["F"], ["M"]]}}'
            COLUMN Location PARAMETERS '{"is_quasi_identifier":true, "hierarchy":{"embedded": [["Paris", "France"], ["Munich", "Germany"], ["Nice", "France"]]}}');
         
```

After you create the anonymized view, you must refresh it to select from it:

```
REFRESH VIEW Illness_K_Anon ANONYMIZATION;
```

View the anonymized data in the view:

```
SELECT * FROM Illness_K_Anon;
```


<table>
<tr>
<th valign="top">

ID

</th>
<th valign="top">

GENDER

</th>
<th valign="top">

LOCATION

</th>
<th valign="top">

ILLNESS

</th>
</tr>
<tr>
<td valign="top">

1

</td>
<td valign="top">

\*

</td>
<td valign="top">

France

</td>
<td valign="top">

BRONCHITIS

</td>
</tr>
<tr>
<td valign="top">

2

</td>
<td valign="top">

\*

</td>
<td valign="top">

Germany

</td>
<td valign="top">

ANGINA

</td>
</tr>
<tr>
<td valign="top">

3

</td>
<td valign="top">

\*

</td>
<td valign="top">

France

</td>
<td valign="top">

FLU

</td>
</tr>
<tr>
<td valign="top">

4

</td>
<td valign="top">

\*

</td>
<td valign="top">

Germany

</td>
<td valign="top">

BROKEN LEG

</td>
</tr>
</table>

**Related Information**  


[ALTER VIEW Statement \(Data Definition\)](alter-view-statement-data-definition-3bc8951.md "Alters the definition, restrictions, or options on a view.")

[VIEW\_EXPRESSION\_MACROS System View](../../020-System-Views-Reference/021-System-Views/view-expression-macros-system-view-d163421.md "Describes the expression macros defined for views.")

[EXPRESSION\_MACRO Function \(Miscellaneous\)](../011-SQL-Functions/expression-macro-function-miscellaneous-a8d1145.md "Returns aggregated results from a query.")

[Expressions](../expressions-20a4389.md "An expression is a clause that can be evaluated to return values.")

[REFRESH VIEW Statement \(Data Definition\)](refresh-view-statement-data-definition-81e1583.md "Refreshes an anonymized view.")

[VIEWS System View](../../020-System-Views-Reference/021-System-Views/views-system-view-2102bf2.md "Lists available views.")

[VIEW\_COLUMNS System View](../../020-System-Views-Reference/021-System-Views/view-columns-system-view-21028f1.md "Lists available view columns.")

[SAP HANA Cloud, SAP HANA Database Security Guide](https://help.sap.com/viewer/a1317de16a1e41a6b0ff81849d80713c/2023_4_QRC/en-US/c3d9889e3c9843bdb834e9eb56f1b041.html#loioc3d9889e3c9843bdb834e9eb56f1b041 "The SAP HANA Cloud, SAP HANA Database Security Guide is the entry point for all information relating to the secure operation and configuration of SAP HANA Cloud, SAP HANA database.") :arrow_upper_right:

