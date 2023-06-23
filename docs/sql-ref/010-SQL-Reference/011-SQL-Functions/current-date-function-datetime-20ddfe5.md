<!-- loio20ddfe5d75191014af50837e2818462d -->

# CURRENT\_DATE Function \(Datetime\)

Returns the current local system date.



<a name="loio20ddfe5d75191014af50837e2818462d__sql_function_current_date_1sql_function_current_date_syntax"/>

## Syntax

```
CURRENT_DATE
```



<a name="loio20ddfe5d75191014af50837e2818462d__sql_function_current_date_1sql_function_current_date_description"/>

## Description

Returns the current local system date.

It is recommended that you use UTC dates instead of local dates. See to the CURRENT\_UTCDATE function for more information.



<a name="loio20ddfe5d75191014af50837e2818462d__sql_function_current_date_1sql_function_current_date_examples"/>

## Example

The following example returns the local and UTC date of the local system:

```
SELECT CURRENT_DATE "Current Date", CURRENT_UTCDATE "Coordinated Universal Date" FROM DUMMY;
```


<table>
<tr>
<th valign="top">

 



</th>
<th valign="top">

Current Date



</th>
<th valign="top">

Coordinated Universal Date



</th>
</tr>
<tr>
<td valign="top">

1



</td>
<td valign="top">

May 1, 2019



</td>
<td valign="top">

May 1, 2019



</td>
</tr>
</table>

```
SELECT CURRENT_DATE "Current Date", CURRENT_UTCDATE "Coordinated Universal Date" FROM DUMMY;
```


<table>
<tr>
<th valign="top">

 



</th>
<th valign="top">

Current Date



</th>
<th valign="top">

Coordinated Universal Date



</th>
</tr>
<tr>
<td valign="top">

1



</td>
<td valign="top">

May 1, 2019



</td>
<td valign="top">

May 1, 2019



</td>
</tr>
</table>

**Related Information**  


[Datetime Data Types](../datetime-data-types-3f81ccc.md "Datetime data types are used to store date and time information.")

[CURRENT\_UTCDATE Function \(Datetime\)](current-utcdate-function-datetime-20dea8e.md "Returns the current UTC date.")

