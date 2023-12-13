<!-- loio20e3b6b77519101485e6bd62f7018f75 -->

# LOCATE Function \(String\)

Returns the position of a substring within a string.



<a name="loio20e3b6b77519101485e6bd62f7018f75__sql_function_locate_1sql_function_locate_syntax"/>

## Syntax

```
LOCATE( <haystack>, <needle>, [<start_position>] , [ <occurrences> ] )
```



<a name="loio20e3b6b77519101485e6bd62f7018f75__sql_function_locate_1sql_function_locate_description"/>

## Description

The LOCATE function returns the position of a substring *<needle\>* within a string *<haystack\>*.

-   If *<needle\>* is not found within *<haystack\>*, or if *<occurrences\>* is set to less than 1, then 0 is returned.

-   If *<haystack\>*, *<needle\>*, or *<occurences\>* is \(explicitly\) NULL, then NULL is returned.

-   If *<occurrences\>* is not specified, then the first matched position is returned. A setting of 1 for *<occurrences\>* is the same as not specifying it, while a setting of *n* returns the *n*th match \(or 0 if there are no more matches found\).

-   If *<start\_position\>* is a positive integer, or 0, or not specified, then the matching direction proceeds from left to right.

-   If *<start\_position\>* is negative, then matching starts at the end of *<haystack\>* and proceeds in the reverse direction \(right to left\). For example:


    <table>
    <tr>
    <th valign="top">

    Statement
    
    </th>
    <th valign="top">

    Returns
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    `SELECT LOCATE('AAA', 'A', -1) FROM "DUMMY";`
    
    </td>
    <td valign="top">
    
    3 - the position of the last A
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `SELECT LOCATE('AAA', 'A', -2) FROM "DUMMY";`
    
    </td>
    <td valign="top">
    
    2 - the position of the second to last A
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `SELECT LOCATE('AAA', 'A', -3) FROM "DUMMY";`
    
    </td>
    <td valign="top">
    
    1 - the position of the third to last A
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `SELECT LOCATE('AAA', 'A', -4) FROM "DUMMY";`
    
    </td>
    <td valign="top">
    
    0 - not found
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `SELECT LOCATE('ABABAC', 'A', -2) FROM "DUMMY";`
    
    </td>
    <td valign="top">
    
    5 - the position of the first A starting from the second last position
    
    </td>
    </tr>
    </table>
    
-   If a match is found, then the match position returned is always a positive number, even when *<start\_position\>* is a negative number.




<a name="loio20e3b6b77519101485e6bd62f7018f75__sql_function_locate_1sql_function_locate_examples"/>

## Examples

The following example returns ***1*** because *<needle\>* is an empty string.

```
SELECT LOCATE ('length in char', '') "locate" FROM DUMMY;
```

The following example returns the starting position \(***1***\) of `length` in the string `length in char`:

```
SELECT LOCATE ('length in char', 'length') "locate" FROM DUMMY;
```

The following example returns ***0*** because the search pattern `zchar` cannot be found in the given string:

```
SELECT LOCATE ('length in char', 'zchar') "locate" FROM DUMMY;
```

**Related Information**  


[Character String Data Types](../character-string-data-types-a33f788.md "Character string data types are used to store values that contain character strings.")

