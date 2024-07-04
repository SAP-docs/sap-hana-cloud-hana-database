<!-- loio6522df94eee542d5b1700a7766e6e6a2 -->

# NTH\_VALUE Function \(Aggregate\)

Returns the value of an element at a specific position in an expression. This function can also be used as a window function.



## Syntax

**Aggregate function:**

```
NTH_VALUE( <expression>, <position> <order_by_clause> )
```

**Window function:**

```
NTH_VALUE( <expression>, <position> <order_by_clause> ) <window_specification>
```



## Syntax Elements


<dl>
<dt><b>

*<expression\>*

</b></dt>
<dd>

Specifies the expression where the position of the element occurs.



</dd><dt><b>

*<position\>*

</b></dt>
<dd>

Specifies the position of the element in *<expression\>*.



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

Returns the value of the element at position specified by *<position\>* in *<expression\>* as ordered by *<order\_by\_clause\>*.

Null is returned if the value is NULL or if the value of *<position\>* is greater than the number of elements in *<expression\>*.

An error is raised if *<position\>* is less than or equal to 0.

The output of NTH\_VALUE function can be non-deterministic among tied values.



## Example

The example below returns the second value in column `COL1`: ***700***, when the table is ordered by `COL2`.

```
CREATE ROW TABLE T (COL1 DOUBLE, COL2 DOUBLE);
INSERT INTO T VALUES(900, 10);
INSERT INTO T VALUES(400, 50);
INSERT INTO T VALUES(700, 30);
INSERT INTO T VALUES(200, 40);

SELECT NTH_VALUE (COL1, 2 ORDER BY COL2) FROM T;
```



<a name="loio6522df94eee542d5b1700a7766e6e6a2__section_exq_cfs_qxb"/>

## Example for Spatial Data Type \(ST\_Geometry, ST\_Point\)

The example below returns the nth value, ***POINT \(3 3\)***, in binary format, when the table is ordered by ID:

```
CREATE TABLE TAB (ID INT, SHAPE ST_Geometry(4326));

INSERT INTO TAB VALUES(1, ST_GeomFromText('POINT(1 1)', 4326));
INSERT INTO TAB VALUES(2, ST_GeomFromText('POINT(2 2)', 4326));
INSERT INTO TAB VALUES(3, ST_GeomFromText('POINT(3 3)', 4326));
INSERT INTO TAB VALUES(4, ST_GeomFromText('POINT(4 4)', 4326));

SELECT NTH_VALUE(SHAPE, 3 ORDER BY ID) FROM TAB;
```

To return a result as data type NVARCHAR, use the following statement:

```
SELECT NTH_VALUE(CAST(SHAPE AS NVARCHAR), 3 ORDER BY ID) FROM TAB;
```

**Related Information**  


[COLLATIONS System View](../../020-System-Views-Reference/021-System-Views/collations-system-view-57ff6fd.md "Provides the list of collations that can be specified in an ORDER BY clause.")

[Window Functions and the Window Specification](window-functions-and-the-window-specification-20a3533.md "Window functions allow you to perform analytic operations over a set of input rows.")

[Window Aggregate Functions](window-aggregate-functions-ee3c26a.md "Some aggregate functions can be used as window functions over a window specification.")

[SAP HANA Cloud, SAP HANA Database Spatial Reference](https://help.sap.com/viewer/bc9e455fe75541b8a248b4c09b086cf5/2024_3_QRC/en-US/e1c934157bd14021a3b43b5822b2cbe9.html "This guide is the entry point for SAP HANA Spatial capabilities.") :arrow_upper_right:

