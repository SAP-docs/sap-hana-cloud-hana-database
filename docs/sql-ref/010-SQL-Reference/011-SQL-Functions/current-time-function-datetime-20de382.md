<!-- loio20de382f7519101482ca9a2865a86014 -->

# CURRENT\_TIME Function \(Datetime\)

Returns the local system time.



<a name="loio20de382f7519101482ca9a2865a86014__sql_function_current_time_1sql_function_current_time_syntax"/>

## Syntax

```
CURRENT_TIME
```



<a name="loio20de382f7519101482ca9a2865a86014__sql_function_current_time_1sql_function_current_time_description"/>

## Description

Returns the current local system time.

It is recommended that you use UTC times instead of local times. See to the CURRENT\_UTCTIME function for more information.



<a name="loio20de382f7519101482ca9a2865a86014__sql_function_current_time_1sql_function_current_time_examples"/>

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

[CURRENT\_UTCTIME Function \(Datetime\)](current-utctime-function-datetime-20dec53.md "Returns the current UTC time.")

