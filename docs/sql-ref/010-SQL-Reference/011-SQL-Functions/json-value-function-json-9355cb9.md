<!-- loio9355cb9e45a149c1a6ddb2bd2392d864 -->

# JSON\_VALUE Function \(JSON\)

Extracts an SQL value of a predefined type from a JSON value.



<a name="loio9355cb9e45a149c1a6ddb2bd2392d864__json_value_function_1sql_json_value_function_syntax"/>

## Syntax

```
JSON_VALUE(
 <JSON_API_common_syntax>
 [ <JSON_returning_clause> ]
 [ <JSON_value_empty_behavior> ON EMPTY ]
 [ <JSON_value_error_behavior> ON ERROR ]
 )
```



## Syntax Elements


<dl>
<dt><b>

*<JSON\_API\_common\_syntax\>*

</b></dt>
<dd>

Specifies a JSON context item and a path to the context item, using common syntax for the JSON API.

```
<JSON_API_common_syntax> ::= <JSON_context_item>, <JSON_path_specification>
```


<dl>
<dt><b>

*<JSON\_context\_item\>*

</b></dt>
<dd>

Specifies the JSON document to operate on, such as a table column, string, or collection.



</dd><dt><b>

*<JSON\_path\_specification\>*

</b></dt>
<dd>

Specifies the path to *<JSON\_context\_item\>*.

```
<JSON_path_specification> ::= <JSON_path_mode> <JSON_path_wff>

<JSON_path_mode> ::= STRICT | LAX
```

When *<JSON\_path\_mode\>* is set to STRICT, if the structural error occurs within a JSON filter expression, then the error handling of a JSON filter expression applies. Otherwise, a structural error is an unhandled error.

When the path is set to LAX, one of the following options occurs:

-   If an operation requires an SQL/JSON array but the operand is not an SQL/JSON array, then the operand is wrapped in an SQL/JSON array prior to performing the operation.
-   If an operation requires something other than an SQL/JSON array, but the operand is an SQL/JSON array, then the operand is unwrapped by converting its elements into an SQL/JSON sequence prior to performing the operation.

Array indexes start from 0, rather than 1 \(the SQL standard\).

If there is still a structural error after applying these resolutions, then the result is an empty SQL/JSON sequence.

*<JSON\_path\_wff\>* indicates an actual JSON path \(for example, `'$.item1'`\). *<JSON\_path\_specification\>* does not use double quotes.



</dd>
</dl>



</dd><dt><b>

*<JSON\_returning\_clause\>*

</b></dt>
<dd>

Defines the data type of the result.

```
<JSON_returning_clause> ::= RETURNING <data_type>

<data_type> ::= 
INTEGER 
 | BIGINT 
 | DECIMAL 
 | NVARCHAR(<integer>)
```



</dd><dt><b>

*<JSON\_value\_empty\_behavior\>* ON EMPTY

</b></dt>
<dd>

Specifies the behavior of the function when the related data is not in the context item. The default is NULL ON EMPTY

```
<JSON_value_empty_behavior> ON EMPTY

<JSON_value_empty_behavior> ::=
ERROR
 | NULL
 | DEFAULT <value_expression>
```

ERROR ON EMPTY returns an error if the related data is not in the context item. NULL ON EMPTY returns a NULL if the related data is not in the context item. DEFAULT *<value\_expression\>* ON EMPTY returns *<value\_expression\>* if the related data is not in the context item.



</dd><dt><b>

*<JSON\_value\_error\_behavior\>* ON ERROR

</b></dt>
<dd>

Specifies the behavior of the JSON\_VALUE function when an error occurs. The default is NULL ON ERROR.

```
<JSON_value_error_behavior> ON ERROR

<JSON_value_error_behavior> ::=
ERROR
 | NULL
 | DEFAULT <value_expression>
```

ERROR ON ERROR returns an error if the function results include an error. NULL ON ERROR returns a NULL if the function results include an error. DEFAULT *<value\_expression\>* ON ERROR returns *<value\_expression\>* if the function results include an error.



</dd>
</dl>



## Description

Extracts an SQL value of a predefined type from a JSON value.

The following tokens are supported in *<JSON\_API\_common\_syntax\>*:


<table>
<tr>
<th valign="top">

Token



</th>
<th valign="top">

Description



</th>
<th valign="top">

Example



</th>
</tr>
<tr>
<td valign="top">

$



</td>
<td valign="top">

The context item \(the first argument of the function\).



</td>
<td valign="top">

 `'$'` 



</td>
</tr>
<tr>
<td valign="top">

.



</td>
<td valign="top">

The member of an object.



</td>
<td valign="top">

 `'$.item.description'` 



</td>
</tr>
<tr>
<td valign="top">

\[



</td>
<td valign="top">

The array index specifier \(open\).



</td>
<td valign="top">



</td>
</tr>
<tr>
<td valign="top">

\]



</td>
<td valign="top">

Array index specifier \(closed\).



</td>
<td valign="top">

`'$[1]'`

`'$.item.list[1]'`



</td>
</tr>
<tr>
<td valign="top">

to



</td>
<td valign="top">

The array index range.



</td>
<td valign="top">

`'$[3 to 5]'`

`= '$[3,4,5]'`



</td>
</tr>
<tr>
<td valign="top">

\*



</td>
<td valign="top">

The wild card.



</td>
<td valign="top">

`'$.*.description'`

`'$.item.list[*]'`



</td>
</tr>
</table>



<a name="loio9355cb9e45a149c1a6ddb2bd2392d864__json_value_function_1sql_json_value_function_examples"/>

## Example

The following statement returns a value of 10:

```
SELECT JSON_VALUE('{"item1":10}', '$.item1') AS "value" FROM DUMMY;
```

The following statement returns a value of 5:

```
SELECT JSON_VALUE('{"item1":{"sub1":10}, "item2":{"sub2":5}, "item3":{"sub3":7}}', '$.*.sub2') AS "value" FROM DUMMY;
```

The following statement returns a value of 0:

```
SELECT JSON_VALUE('[0, 1, 2, 3]', '$[0]') AS "value"  FROM DUMMY;
```

The following statement returns the value "No last name found":

```
SELECT JSON_VALUE('{"firstname":"John"}', '$.lastname' DEFAULT 'No last name found' ON EMPTY) AS "Last Name" FROM DUMMY;
```

The following statement causes a type conversion error to demonstrate the behavior for ERROR ON ERROR:

```
SELECT JSON_VALUE('{"item":"string"}', '$.item' RETURNING DECIMAL ERROR ON ERROR) AS "Item" FROM DUMMY;
```

The following statement demonstrates what happens when there is no value \(the object does not have the name "last name"\):

```
SELECT JSON_VALUE('{"firstname":"John"}', 'strict $.lastname' ERROR ON ERROR) AS "Last Name" FROM DUMMY;
```

**Related Information**  


[Expressions](../expressions-20a4389.md "An expression is a clause that can be evaluated to return values.")

