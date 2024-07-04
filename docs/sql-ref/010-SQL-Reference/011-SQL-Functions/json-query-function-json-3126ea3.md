<!-- loio3126ea33d50d42d19517a08fe22ec5a1 -->

# JSON\_QUERY Function \(JSON\)

Extracts JSON text from a JSON context item by using a SQL/JSON path expression.



<a name="loio3126ea33d50d42d19517a08fe22ec5a1__sql_function_json_query_1sql_function_json_query_syntax"/>

## Syntax

```
JSON_QUERY(
 <JSON_API_common_syntax>
 [ <JSON_output_clause> ]
 [ <JSON_query_wrapper_behavior> ]
 [ <JSON_query_empty_behavior> ON EMPTY ]
 [ <JSON_query_error_behavior> ON ERROR ]
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

If a structural error occurs within a JSON filter expression and *<JSON\_path\_mode\>* is set to STRICT, then the error handling of a JSON filter expression applies. Otherwise, a structural error is an unhandled error.

When the path is set to LAX, one of the following options occurs:

-   If an operation requires an SQL/JSON array but the operand is not an SQL/JSON array, then the operand is wrapped in an SQL/JSON array prior to performing the operation.
-   If an operation requires something other than an SQL/JSON array, but the operand is an SQL/JSON array, then the operand is unwrapped by converting its elements into an SQL/JSON sequence prior to performing the operation.

Array indexes start from 0, rather than 1 \(the SQL standard\).

If there is still a structural error after applying these resolutions, then the result is an empty SQL/JSON sequence.

*<JSON\_path\_wff\>* indicates an actual JSON path \(for example, `'$.item1'`\). *<JSON\_path\_specification\>* does not use double quotes.



</dd>
</dl>



</dd><dt><b>

*<JSON\_output\_clause\>*

</b></dt>
<dd>

Specifies the output created by the JSON\_QUERY function.

```
<JSON_output_clause> ::= RETURNING <data_type>
```


<dl>
<dt><b>

*<data\_type\>*

</b></dt>
<dd>

Specifies the data type to be set as the return type of the JSON QUERY function. Supported data types: NVARCHAR\(*<length\>*\).



</dd>
</dl>



</dd><dt><b>

*<JSON\_query\_wrapper\_behavior\>* WRAPPER

</b></dt>
<dd>

Specifies the wrapper behavior of the JSON query.

```
<JSON_query_wrapper_behavior> WRAPPER

<JSON_query_wrapper_behavior> ::=
WITHOUT [ ARRAY ]
 | WITH [ CONDITIONAL | UNCONDITIONAL ] [ ARRAY ]
```

The default is WITHOUT ARRAY WRAPPER. However, if WITH is specified, then the default is UNCONDITIONAL ARRAY WRAPPER.



</dd><dt><b>

*<JSON\_query\_empty\_behavior\>* ON EMPTY

</b></dt>
<dd>

Specifies the behavior of the function if the related data is not in the context item. The default is NULL ON EMPTY.

```
<JSON_query_empty_behavior> ON EMPTY

<JSON_query_empty_behavior> ::=
ERROR
 | NULL
 | EMPTY ARRAY
 | EMPTY OBJECT
```

ERROR ON EMPTY returns an error if the related data is not in the context item. NULL ON EMPTY returns a NULL if the related data is not in the context item. EMPTY ARRAY ON EMPTY returns an empty array if the related data is not in the context item. EMPTY OBJECT ON EMPTY returns an empty JSON object if the related data is not in the context item.



</dd><dt><b>

*<JSON\_query\_error\_behavior\>* ON ERROR

</b></dt>
<dd>

Specifies the behavior of the function when the query throws an error. The default is NULL ON ERROR.

```
<JSON_query_error_behavior> ON ERROR

<JSON_query_error_behavior> ::= 
ERROR
 | NULL
 | EMPTY ARRAY
 | EMPTY OBJECT
```

ERROR ON ERROR returns an error if the function result includes an error. NULL ON ERROR returns a NULL if the function result includes an error. EMPTY ARRAY ON ERROR returns an empty array if the function result includes an error. EMPTY OBJECT ON ERROR returns an empty JSON object if the function result includes an error.



</dd>
</dl>



## Description

Extracts JSON text from a JSON context item using a SQL/JSON path expression.

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

\[ \]

</td>
<td valign="top">

Bracket notation:

-   Name selector: `"<string>"` or `'<string>'`
-   Index selector: `<array-index> (, <array-index>)` 
-   Array slice selector: `<start-index>:<end-index>` \(the element of the end index is not included in selection\)
-   "to"-selector: `<start-index>` to `<end-index>` \(the element of the end index is included in selection\)
-   Wildcard selector: \*



</td>
<td valign="top">

`'$[1]'`

`'$.item.list[1]'`

`'$["item"]'`

`'$[1:3]' = '$[1,2]'`

`'$[1 to 3] = '$[1,2,3]'`

`'$[1:-1]'`

`'$.item[*]'`

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



<a name="loio3126ea33d50d42d19517a08fe22ec5a1__json_query_function_1sql_json_query_function_examples"/>

## Example

The following query returns the value ***\{"item1":1,"item2":2,"item3":3\}***.

```
SELECT JSON_QUERY('{"item1":1, "item2":2, "item3":3}', '$') AS JSONQUERY FROM DUMMY;
```

The following query returns the value ***\[1\]***.

```
SELECT JSON_QUERY('{"item1":1, "item2":2, "item3":3}', '$.item1' WITH WRAPPER ) AS JSONQUERY FROM DUMMY;
```

**Related Information**  


[Expressions](../expressions-20a4389.md "An expression is a clause that can be evaluated to return values.")

