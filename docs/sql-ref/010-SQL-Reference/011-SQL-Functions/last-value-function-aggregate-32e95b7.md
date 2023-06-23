<!-- loio32e95b7fac5c4b489d938c11ce5b4695 -->

# LAST\_VALUE Function \(Aggregate\)

Returns the value of the last element of an expression. This function can also be used as a window function.



## Syntax

**Aggregate function:**

```
LAST_VALUE( <expression> <order_by_clause> )
```

**Window function:**

```
LAST_VALUE( <expression> <order_by_clause> ) <window_specification>
```



<a name="loio32e95b7fac5c4b489d938c11ce5b4695__section_whf_lbl_w2b"/>

## Syntax Elements


<dl>
<dt><b>

*<expression\>*

</b></dt>
<dd>

Specifies the expression of data to operate over.



</dd><dt><b>

*<order\_by\_clause\>*

</b></dt>
<dd>

Specifies the sort order of the input rows.

```
<order_by_clause> ::= ORDER BY <order_by_expression> [, <order_by_expression> [,...] ]

<order_by_expression> ::= 
 <column_name> [ <collate_clause> ] [ ASC | DESC ] [ NULLS FIRST | NULLS LAST ] 
 | <column_position> [ <collate_clause> ] [ ASC | DESC ] [ NULLS FIRST | NULLS LAST ] 

<collate_clause> ::= COLLATE <collation_name>
```

*<collate\_clause\>* specifies the collation to use for ordering values in the results. *<collate\_clause\>* can only be used on columns defined as NVARCHAR \(or VARCHAR, which is a synonym for NVARCHAR\).*<collation\_name\>* is one of the supported collation names listed in the COLLATIONS system view.



</dd><dt><b>

*<window\_specification\>*

</b></dt>
<dd>

Defines a window on the data over which the function operates. For *<window\_specification\>*, see [Window Functions and the Window Specification](window-functions-and-the-window-specification-20a3533.md).



</dd>
</dl>



## Description

Returns the value of the last element in *<expression\>* as ordered by *<order\_by\_clause\>*.

NULL is returned if the value is NULL or if *<expression\>* is empty.

The output of the LAST\_VALUE function can be non-deterministic among tie values.



## Example

The example below returns the last value in COL1 column when the table is ordered by COL2. The query returns ***4***.

```
CREATE ROW TABLE T (COL1 DOUBLE, COL2 DOUBLE);

INSERT INTO T VALUES(1, 1);
INSERT INTO T VALUES(4, 5);
INSERT INTO T VALUES(7, 3);

SELECT LAST_VALUE (COL1 ORDER BY COL2) FROM T;
```



<a name="loio32e95b7fac5c4b489d938c11ce5b4695__section_exq_cfs_qxb"/>

## Example for Spatial Data Type \(ST\_Geometry, ST\_Point\)

The example below returns the last value, ***POINT \(4 4\)***, in binary format, when the table is ordered by ID:

```
CREATE TABLE TAB (ID INT, SHAPE ST_Geometry(4326));

INSERT INTO TAB VALUES(1, ST_GeomFromText('POINT(1 1)', 4326));
INSERT INTO TAB VALUES(2, ST_GeomFromText('POINT(2 2)', 4326));
INSERT INTO TAB VALUES(3, ST_GeomFromText('POINT(3 3)', 4326));
INSERT INTO TAB VALUES(4, ST_GeomFromText('POINT(4 4)', 4326));

SELECT LAST_VALUE(SHAPE ORDER BY ID) FROM TAB;
```

To return a result as data type NVARCHAR, use the following statement:

```
SELECT LAST_VALUE(CAST(SHAPE AS NVARCHAR) ORDER BY ID) FROM TAB;
```

**Related Information**  


[COLLATIONS System View](../../020-System-Views-Reference/021-System-Views/collations-system-view-57ff6fd.md "Provides the list of collations that can be specified in an ORDER BY clause.")

[Window Functions and the Window Specification](window-functions-and-the-window-specification-20a3533.md "Window functions allow you to perform analytic operations over a set of input rows.")

[Window Aggregate Functions](window-aggregate-functions-ee3c26a.md "Some aggregate functions can be used as window functions over a window specification.")

[Aggregate Functions](aggregate-functions-6fff7f0.md "Aggregate functions are analytic functions that calculate an aggregate value based on a group of rows.")

[SAP HANA Cloud, SAP HANA Database Spatial Reference](https://help.sap.com/viewer/bc9e455fe75541b8a248b4c09b086cf5/2023_2_QRC/en-US/e1c934157bd14021a3b43b5822b2cbe9.html "This guide is the entry point for SAP HANA Spatial capabilities.") :arrow_upper_right:

