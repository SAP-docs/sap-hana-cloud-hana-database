<!-- loio46c5fecd565c4623b03ad316e27aa22a -->

# ESCAPE\_DOUBLE\_QUOTES Function \(Security\)

Escapes double quotes in the specified string.



## Syntax

```
ESCAPE_DOUBLE_QUOTES(<value>)
```



## Description

Escapes double quotes in the *<value\>* string, ensuring that a valid SQL identifier is used in dynamic SQL statements to prevent SQL injections. The function returns the input string with escaped double quotes.



## Example

The following query escapes the double quotes and returns the value ***TAB""LE***.

```
SELECT ESCAPE_DOUBLE_QUOTES('TAB"LE') "table_name" FROM DUMMY;
```

