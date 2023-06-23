<!-- loio20e0f06c751910148d388dacfe4b0b58 -->

# CURRENT\_UTCTIMESTAMP Function \(Datetime\)

Returns the current UTC timestamp.



<a name="loio20e0f06c751910148d388dacfe4b0b58__sql_function_current_utctimestamp_1sql_function_current_utctimestamp_syntax"/>

## Syntax

```
CURRENT_UTCTIMESTAMP[(<precision>)]
```



<a name="loio20e0f06c751910148d388dacfe4b0b58__section_glg_wwh_rpb"/>

## Syntax Elements


<dl>
<dt><b>

*<precision\>*

</b></dt>
<dd>

Specifies the precision of the sub-seconds displayed. *<precision\>* is an integer datatype with a valid range of 0-7. If not specified, the default precision is three.



</dd>
</dl>



<a name="loio20e0f06c751910148d388dacfe4b0b58__sql_function_current_utctimestamp_1sql_function_current_utctimestamp_description"/>

## Description

Returns the current UTC timestamp.



<a name="loio20e0f06c751910148d388dacfe4b0b58__sql_function_current_utctimestamp_1sql_function_current_utctimestamp_examples"/>

## Example

The following example returns the UTC timestamp of the system with zero, three, and seven precision values:

```
SELECT 
   CURRENT_UTCTIMESTAMP
   CURRENT_UTCTIMESTAMP(0) 
   CURRENT_UTCTIMESTAMP(3) 
   CURRENT_UTCTIMESTAMP(7) 
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

[CURRENT\_TIMESTAMP Function \(Datetime\)](current-timestamp-function-datetime-20de551.md "Returns the current local system timestamp information.")

