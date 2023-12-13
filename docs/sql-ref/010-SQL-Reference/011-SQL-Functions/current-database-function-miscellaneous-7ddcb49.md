<!-- loio7ddcb499036a483ab18ecb19816e6708 -->

# CURRENT\_DATABASE Function \(Miscellaneous\)

Returns a string containing the current tenant database name.



<a name="loio7ddcb499036a483ab18ecb19816e6708__sql_function_current_database_sql_function_current_database_syntax"/>

## Syntax

```
CURRENT_DATABASE()
```



<a name="loio7ddcb499036a483ab18ecb19816e6708__sql_function_current_database_sql_function_current_database_description"/>

## Description

Returns the current tenant database name in a SAP HANA environment.



<a name="loio7ddcb499036a483ab18ecb19816e6708__sql_function_current_database_sql_function_current_database_examples"/>

## Example

The following example demonstrates the basic operation of the function by returning the name of the current database:

```
SELECT CURRENT_DATABASE() "current database" FROM DUMMY;
```

Sample Output:


<table>
<tr>
<th valign="top">

current database

</th>
</tr>
<tr>
<td valign="top">

H01

</td>
</tr>
</table>

