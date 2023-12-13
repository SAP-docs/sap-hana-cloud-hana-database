<!-- loio20e3428a75191014a9949b4f90076dee -->

# LEFT Function \(String\)

Returns the specified number of characters or bytes of a string, starting from the left side.



<a name="loio20e3428a75191014a9949b4f90076dee__sql_function_left_1sql_function_left_syntax"/>

## Syntax

```
LEFT(<string>, <number>)
```



## Syntax Elements


<dl>
<dt><b>

*<string\>*

</b></dt>
<dd>

Specifies the string to be operated on.



</dd><dt><b>

*<number\>*

</b></dt>
<dd>

Specifies the length of characters or bytes to return, starting from the left side.



</dd>
</dl>



<a name="loio20e3428a75191014a9949b4f90076dee__sql_function_left_1sql_function_left_description"/>

## Description

Returns the first *<number\>* of characters or bytes from the beginning of *<string\>*.

Returns an empty string value if *<number\>* is less than 1.

Returns *<string\>* \(without blank padding\) if the value of *<number\>* is greater than the length of *<string\>*.



<a name="loio20e3428a75191014a9949b4f90076dee__sql_function_left_1sql_function_left_examples"/>

## Example

The following example returns the leftmost three characters of the string `Hel`:

```
SELECT LEFT ('Hello', 3) "left" FROM DUMMY;
```

The following example returns the string `Hello` because the value 10 exceeds the string length:

```
SELECT LEFT ('Hello', 10) "left" FROM DUMMY;
```

