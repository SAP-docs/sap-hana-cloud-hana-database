<!-- loioa7804953f5cb458a84f47d3045436107 -->

# ALTER SYSTEM CLEAR TIMEZONE CACHE Statement \(System Management\)

Clears cached timezone definitions.



## Syntax

```
ALTER SYSTEM CLEAR TIMEZONE CACHE DATASET <timezone_dataset_string_literal>
```



## Syntax Elements


<dl>
<dt><b>

*<timezone\_dataset\_string\_literal\>*

</b></dt>
<dd>

Specifies the data to be cleared.

```
<timezone_dataset_string_literal> ::= { sap | platform }
```


<dl>
<dt><b>

sap

</b></dt>
<dd>

Specifies to clear the currently-used SAP HANA dataset.



</dd><dt><b>

platform

</b></dt>
<dd>

Specifies to clear the dataset provided by the operating system.



</dd>
</dl>



</dd>
</dl>



## Description

For efficiency purposes, timezone definitions are cached in internal structures for timestamp conversions such as UTC to local date and time. Use ALTER SYSTEM CLEAR TIMEZONE CACHE DATASET to clear out the cached timezone definitions when they become stale, for example when a timezone definition changes.

After executing this statement, the timezone cache contents are recreated for the respective data sources at the next access.



## Permissions

You must have the SERVICE ADMIN system privilege to execute this statement.



<a name="loioa7804953f5cb458a84f47d3045436107__sql_alter_system_clear_sql_plan_cache_1sql_alter_system_clear_sql_plan_cache_examples"/>

## Example

Clears all cached timezone definitions in the currently used 'sap' dataset.

```
ALTER SYSTEM CLEAR TIMEZONE CACHE DATASET 'sap';
```

**Related Information**  


[TIMEZONES System View](../../020-System-Views-Reference/021-System-Views/timezones-system-view-adeba8e.md "Provides information about the timezones which are available together with their originating data set.")

