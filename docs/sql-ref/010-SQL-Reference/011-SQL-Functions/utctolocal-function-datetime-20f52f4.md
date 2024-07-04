<!-- loio20f52f4475191014a1089242486060c1 -->

# UTCTOLOCAL Function \(Datetime\)

Converts the specified timestamp between UTC and local time.



<a name="loio20f52f4475191014a1089242486060c1__sql_function_utctolocal_1sql_function_utctolocal_syntax"/>

## Syntax

```
UTCTOLOCAL (<time> [, <timezone> [, <timezone_dataset>]])
```



## Syntax Elements


<dl>
<dt><b>

*<time\>*

</b></dt>
<dd>

Specifies a timestamp in UTC to be converted to local time.

```
<time> ::= <timestamp>
```



</dd><dt><b>

*<timezone\>*

</b></dt>
<dd>

Specifies a string parameter holding the timezone defining the local time. If the local timezone is not explicitly specified, then the local timezone of the SAP HANA system is used.

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

-   `sap` searches in the dataset in the timezone definition tables. To use this value, import a timezone dataset \(see SAP Note 1791342\). If you use this value without importing a dataset, the function returns an error.
-   `platform` searches in the dataset provided by the operating system. This is the default value.



</dd>
</dl>



<a name="loio20f52f4475191014a1089242486060c1__sql_function_utctolocal_1sql_function_utctolocal_description"/>

## Description

Converts the UTC\(GMT\) time *<t\>* to the local time in a timezone.

Use UTC times instead of local timestamps. The use of local times or conversion between local time zones might require additional handling in the application code.



<a name="loio20f52f4475191014a1089242486060c1__sql_function_utctolocal_1sql_function_utctolocal_examples"/>

## Examples

The following example returns the value ***2011-12-31 20:00:00.000000000*** as the local time equivalent \(in EST\) of the specified UTC time:

```
SELECT UTCTOLOCAL (TO_TIMESTAMP('2012-01-01 01:00:00', 'YYYY-MM-DD HH24:MI:SS'), 'EST') "utctolocal" FROM DUMMY;
```

The following example returns the value ***2011-12-31 20:00:00.000000000*** as the local time equivalent \(in EST\) of the specified UTC time:

```
SELECT UTCTOLOCAL (TO_TIMESTAMP('2012-01-01 01:00:00', 'YYYY-MM-DD HH24:MI:SS'), 'EST', 'sap') "utctolocal" FROM DUMMY;
```

