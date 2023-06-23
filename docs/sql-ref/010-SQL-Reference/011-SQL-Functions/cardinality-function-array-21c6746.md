<!-- loio21c6746955ce4cc2809801c5b0e93817 -->

# CARDINALITY Function \(Array\)

Returns the number of elements in a specified array.



## Syntax

```
CARDINALITY(<array_value_expression>)
```



## Syntax Elements


<dl>
<dt><b>

*<array\_value\_expression\>*

</b></dt>
<dd>

Specifies the array that the function returns the number of elements for.



</dd>
</dl>



## Description

Returns the number of elements in *<array\_value\_expression\>*.



## Example

The following example returns the number of elements \(3 and 4, respectively\) contained in two arrays.

```
CREATE COLUMN TABLE ARRAY_TEST (IDX INT, VAL INT ARRAY);
INSERT INTO ARRAY_TEST VALUES (1, ARRAY(1, 2, 3));
INSERT INTO ARRAY_TEST VALUES (2, ARRAY(10, 20, 30, 40));

SELECT CARDINALITY(VAL) "cardinality" FROM ARRAY_TEST;
```

**Related Information**  


[Expressions](../expressions-20a4389.md "An expression is a clause that can be evaluated to return values.")

