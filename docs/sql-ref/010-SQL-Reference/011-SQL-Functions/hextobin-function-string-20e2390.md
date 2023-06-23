<!-- loio20e2390b75191014be86bf1562fcaf1b -->

# HEXTOBIN Function \(String\)

Converts a string of hexadecimal characters to a VARBINARY value.



<a name="loio20e2390b75191014be86bf1562fcaf1b__sql_function_hextobin_1sql_function_hextobin_syntax"/>

## Syntax

```
HEXTOBIN(<hexadecimal_string>)
```



<a name="loio20e2390b75191014be86bf1562fcaf1b__sql_function_hextobin_1sql_function_hextobin_description"/>

## Description

HEXTOBIN returns a VARBINARY value where each byte of the result corresponds to two characters of *<hexadecimal\_string\>*. If *<hexadecimal\_string\>* does not contain an even number of digits, an error is returned.

In SAP HANA, lowercase characters in *<hexadecimal\_string\>* are supported and are treated as uppercase.



<a name="loio20e2390b75191014be86bf1562fcaf1b__sql_function_hextobin_1sql_function_hextobin_examples"/>

## Example

The following two examples return the VARBINARY value ***608DA975***:

```
SELECT HEXTOBIN ('608da975') "Result" FROM DUMMY;
```

```
SELECT HEXTOBIN ('608DA975') "Result" FROM DUMMY;
```

**Related Information**  


[Character String Data Types](../character-string-data-types-a33f788.md "Character string data types are used to store values that contain character strings.")

