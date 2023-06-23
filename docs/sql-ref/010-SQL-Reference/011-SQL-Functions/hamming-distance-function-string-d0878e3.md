<!-- loiod0878e31868b4f0392c71a299125148d -->

# HAMMING\_DISTANCE Function \(String\)

Performs a bitwise or bytewise comparison between two arguments and returns the hamming distance.



## Syntax

```
HAMMING_DISTANCE(<left_hand_side>, <right_hand_side>)
```



## Syntax Elements


<dl>
<dt><b>

*<left\_hand\_side\>*

</b></dt>
<dd>

Specifies a left hand side argument against which *<right\_hand\_side\>* is compared.

```
<lhs> ::= <string>
```



</dd><dt><b>

*<right\_hand\_side\>*

</b></dt>
<dd>

Specifies a right hand side argument to compare against *<left\_hand\_side\>*

```
<rhs> ::= <string>
```



</dd>
</dl>



## Description

Hamming distance describes differences between two specified arguments, and reflects the number of corresponding positions that differ from each other across the two arguments. Integer and binary arguments are compared bitwise, whereas string arguments are compared byte-wise.

The HAMMING\_DISTANCE function returns -1 if the length of the two arguments is different, and NULL if either of the arguments is NULL.



## Examples

The following example returns ***\-1*** because the arguments are of different length:

```
SELECT HAMMING_DISTANCE('abc', 'ca') "hamming_distance" FROM DUMMY;
```

The following example returns ***0*** because the arguments are identical:

```
SELECT HAMMING_DISTANCE('abc', 'abc') "hamming_distance" FROM DUMMY;
```

The following example returns ***0*** because the arguments are identical:

```
SELECT HAMMING_DISTANCE(4, 4) "hamming_distance" FROM DUMMY;
```

The following example returns ***3*** because all positions in the two arguments are different from the other string:

```
SELECT HAMMING_DISTANCE('abc', 'cab') "hamming_distance" FROM DUMMY;
```

The following example returns ***4*** to reflect the bitwise comparison of the arguments:

```
SELECT HAMMING_DISTANCE(TO_BINARY('abc'), TO_BINARY('cab')) "hamming_distance" FROM DUMMY;
```

The following example returns ***3*** to reflect the bitwise comparison of the arguments:

```
SELECT HAMMING_DISTANCE(4, 9) "hamming_distance" FROM DUMMY;
```

The following example returns ***\-1*** because the binary arguments are of different length:

```
SELECT HAMMING_DISTANCE(to_binary('abc'), to_binary('ca')) "hamming_distance" FROM DUMMY;
```

**Related Information**  


[Character String Data Types](../character-string-data-types-a33f788.md "Character string data types are used to store values that contain character strings.")

