<!-- loio97dca93d321540faa947abe647ebdf6b -->

# ALTER SYSTEM CLEAR RESULT CACHE Statement \(System Management\)

Removes all result cache entries from the system.



## Syntax

```
ALTER SYSTEM CLEAR [<cache_type>] RESULT CACHE
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



</dd>
</dl>



## Description

The next suitable SELECT statement rebuilds the respective result cache entry.

