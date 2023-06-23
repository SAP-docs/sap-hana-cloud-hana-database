<!-- loio20dec53a751910149b5e8425a022f9cd -->

# CURRENT\_UTCTIME Function \(Datetime\)

Returns the current UTC time.



<a name="loio20dec53a751910149b5e8425a022f9cd__sql_function_current_utctime_1sql_function_current_utctime_syntax"/>

## Syntax

```
CURRENT_UTCTIME
```



<a name="loio20dec53a751910149b5e8425a022f9cd__sql_function_current_utctime_1sql_function_current_utctime_description"/>

## Description

Returns the current UTC time.



<a name="loio20dec53a751910149b5e8425a022f9cd__sql_function_current_utctime_1sql_function_current_utctime_examples"/>

## Example

The following example returns the local and UTC time of the system:

```
SELECT CURRENT_TIME "Current Time", CURRENT_UTCTIME "Coordinated Universal Time" FROM DUMMY;
```


<table>
<tr>
<th valign="top">

 



</th>
<th valign="top">

Current Time



</th>
<th valign="top">

Coordinated Universal Time



</th>
</tr>
<tr>
<td valign="top">

1



</td>
<td valign="top">

7:56:51 AM



</td>
<td valign="top">

2:56:51 PM



</td>
</tr>
</table>

**Related Information**  


[Datetime Data Types](../datetime-data-types-3f81ccc.md "Datetime data types are used to store date and time information.")

