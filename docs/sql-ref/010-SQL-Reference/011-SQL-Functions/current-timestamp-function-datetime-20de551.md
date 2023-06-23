<!-- loio20de551c751910149bcfc30eaf359b03 -->

# CURRENT\_TIMESTAMP Function \(Datetime\)

Returns the current local system timestamp information.



<a name="loio20de551c751910149bcfc30eaf359b03__sql_function_current_timestamp_1sql_function_current_timestamp_syntax"/>

## Syntax

```
CURRENT_TIMESTAMP[(<precision>)]
```



<a name="loio20de551c751910149bcfc30eaf359b03__section_glg_wwh_rpb"/>

## Syntax Elements


<dl>
<dt><b>

*<precision\>*

</b></dt>
<dd>

Specifies the precision of the sub-seconds displayed. *<precision\>* is an integer datatype with a valid range of 0-7. If not specified, the default precision is three.



</dd>
</dl>



<a name="loio20de551c751910149bcfc30eaf359b03__sql_function_current_timestamp_1sql_function_current_timestamp_description"/>

## Description

Returns the current local system timestamp information.

It is recommended that you use UTC timestamps instead of local timestamps. See CURRENT\_UTCTIMESTAMP function for more information.



<a name="loio20de551c751910149bcfc30eaf359b03__sql_function_current_timestamp_1sql_function_current_timestamp_examples"/>

## Example

The following example returns the local timestamp of the system with zero, three, and seven precision values:

```
SELECT 
   CURRENT_TIMESTAMP,
   CURRENT_TIMESTAMP(0),
   CURRENT_TIMESTAMP(3),
   CURRENT_TIMESTAMP(7),
FROM DUMMY;
```

```
   '2021-03-09 09:07:36.8110000',
   '2021-03-09 09:07:36.0000000', 
   '2021-03-09 09:07:36.8110000', 
   '2021-03-09 09:07:36.8118739'

```

**Related Information**  


[Datetime Data Types](../datetime-data-types-3f81ccc.md "Datetime data types are used to store date and time information.")

[CURRENT\_UTCTIMESTAMP Function \(Datetime\)](current-utctimestamp-function-datetime-20e0f06.md "Returns the current UTC timestamp.")

