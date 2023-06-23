<!-- loiofe7b7fede9aa4287ae69ffe3986e9c25 -->

# NEWUID Function \(Miscellaneous\)

Creates a unique identifier within an SAP HANA database.



<a name="loiofe7b7fede9aa4287ae69ffe3986e9c25__sql_function_newuid_1sql_function_newuid"/>

## Syntax

```
NEWUID()
```



<a name="loiofe7b7fede9aa4287ae69ffe3986e9c25__sql_function_newuid_1sql_function_newuid_description"/>

## Description

The NEWUID function acts as an alternative to the SYSUUID function. The SYSUUID function generates a universally unique identifier, whereas the NEWUID function generates a unique identifier within one SAP HANA database. Both functions return VARBINARY\(16\).



<a name="loiofe7b7fede9aa4287ae69ffe3986e9c25__sql_function_newuid_1sql_function_newuid_examples"/>

## Example

The following fictitious example returns a unique value, such as ***C15F6DB61C6A2B00F0000001EC2E2F00***:

```
SELECT NEWUID() FROM DUMMY;
```

