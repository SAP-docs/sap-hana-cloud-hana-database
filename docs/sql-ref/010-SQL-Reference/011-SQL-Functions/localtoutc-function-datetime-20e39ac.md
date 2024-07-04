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
<timezone_dataset> ::= { sap | platform }
```

-   `sap` searches in the dataset in the timezone definition tables. To use this value, import a timezone dataset \(see SAP Note [1791342](https://me.sap.com/notes/1791342)\). If you use this value without importing a dataset, the function returns an error.
-   `platform` searches in the dataset provided by the operating system. This is the default value.



</dd>
</dl>



<a name="loio20e39ac67519101486b49c65d9aa5174__sql_function_localtoutc_1sql_function_localtoutc_description"/>

## Description

Converts the local time *<time\>* from a timezone to the UTC\(GMT\) time.

The usage of local timestamps is discouraged; use UTC times instead. The use of local times or conversion between local time zones might require additional handling in the application code.



<a name="loio20e39ac67519101486b49c65d9aa5174__sql_function_localtoutc_1sql_function_localtoutc_examples"/>

## Examples

The following example returns the value ***2012-01-01 06:00:00.000000000*** for the UTC date and time:

```
SELECT LOCALTOUTC (TO_TIMESTAMP('2012-01-01 01:00:00', 'YYYY-MM-DD HH24:MI:SS'), 'EST') "localtoutc" FROM DUMMY;
```

The following example returns the value ***2012-01-01 06:00:00.000000000*** for the UTC date and time:

```
SELECT LOCALTOUTC (TO_TIMESTAMP('2012-01-01 01:00:00', 'YYYY-MM-DD HH24:MI:SS'), 'EST', 'sap') "localtoutc" FROM DUMMY;
```

