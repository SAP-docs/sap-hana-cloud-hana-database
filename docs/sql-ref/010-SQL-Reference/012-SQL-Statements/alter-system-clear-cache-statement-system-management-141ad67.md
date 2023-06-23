<!-- loio141ad67a9cbe4c6c951b542aff239df4 -->

# ALTER SYSTEM CLEAR CACHE Statement \(System Management\)

Clears resources \(entries\) from one or more cache instances.



<a name="loio141ad67a9cbe4c6c951b542aff239df4__section_nsc_lgm_3bb"/>

## Syntax

```
ALTER SYSTEM CLEAR CACHE ( <cache_id> [, <cache_id> […] ] ) [ SYNC ]
```



<a name="loio141ad67a9cbe4c6c951b542aff239df4__section_osc_lgm_3bb"/>

## Syntax Elements


<dl>
<dt><b>

*<cache\_id\>*

</b></dt>
<dd>

Specifies the ID of the cache instance to clear, as found in the M\_CACHES system view.



</dd><dt><b>

SYNC

</b></dt>
<dd>

Increases the retry attempts for resources \(entries\) that were initially blocked from clearing. Specifying SYNC may make this statement take longer to return \(for example if many retries were required\) but performs a better clearing operation than without specifying SYNC.



</dd>
</dl>



<a name="loio141ad67a9cbe4c6c951b542aff239df4__section_psc_lgm_3bb"/>

## Description

Executing this statement clears the specified cache instances not only on the local \(index\) server, but across all distributed instances of the cache.

Entries \(resources\) in a cache instance may be blocked from clearing. This can happen while entries are being inserted or searched for, or when entries are being fetched for display in M\_CACHE\_ENTRIES. There may be other reasons why entries are blocked from clearing as well, so after a clearing operation \(even if SYNC is specified\), some entries may still remain in the cache instance.

When SYNC is not specified, the HANA server makes a best attempt effort at clearing as many cache entries as possible, and the statement always succeeds.

When SYNC is specified, the HANA server increases the number of retry attempts on resources that were initially busy. If there are distributed instances of the cache, then the command is successful only if each local clearing operation succeeds without exceeding the timeout for cache distributed requests \(ini parameter \[cache\] resultcache\_request\_timeout\_in\_milliseconds\). With SYNC, the statement may return a general error \(error number 2\) if the clear operation failed to clear some entries.

Regardless of whether SYNC is specified, the M\_CACHE\_ENTRIES system view may still return entries immediately after the ALTER SYSTEM CLEAR CACHE statement is run. This can happen if the clearing operation occurred concurrently with other database operations.

**Related Information**  


[M\_CACHE\_ENTRIES System View](../../020-System-Views-Reference/022-Monitoring-Views/m-cache-entries-system-view-20a907b.md "Provides cache entry information.")

