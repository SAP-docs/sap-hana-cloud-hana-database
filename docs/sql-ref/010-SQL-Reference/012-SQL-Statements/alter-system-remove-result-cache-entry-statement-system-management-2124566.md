<!-- loio2124566f72194618be0d40036c1dea52 -->

# ALTER SYSTEM REMOVE RESULT CACHE ENTRY Statement \(System Management\)

Removes the result cache entry for the specified cache ID.



## Syntax

```
ALTER SYSTEM REMOVE [<cache_type>] RESULT CACHE ENTRY <cache_id>;
```



## Syntax Elements


<dl>
<dt><b>

*<cache\_type\>*

</b></dt>
<dd>

Setting *<cache\_type\>* to DYNAMIC ensures that the cache is refreshed every time a query on the result cache is run. The default value is STATIC.

```
<cache_type> ::= STATIC | DYNAMIC
```



</dd><dt><b>

*<cache\_id\>*

</b></dt>
<dd>

Specifies the cache ID of the result cache entry according to the monitoring view. The M\_RESULT\_CACHE monitoring view provides cache IDs for static result caches and the M\_DYNAMIC\_RESULT\_CACHE monitoring view provides cache IDs for dynamic result caches.



</dd>
</dl>



## Description

The next suitable SELECT statement rebuilds the respective result cache entry.



Removes the specified static result cache entry from the M\_RESULT\_CACHE view.

```
ALTER SYSTEM REMOVE STATIC RESULT CACHE ENTRY <cache-ID>;
```

Removes the specified dynamic result cache entry from the M\_DYNAMIC\_RESULT\_CACHE view.

```
ALTER SYSTEM REMOVE DYNAMIC RESULT CACHE ENTRY <cache-ID>;
```

**Related Information**  


[ALTER SYSTEM REFRESH RESULT CACHE ENTRY Statement \(System Management\)](alter-system-refresh-result-cache-entry-statement-system-management-1ab0dbb.md "Refreshes the specified result cache entry.")

[M\_RESULT\_CACHE System View](../../020-System-Views-Reference/022-Monitoring-Views/m-result-cache-system-view-71e6d97.md "Provides result cache information.")

[M\_DYNAMIC\_RESULT\_CACHE System View](../../020-System-Views-Reference/022-Monitoring-Views/m-dynamic-result-cache-system-view-01f8a85.md "Lists statistics for the dynamic result cache.")

