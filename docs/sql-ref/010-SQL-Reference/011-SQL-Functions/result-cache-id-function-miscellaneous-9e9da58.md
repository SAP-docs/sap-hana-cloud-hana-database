<!-- loio9e9da58b772a4df4811e3d0845679d5d -->

# RESULT\_CACHE\_ID Function \(Miscellaneous\)

Returns the cache ID of a result cache entry.



<a name="loio9e9da58b772a4df4811e3d0845679d5d__sql_function_nullif_1sql_function_nullif_syntax"/>

## Syntax

```
RESULT_CACHE_ID()
```



<a name="loio9e9da58b772a4df4811e3d0845679d5d__sql_function_nullif_1sql_function_nullif_description"/>

## Description

If no result cache entry is specified, then NULL is returned.



<a name="loio9e9da58b772a4df4811e3d0845679d5d__sql_function_nullif_1sql_function_nullif_examples"/>

## Example

The following fictitious example returns the cache ID for result cache entry V1, ***40000001***.

```
SELECT DISTINCT RESULT_CACHE_ID () FROM V1 WITH HINT(RESULT_CACHE);
```

