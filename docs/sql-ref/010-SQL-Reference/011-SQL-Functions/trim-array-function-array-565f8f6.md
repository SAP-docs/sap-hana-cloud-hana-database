<!-- loio565f8f65e5324117b5435682150f45f3 -->

# TRIM\_ARRAY Function \(Array\)

Removes the specified number of elements from the end of an array.



## Syntax

```
TRIM_ARRAY(<array_value_expression>, <truncate_length>)
```



## Syntax Elements


<dl>
<dt><b>

*<array\_value\_expression\>*

</b></dt>
<dd>

Specifies the array that the function removes the elements from.



</dd><dt><b>

*<truncate\_length\>*

</b></dt>
<dd>

Specifies the number of elements to remove at the end of the array.



</dd>
</dl>



## Description

Returns an array that has a specified number of elements trimmed from the end.

If *<truncate\_length\>* is less than or equal to 0, then an exception is thrown.



## Example

The following example demonstrates the removal of three elements from an array. The query returns ***10***.

```
CREATE COLUMN TABLE ARRAY_TEST (IDX INT, VAL INT ARRAY);
INSERT INTO ARRAY_TEST VALUES (1, ARRAY(1, 2, 3));
INSERT INTO ARRAY_TEST VALUES (2, ARRAY(10, 20, 30, 40));

SELECT TRIM_ARRAY(VAL, 3) "trim_array" FROM ARRAY_TEST;
```

**Related Information**  


[Expressions](../expressions-20a4389.md "An expression is a clause that can be evaluated to return values.")

