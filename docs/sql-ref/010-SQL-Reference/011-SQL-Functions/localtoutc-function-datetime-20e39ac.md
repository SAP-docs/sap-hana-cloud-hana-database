<!-- loio20e39ac67519101486b49c65d9aa5174 -->

# LOCALTOUTC Function \(Datetime\)

A timestamp parameter holding the time to be converted between UTC and local time.



<a name="loio20e39ac67519101486b49c65d9aa5174__sql_function_localtoutc_1sql_function_localtoutc_syntax"/>

## Syntax

```
LOCALTOUTC (<time> [, <timezone> [, <timezone_dataset>]])
```



## Syntax Elements


<dl>
<dt><b>

*<time\>*

</b></dt>
<dd>

Specifies the time to be converted between UTC and local time.

```
<time> ::= <timestamp>
```



</dd><dt><b>

*<timezone\>*

</b></dt>
<dd>

Specifies the timezone defining the local time. For a list of available timezones, see the TIMEZONES system view. If the local timezone is not explicitly specified, then the local timezone of the SAP HANA system is used.

```
<timezone> ::= <string_literal>
```



</dd><dt><b>

*<timezone\_dataset\>*

</b></dt>
<dd>

Specifies the dataset in which to search for the given timezone. If specified, this must be set to `platform`, which searches in the dataset provided by the operating system.

```
<timezone_dataset> ::= platform
```



</dd>
</dl>



<a name="loio20e39ac67519101486b49c65d9aa5174__sql_function_localtoutc_1sql_function_localtoutc_description"/>

## Description

Converts the local time *<time\>* from a timezone to the UTC\(GMT\) time.

The usage of local timestamps is discouraged; use UTC times instead. The use of local times or conversion between local time zones might require additional handling in the application code.



<a name="loio20e39ac67519101486b49c65d9aa5174__sql_function_localtoutc_1sql_function_localtoutc_examples"/>

## Examples

The following example returns the value ***2012-01-01 06:00:00.0*** for the UTC date and time:

```
SELECT LOCALTOUTC (TO_TIMESTAMP('2012-01-01 01:00:00', 'YYYY-MM-DD HH24:MI:SS'), 'EST') "localtoutc" FROM DUMMY;
```

