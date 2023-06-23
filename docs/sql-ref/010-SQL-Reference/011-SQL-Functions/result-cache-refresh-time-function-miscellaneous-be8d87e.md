<!-- loiobe8d87e527aa499fbcbcd75357af73bf -->

# RESULT\_CACHE\_REFRESH\_TIME Function \(Miscellaneous\)

Returns the last cache refresh time of a result cache entry.



<a name="loiobe8d87e527aa499fbcbcd75357af73bf__sql_function_nullif_1sql_function_nullif_syntax"/>

## Syntax

```
RESULT_CACHE_REFRESH_TIME()
```



<a name="loiobe8d87e527aa499fbcbcd75357af73bf__sql_function_nullif_1sql_function_nullif_description"/>

## Description

If no result cache entry is provided, then NULL is returned.



<a name="loiobe8d87e527aa499fbcbcd75357af73bf__sql_function_nullif_1sql_function_nullif_examples"/>

## Example

The following fictitious example returns the last cache refresh time of the result cache entry V1, ***2015-11-20 01:01:01.010101***.

```
SELECT DISTINCT RESULT_CACHE_REFRESH_TIME() FROM V1;
```

