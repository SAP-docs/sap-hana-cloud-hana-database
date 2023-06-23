<!-- loio5e7c8dd968d74c009bef98028837d5a9 -->

# CONCAT\_NAZ Function \(String\)

Returns a combined, non-null value string consisting of two specified strings.



<a name="loio5e7c8dd968d74c009bef98028837d5a9__sql_function_concat_1sql_function_concat_syntax"/>

## Syntax

```
CONCAT_NAZ(<string1>, <string2>)
```



<a name="loio5e7c8dd968d74c009bef98028837d5a9__section_lfn_nfw_m1b"/>

## Syntax Elements


<dl>
<dt><b>

*<string1\>*

</b></dt>
<dd>

Specifies the first string to combine.



</dd><dt><b>

*<string2\>*

</b></dt>
<dd>

Specifies the second string to combine.



</dd>
</dl>



<a name="loio5e7c8dd968d74c009bef98028837d5a9__sql_function_concat_1sql_function_concat_description"/>

## Description

Returns a combined value string consisting of *<string1\>* followed by *<string2\>*. If one value is NULL, the other value is returned. If both values are NULL, NULL is returned.

The maximum length of the concatenated string is 8,388,607. If the string length is longer than the maximum length, then an exception is thrown. Exceptionally, an implicit truncation is performed when converting an NCLOB typed value with a size greater than the maximum length of an NVARCHAR typed value.



<a name="loio5e7c8dd968d74c009bef98028837d5a9__sql_function_concat_1sql_function_concat_examples"/>

## Example

The following example returns the AB:

```
SELECT CONCAT_NAZ ('A', 'B') "concat" FROM DUMMY;
```


<table>
<tr>
<th valign="top">

concat



</th>
</tr>
<tr>
<td valign="top">

AB



</td>
</tr>
</table>

The following example returns C:

```
SELECT CONCAT_NAZ ('C', null) "concat" FROM DUMMY;
```


<table>
<tr>
<th valign="top">

concat



</th>
</tr>
<tr>
<td valign="top">

C



</td>
</tr>
</table>

The following example returns the NULL value:

```
SELECT CONCAT_NAZ (null, null) "concat" FROM DUMMY;
```


<table>
<tr>
<th valign="top">

concat



</th>
</tr>
<tr>
<td valign="top">

NULL



</td>
</tr>
</table>

**Related Information**  


[Character String Data Types](../character-string-data-types-a33f788.md "Character string data types are used to store values that contain character strings.")

