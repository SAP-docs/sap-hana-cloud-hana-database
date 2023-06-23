<!-- loio1ab0dbbae3734a48b7a286f3df467b6b -->

# ALTER SYSTEM REFRESH RESULT CACHE ENTRY Statement \(System Management\)

Refreshes the specified result cache entry.



## Syntax

```
ALTER SYSTEM REFRESH [<cache_type>] RESULT CACHE ENTRY <cache_id>;
```



## Syntax Elements


<dl>
<dt><b>

*<cache\_type\>*

</b></dt>
<dd>

Specifies the cache type. The default value is STATIC.

```
<cache_type> ::= STATIC
```



</dd><dt><b>

*<cache\_id\>*

</b></dt>
<dd>

Specifies the cache ID of the result cache entry according to the monitoring view. The M\_RESULT\_CACHE monitoring view provides cache IDs for static result caches.



</dd>
</dl>



## Description

Refreshes the result cache entry specified by the *<cache\_id\>*. No subsequent SELECT statement is required.



<a name="loio1ab0dbbae3734a48b7a286f3df467b6b__section_rxh_1db_chb"/>

## Examples

Refresh the specified static result cache entry from the M\_RESULT\_CACHE view.

```
ALTER SYSTEM REFRESH STATIC RESULT CACHE ENTRY <cache-ID>;
```

**Related Information**  


[M\_RESULT\_CACHE System View](../../020-System-Views-Reference/022-Monitoring-Views/m-result-cache-system-view-71e6d97.md "Provides result cache information.")

