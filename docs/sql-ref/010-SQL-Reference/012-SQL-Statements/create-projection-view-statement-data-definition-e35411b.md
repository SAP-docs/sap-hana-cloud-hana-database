<!-- loioe35411b417a94f199679b9f9f45c2306 -->

# CREATE PROJECTION VIEW Statement \(Data Definition\)

Creates a projection view. Projection views can be used as updatable views; insert, update, and delete triggers on projection views are supported.



<a name="loioe35411b417a94f199679b9f9f45c2306__sql_alter_fulltext_index_1sql_alter_fulltext_index_syntax"/>

## Syntax

```
CREATE [ OR REPLACE ] PROJECTION VIEW <projection_view_name> [ ( <view_column_name_list> ) ]
 AS SELECT <table_column_list>
 FROM [ <schema>.]<source_table_name>
 [ <with_association_clause> ]
 [ <with_annotations_clause> ]
 [ WITH DDL ONLY ]
 [ WITH READ ONLY ]
```



<a name="loioe35411b417a94f199679b9f9f45c2306__sql_alter_fulltext_index_1sql_alter_fulltext_index_syntax_elements"/>

## Syntax Elements


<dl>
<dt><b>

OR REPLACE

</b></dt>
<dd>

Replaces the projection view if it already exists; otherwise, if the view does not exist, then it is created.

A CREATE OR REPLACE operation does not change the ID of an existing projection view, and maintains any privileges associated with the view.



</dd><dt><b>

*<projection\_view\_name\>*

</b></dt>
<dd>

Specifies a name for the new projection view.



</dd><dt><b>

*<view\_column\_name\_list\>*

</b></dt>
<dd>

Specifies alternative names for the columns in the projection view if the names need to be different than those in *<table\_column\_list\>*.



</dd><dt><b>

*<table\_column\_list\>*

</b></dt>
<dd>

Specifies the columns in *<source\_table\_name\>* to include in the projection view. *<table\_column\_list\>* must include all primary key columns of the underlying source table.



</dd><dt><b>

*<source\_table\_name\>*

</b></dt>
<dd>

Specifies the source table for the projection view.



</dd><dt><b>

*<with\_association\_clause\>*

</b></dt>
<dd>

Creates a relationship between the view being created and one or more existing tables.

```
<with_association_clause> ::= 
 WITH ASSOCIATIONS (<association_def_list>)

<association_def_list> ::= <association_def>, ...
<association_def> ::= <forward_join_def> | <propagation_def>
<forward_join_def> ::= <join_cardinality_class>

[<join_cardinality_class>] ::= JOIN <table_or_view_identifier> [AS <table_alias>] ON <condition>
  | <propagation_def>

<join_cardinality> ::= 
 MANY TO ONE
 | MANY TO MANY
 | ONE TO ONE
 | ONE TO MANY

<propagation_def> ::= [<schema>.][<table>.]<association_identifier> [AS <alias>]
```



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

WITH DDL ONLY

</b></dt>
<dd>

Prevents users from querying the view and from modifying the underlying table.



</dd><dt><b>

WITH READ ONLY

</b></dt>
<dd>

This clause restricts the view to read-only access. It also enables the creation of projection views by overriding some standard limitations that normally disallow modifications on the view.

These limitations include requirements such as:

-   Each column in the view should map to a column of a single table.
-   If a column in the base table of the view has a NOT NULL constraint without a default value, then that column must be included in the view columns to enable insert operations.
-   The view cannot contain aggregate or analytic functions in the SELECT list. For example, the following functions are not allowed:
    -   TOP, SET, or DISTINCT operators in a SELECT list.
    -   A GROUP BY clause.

-   The view cannot contain a subquery in a SELECT list.
-   The view cannot contain a sequence value \(CURRVAL, NEXTVAL\).
-   The view cannot contain a column view as the base view.
-   The view cannot contain a calculated or a generated column.
-   The view cannot contain a partition restriction in a SELECT list.



</dd>
</dl>



<a name="loioe35411b417a94f199679b9f9f45c2306__sql_alter_fulltext_index_1sql_alter_fulltext_index_description"/>

## Description

You drop a projection view by using the normal DROP VIEW statement.



<a name="loioe35411b417a94f199679b9f9f45c2306__sql_alter_fulltext_index_1sql_alter_fulltext_index_examples"/>

## Examples

The following example creates a projection view on a table, SEARCH\_TEXT, and then inserts, modifies, and deletes data from the projection view:

```
CREATE ROW TABLE SEARCH_TEXT( Product NVARCHAR(200) PRIMARY KEY, Descrip NVARCHAR(200), Status NVARCHAR(200) );
INSERT INTO SEARCH_TEXT VALUES( 'Blue baseball cap', 'Vintage', 'Out of stock');
INSERT INTO SEARCH_TEXT VALUES( 'Red car', 'Vintage', 'Taking orders' );

CREATE PROJECTION VIEW myProjView (Item, Description, Status) AS SELECT * FROM SEARCH_TEXT;
INSERT INTO myProjView VALUES( 'Bluish sky', 'Retro', 'Discontinued' );
UPDATE myProjView SET Status = 'Discontinued' WHERE Item = 'Blue baseball cap';
DELETE FROM myProjView WHERE Item = 'Red car';

SELECT * FROM myProjView;
```


<table>
<tr>
<th valign="top">

ITEM

</th>
<th valign="top">

DESCRIPTION

</th>
<th valign="top">

STATUS

</th>
</tr>
<tr>
<td valign="top">

Bluish baseball cap

</td>
<td valign="top">

Vintage

</td>
<td valign="top">

Discontinued

</td>
</tr>
<tr>
<td valign="top">

Bluish sky

</td>
<td valign="top">

Retro

</td>
<td valign="top">

Discontinued

</td>
</tr>
</table>

The following example creates two tables and a projection view with associations to them:

```
CREATE ROW TABLE T1(A INT, B INT);
INSERT INTO T1 VALUES(1,1);

CREATE ROW TABLE T2(A INT, B INT);
INSERT INTO T2 VALUES(1,1);
INSERT INTO T2 VALUES(2,2);
				
CREATE PROJECTION VIEW V1 AS SELECT A, B FROM T1 WITH ASSOCIATIONS(JOIN T2 AS C ON C.A = A);
				
SELECT C.A, C.B FROM V1;
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

1

</td>
</tr>
</table>

The following example creates a table with annotations and then creates a projection view that also has annotations:

```
CREATE TABLE t1(c1 INT) WITH ANNOTATIONS(
    SET 't_k1' = 't_v1', 't_k2' = 't_v2'
    COLUMN c1 SET 'c_k1' = 'c_v1', 'c_k2' = 'c_v2');

CREATE PROJECTION VIEW v2 AS SELECT * FROM t1 WITH ANNOTATIONS(
    SET 'v_k1' = 'v_v1', 'v_k2' = 'v_v2'
    COLUMN c1 SET 'c_k1' = 'c_v1', 'c_k2' = 'c_v2');
```

The following statements show you how to use the WITH DDL ONLY clause to control whether users can query a view:

```
CREATE TABLE t1 (a int, b int);
CREATE PROJECTION VIEW v1 AS SELECT * FROM t1 WITH DDL ONLY;

SELECT * FROM v1; -- invalid view name: cannot select the view because it is in DDL-only mode
SELECT IS_DDL_ONLY from VIEWS where VIEW_NAME = 'V1'; -- returns TRUE

CREATE PROJECTION VIEW v2 AS SELECT * FROM v1; -- you can select from the view in a DDL statement.
```

**Related Information**  


[Projection Views (.hdbprojectionview and .hdbprojectionviewconfig)](https://help.sap.com/viewer/c2cc2e43458d4abda6788049c58143dc/2024_3_QRC/en-US/d8a3392c1287420ca82ac3090cd5049b.html "Transforms a design-time projection-view definition into a database object.") :arrow_upper_right:

[DROP VIEW Statement \(Data Definition\)](drop-view-statement-data-definition-20d9c05.md "Removes a view from the database.")

