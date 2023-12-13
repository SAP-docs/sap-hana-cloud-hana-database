<!-- loio20dea8e57519101499438ff2eb028eff -->

# CURRENT\_UTCDATE Function \(Datetime\)

Returns the current UTC date.



<a name="loio20dea8e57519101499438ff2eb028eff__sql_function_current_utcdate_1sql_function_current_utcdate_syntax"/>

## Syntax

```
CURRENT_UTCDATE
```



<a name="loio20dea8e57519101499438ff2eb028eff__sql_function_current_utcdate_1sql_function_current_utcdate_description"/>

## Description

Returns the current UTC date.

In application code, it is recommended that you use UTC dates instead of local dates.



<a name="loio20dea8e57519101499438ff2eb028eff__sql_function_current_utcdate_1sql_function_current_utcdate_examples"/>

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

**Related Information**  


[Datetime Data Types](../datetime-data-types-3f81ccc.md "Datetime data types are used to store date and time information.")

