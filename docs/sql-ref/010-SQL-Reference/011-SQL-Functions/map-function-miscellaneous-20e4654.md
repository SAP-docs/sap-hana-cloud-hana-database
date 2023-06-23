<!-- loio20e4654f75191014b58bdd5ea7423a15 -->

# MAP Function \(Miscellaneous\)

Searches for an expression within a set of values and returns a specified result.



<a name="loio20e4654f75191014b58bdd5ea7423a15__sql_function_map_1sql_function_map_syntax"/>

## Syntax

```
MAP(<expression>, <search_value>, <result> [, <search_value>, <result> [...] ] [, <default_result>])
```



## Syntax Elements


<dl>
<dt><b>

*<expression\>*

</b></dt>
<dd>

Specifies the expression to search for in any of the *<search\>* values.



</dd><dt><b>

*<search\_value\>*

</b></dt>
<dd>

Specifies a value to search for *<expression\>* in. You can specify more than one search value, and for each *<search\_value\>* value you can specify a corresponding *<result\>*.



</dd><dt><b>

*<result\>*

</b></dt>
<dd>

Specifies the result to return when *<expression\>* is found in the corresponding *<search\_value\>* value.



</dd><dt><b>

*<default\_result\>*

</b></dt>
<dd>

Specifies the default result to return when *<expression\>* is not found in any of the *<search\_value\>* values.



</dd>
</dl>



<a name="loio20e4654f75191014b58bdd5ea7423a15__sql_function_map_1sql_function_map_description"/>

## Description

Searches for *<expression\>* within a set of search values and returns the corresponding result.

-   If *<expression\>* is not found and *<default\_result\>* is defined, then MAP returns *<default\_result\>*.

-   If *<expression\>* is not found and *<default\_result\>* is not defined, then MAP returns NULL.


*<search\_value\>* and corresponding *<result\>* values must be specified as pairs.



<a name="loio20e4654f75191014b58bdd5ea7423a15__sql_function_map_1sql_function_map_examples"/>

## Example

The following query searches for 2, finds it in the third *<search\>*/*<result\>* pair \(`2, 'Two'`\), and returns the configured *<result\>* value ***Two***.

```
SELECT MAP(2, 0, 'Zero', 1, 'One', 2, 'Two', 3, 'Three', 'Default') "map" FROM DUMMY;
```

The following searches for 99 in the *<search\>* values, and, not finding it, returns the *<default\_result\>* value ***Default***.

```
SELECT MAP(99, 0, 'Zero', 1, 'One', 2, 'Two', 3, 'Three', 'Default') "map" FROM DUMMY;
```

The following searches for 99 in the *<search\>* values, and, not finding it, returns NULL because no *<default\_result\>* was specified.

```
SELECT MAP(99, 0, 'Zero', 1, 'One', 2, 'Two', 3, 'Three') "map" FROM DUMMY;
```

**Related Information**  


[Expressions](../expressions-20a4389.md "An expression is a clause that can be evaluated to return values.")

