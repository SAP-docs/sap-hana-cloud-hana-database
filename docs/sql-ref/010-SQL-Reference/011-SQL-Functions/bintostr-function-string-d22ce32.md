<!-- loiod22ce32dd295101481d58e6625b2112d -->

# BINTOSTR Function \(String\)

Converts a VARBINARY string to a character string.



<a name="loiod22ce32dd295101481d58e6625b2112d__sql_function_bintostr_1sql_function_bintostr_syntax"/>

## Syntax

```
BINTOSTR(<varbinary_string>)
```



## Syntax Elements


<dl>
<dt><b>

*<varbinary\_string\>*

</b></dt>
<dd>

The VARBINARY string to be converted to a character string.



</dd>
</dl>



<a name="loiod22ce32dd295101481d58e6625b2112d__sql_function_bintostr_1sql_function_bintostr_description"/>

## Description

Converts a VARBINARY string *<varbinary\_string\>* to a character string with CESU-8 encoding.



<a name="loiod22ce32dd295101481d58e6625b2112d__sql_function_bintostr_1sql_function_bintostr_examples"/>

## Example

This example converts the VARBINARY string `416E74` to a CESU-8 encoded character string, and returns the value ***Ant***:

```
SELECT BINTOSTR ('416E74') "bintostr" FROM DUMMY;
```

**Related Information**  


[Character String Data Types](../character-string-data-types-a33f788.md "Character string data types are used to store values that contain character strings.")

