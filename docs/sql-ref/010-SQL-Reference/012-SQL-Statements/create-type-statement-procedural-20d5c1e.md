<!-- loio20d5c1ed75191014a80d897035629def -->

# CREATE TYPE Statement \(Procedural\)

Creates a user-defined type



<a name="loio20d5c1ed75191014a80d897035629def__sql_create_type_1sql_create_type_syntax"/>

## Syntax

```
CREATE TYPE <type_name>
   AS TABLE (<column_definition>[{,<column_definition>}...]) [ SQLSCRIPT SEARCH KEY( <column_name> [,…] ) ]
```



<a name="loio20d5c1ed75191014a80d897035629def__sql_create_type_1sql_create_type_syntax_elements"/>

## Syntax Elements


<dl>
<dt><b>

*<type\_name\>*

</b></dt>
<dd>

Identifies the table type to be created and, optionally, in which schema the creation should take place.

```
<type_name> ::= [<schema_name>.]<identifier>

<schema_name> ::= <unicode_name>
```



</dd><dt><b>

*<column\_definition\>*

</b></dt>
<dd>

Defines a table column.

```
<column_definition> ::= <column_name> <data_type> 
```


<dl>
<dt><b>

*<column\_name\>*

</b></dt>
<dd>

Specifies the table column name.

```
<column_name> ::= <identifier>
```



</dd><dt><b>

*<data\_type\>*

</b></dt>
<dd>

Specifies the data type for the column.

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
 | DECIMAL
 | REAL
 | DOUBLE
 | NVARCHAR
 | VARBINARY
 | BLOB
 | NCLOB


```



</dd>
</dl>



</dd><dt><b>

SQLSCRIPT SEARCH KEY clause

</b></dt>
<dd>

Specifies sorting instructions for the table. For use with SQLScript procedures. See the *SAP HANA Cloud, SAP HANA Database SQLScript Reference* for more information.



</dd>
</dl>



<a name="loio20d5c1ed75191014a80d897035629def__sql_create_type_1sql_create_type_description"/>

## Description

Use a user-defined type in the CREATE PROCEDURE and CREATE FUNCTION commands.

The syntax for defining table types follows the SQL syntax for defining new types. The table type is specified using a list of attribute names and primitive data types. For each table type, attributes must have unique names.



<a name="loio20d5c1ed75191014a80d897035629def__sql_create_type_1sql_create_type_examples"/>

## Example

Create a table type called tt\_publishers.

```
CREATE TYPE tt_publishers AS TABLE (
   publisher INTEGER,
   name NVARCHAR(50),
   price DECIMAL,
   cnt INTEGER);
```

**Related Information**  


[Sorted Table Variables](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2024_3_QRC/en-US/9f10ff55cedf4298b3fd7aebe6776a51.html "") :arrow_upper_right:

[CREATE PROCEDURE Statement \(Procedural\)](create-procedure-statement-procedural-20d4674.md "Creates a procedure that uses the specified programming language.")

[Data Types](../data-types-20a1569.md "A data type defines the characteristics of a data value. A special value of NULL is included in every data type to indicate the absence of a value.")

[CREATE FUNCTION Statement \(Procedural\)](create-function-statement-procedural-20d42e7.md "Creates a user-defined function.")

