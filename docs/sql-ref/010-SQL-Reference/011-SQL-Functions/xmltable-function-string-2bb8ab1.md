<!-- loio2bb8ab119e384b5f94635696bb9f68b5 -->

# XMLTABLE Function \(String\)

Creates a relational table from an XML string.



<a name="loio2bb8ab119e384b5f94635696bb9f68b5__sql_function_json_query_1sql_function_json_query_syntax"/>

## Syntax

```
XMLTABLE( [ <XML_namespace_clause>, ]
 <row_pattern> PASSING <XML_argument> COLUMNS <column_definitions>
 <error_option>
)
```



<a name="loio2bb8ab119e384b5f94635696bb9f68b5__section_ijt_p4y_rz"/>

## Syntax Elements


<dl>
<dt><b>

*<XML\_namespace\_clause\>*

</b></dt>
<dd>

Defines the XML namespace.

```
XMLNAMESPACE (<XML_namespace>[, ...]
 [DEFAULT <default_namespace>]
)
```


<dl>
<dt><b>

*<XML\_namespace\>*

</b></dt>
<dd>

Specifies the XML namespace.

```
<XML_namespace> ::= <namespace_url> AS <namespace_alias>
```

When the XMLNAMESPACE clause is specified, the result contains only the records that belong to the specified namespaces. If the namespace URL is specified \(DEFAULT *<namespace\_url\>*\), then all XPath strings should refer to the namespace URL.



</dd><dt><b>

*<default\_namespace\>*

</b></dt>
<dd>

Specifies the default namespace. *<default\_namespace\>*, *<namespace\_url\>*, and *<namespace\_alias\>* are string constants.



</dd>
</dl>



</dd><dt><b>

*<row\_pattern\>*

</b></dt>
<dd>

Describes the format of the xmlNodes in the XML with an XPath expression.

```
<row_pattern> ::= <str_const>
```



</dd><dt><b>

*<XML\_argument\>*

</b></dt>
<dd>

Specifies the XML to be converted to a table, defined as either as a string constant or a column reference.

```
<XML_argument> ::=
 <str_const>
 | <column_ref>
```


<dl>
<dt><b>

*<str\_const\>*

</b></dt>
<dd>

Specifies an XML string to be converted to a table.



</dd><dt><b>

*<column\_ref\>*

</b></dt>
<dd>

Specifies a column containing the XML to be converted to a table.



</dd>
</dl>



</dd><dt><b>

*<column\_definitions\>*

</b></dt>
<dd>

Defines the columns in the result table.

```
<column_definitions> ::=
 <column_name> <column_type> [, <column_name> <column_type>,...]
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

*<column\_type\>*

</b></dt>
<dd>

Specifies a data type for the column.

```
<column_type> ::=
 FOR ORDINALITY 
 | <regular_column_return_type> PATH <column_pattern> [DEFAULT <str_const>] 
 | <formatted_column_return_type> FORMAT XML PATH <column_pattern> [DEFAULT <str_const>]
```

If the column is an ordinality column, then the value for the I-th row is I. The return type of the ordinality column is BIGINT.

If the column is a regular column, then the value for the I-th row can be defined as follows:

-   If the result value is not empty, then the result comes from applying *<row\_pattern\>* or *<column\_pattern\>* to *<XML\_argument\>*.
-   If the result value is empty, then the result comes from the default value of *<column\_definition\>*.
-   If no default value is specified, then NULL is returned.
-   If FORMAT XML is specified, then the result contains the XML tags and XML structure instead of returning the value.



</dd><dt><b>

*<regular\_column\_return\_type\>*

</b></dt>
<dd>

Specifies the return type of the column.

```
<regular_column_return_type> ::= 
BIGINT
 | DAYDATE
 | DECIMAL
 | DOUBLE
 | INT
 | NVARCHAR (<int_const>)
 | SECONDDATE
 | SMALLDECIMAL 
 | TIME
 | TIMESTAMP
```



</dd><dt><b>

*<column\_pattern\>*

</b></dt>
<dd>

Specifies the xPath Expression to use to extract the value for a column.

```
<column_pattern> ::= <str_const>
```



</dd><dt><b>

*<formatted\_column\_return\_type\>*

</b></dt>
<dd>

Specifies the list of possible return types for the formatted column in the resulting table.

```
<formatted_column_return_type> ::= NVARCHAR (<int_const>)
```



</dd>
</dl>



</dd><dt><b>

*<error\_option\>*

</b></dt>
<dd>

Returns an exception when an error occurs during table creation.

```
<error_option> ::= ERROR ON ERROR
```

If ERROR ON ERROR is not set, then an empty result is returned. If ERROR ON ERROR is specified, then a runtime error is returned instead of a DEFAULT or an empty result.



</dd>
</dl>



<a name="loio2bb8ab119e384b5f94635696bb9f68b5__section_nwr_syy_rz"/>

## Description

Use the XMLTABLE function as a replacement for the FROM clause in a query to extract the data from an XML string. The XMLTABLE function returns the data as a relational table.

ERROR ON ERROR explicitly returns an error on a runtime error, since the default behavior is to return NULL in cases of a runtime error.

FORMAT XML extracts a result in XML format.

The resulting table has a row for each element in the XML string, which is the result of applying the *<row\_pattern\>* to the *<XML\_argument\>*. The rows of the resulting table have a column for each *<column\_definition\>*, with the *<column\_name\>* and *<return\_type\>* specified.

You cannot call the XMLTABLE function in the FROM clause of an UPDATE or DELETE statement.



<a name="loio2bb8ab119e384b5f94635696bb9f68b5__section_mlb_5yy_rz"/>

## Example

The following example returns the table below:

```
SELECT * FROM
XMLTABLE('/doc/item' PASSING
'<doc>
  <item><id>10</id><name>Box</name></item>
  <item><id>20</id><name>Jar</name></item>
</doc>'
COLUMNS 
ID INT PATH 'id', 
NAME NVARCHAR(20) PATH 'name'
) as XTABLE;

```


<table>
<tr>
<th valign="top">

ID



</th>
<th valign="top">

NAME



</th>
</tr>
<tr>
<td valign="top">

10



</td>
<td valign="top">

Box



</td>
</tr>
<tr>
<td valign="top">

20



</td>
<td valign="top">

Jar



</td>
</tr>
</table>

The following example returns the table below:

```
SELECT * FROM
XMLTABLE('/doc/item' PASSING
'<doc>
  <item><id>10</id><name>Box</name></item>
  <item><id>20</id><name>Jar</name></item>
</doc>'
COLUMNS 
RN FOR ORDINALITY,
NAME NVARCHAR(20) PATH 'name'
) as XTABLE;

```


<table>
<tr>
<th valign="top">

RN



</th>
<th valign="top">

NAME



</th>
</tr>
<tr>
<td valign="top">

1



</td>
<td valign="top">

Box



</td>
</tr>
<tr>
<td valign="top">

2



</td>
<td valign="top">

Jar



</td>
</tr>
</table>

The following example returns the table below:

```
SELECT * FROM
XMLTABLE('/doc/item' PASSING
'<doc>
  <item><id>10</id><name>Box</name></item>
  <item><id>20</id><name>Jar</name></item>
</doc>'
COLUMNS 
ID NVARCHAR(20) FORMAT XML PATH 'id', 
NAME NVARCHAR(20) FORMAT XML PATH 'name'
) AS XTABLE;

```


<table>
<tr>
<th valign="top">

ID



</th>
<th valign="top">

NAME



</th>
</tr>
<tr>
<td valign="top">

<id\>10</id\>



</td>
<td valign="top">

<name\>Box</name\>



</td>
</tr>
<tr>
<td valign="top">

<id\>20</id\>



</td>
<td valign="top">

<name\>Jar</name\>



</td>
</tr>
</table>

The following example returns the table below:

```
SELECT * FROM
XMLTABLE('/doc/item' PASSING
'<doc>
  <item><id subid="one">10</id><name>Box</name></item>
  <item><id subid="two">20</id><name>Jar</name></item>
</doc>'
COLUMNS 
ID NVARCHAR(20) PATH 'id/@subid', 
NAME NVARCHAR(20) PATH 'name'
) AS XTABLE;

```


<table>
<tr>
<th valign="top">

ID



</th>
<th valign="top">

NAME



</th>
</tr>
<tr>
<td valign="top">

one



</td>
<td valign="top">

Box



</td>
</tr>
<tr>
<td valign="top">

two



</td>
<td valign="top">

Jar



</td>
</tr>
</table>

The following example returns the table below:

```
SELECT * FROM
XMLTABLE(
XMLNAMESPACE('http://www.sap.com/xmltable' AS 'sap'),
'/sap:doc/sap:item' PASSING
'<sap:doc xmlns:sap="http://www.sap.com/xmltable">
  <sap:item><sap:id>1</sap:id><sap:name>Box</sap:name></sap:item>
  <sap:item><sap:id>2</sap:id><sap:name>Jar</sap:name></sap:item>
</sap:doc>'
COLUMNS 
ID INT PATH 'sap:id', 
NAME NVARCHAR(20) PATH 'sap:name'
) as XTABLE;

```


<table>
<tr>
<th valign="top">

ID



</th>
<th valign="top">

NAME



</th>
</tr>
<tr>
<td valign="top">

1



</td>
<td valign="top">

Box



</td>
</tr>
<tr>
<td valign="top">

2



</td>
<td valign="top">

Jar



</td>
</tr>
</table>

The following example returns the table below:

```
CREATE ROW TABLE XMLDATA (XML NVARCHAR(5000));
INSERT INTO XMLDATA VALUES (
'<sap:doc xmlns:sap="http://www.sap.com/xmltable">
  <sap:item><sap:id>1</sap:id><sap:name>Box</sap:name></sap:item>
  <sap:item><sap:id>2</sap:id><sap:name>Jar</sap:name></sap:item>
</sap:doc>');
INSERT INTO XMLDATA VALUES (
'<labs:doc xmlns:labs="http://www.saplabskorea.com/xmltable">
  <labs:item><labs:id>1</labs:id><labs:name>Apple</labs:name></labs:item>
  <labs:item><labs:id>2</labs:id><labs:name>Coconut</labs:name></labs:item>
</labs:doc>');

SELECT * FROM
XMLTABLE(XMLNAMESPACE('http://www.saplabskorea.com/xmltable' AS 'myns'),
'/myns:doc/myns:item' PASSING
XMLDATA.XML
COLUMNS 
ID INT PATH 'myns:id',
NAME NVARCHAR(20) PATH 'myns:name'
) AS XTABLE;

```


<table>
<tr>
<th valign="top">

ID



</th>
<th valign="top">

NAME



</th>
</tr>
<tr>
<td valign="top">

1



</td>
<td valign="top">

Apple



</td>
</tr>
<tr>
<td valign="top">

2



</td>
<td valign="top">

Coconut



</td>
</tr>
</table>

The following example returns the table below:

```
SELECT * FROM
XMLTABLE(XMLNAMESPACE('http://www.sap.com/xmltable' AS 'myns', 'http://www.namespace.com/name' as 'myns2'),
  '/myns:doc/myns:item' PASSING
  '<sap:doc xmlns:sap= "http://www.sap.com/xmltable" xmlns:ns2= "http://www.namespace.com/name">
 <sap:item><sap:id>1</sap:id><sap:name>Box</sap:name><ns2:count>3</ns2:count></sap:item>
 <sap:item><sap:id>2</sap:id><sap:name>Jar</sap:name><ns2:count>4</ns2:count></sap:item>
 </sap:doc>'
 COLUMNS 
  ID INT PATH 'myns:id', 
  NAME NVARCHAR(20) PATH 'myns:name',
  COUNT INT PATH 'myns2:count'
) AS XTABLE;

```


<table>
<tr>
<th valign="top">

ID



</th>
<th valign="top">

NAME



</th>
<th valign="top">

COUNT



</th>
</tr>
<tr>
<td valign="top">

1



</td>
<td valign="top">

Box



</td>
<td valign="top">

3



</td>
</tr>
<tr>
<td valign="top">

2



</td>
<td valign="top">

Jar



</td>
<td valign="top">

4



</td>
</tr>
</table>

The following example returns the table below:

```
SELECT * FROM
XMLTABLE(
XMLNAMESPACE('http://www.namespace.com/name' AS 'myns2' DEFAULT 'http://www.sap.com/xmltable'),
'/doc/item' PASSING
'<sap:doc xmlns:sap="http://www.sap.com/xmltable" xmlns:ns="http://www.namespace.com/name">
  <sap:item><sap:id>1</sap:id><ns:name>Box</ns:name></sap:item>
  <sap:item><sap:id>2</sap:id><ns:name>Jar</ns:name></sap:item>
</sap:doc>'
COLUMNS 
ID INT PATH 'id', 
NAME NVARCHAR(20) PATH 'myns2:name'
) AS XTABLE;

```


<table>
<tr>
<th valign="top">

ID



</th>
<th valign="top">

NAME



</th>
</tr>
<tr>
<td valign="top">

1



</td>
<td valign="top">

Box



</td>
</tr>
<tr>
<td valign="top">

2



</td>
<td valign="top">

Jar



</td>
</tr>
</table>

