<!-- loio9d274fa7e20d4841a6017e020d871aa0 -->

# ALTER SYSTEM REFRESH RESULT CACHE Statement \(System Management\)

Refreshes all result cache entries related to the specified object with up-to-date results.



## Syntax

```
ALTER SYSTEM REFRESH [<cache_type>] RESULT CACHE <object_name>
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

*<object\_name\>*

</b></dt>
<dd>

Specifies the object name. It can be any of the objects that has a result cache.

```
<object_name>
```

Those objects can be found in the system view M\_RESULT\_CACHE.



</dd>
</dl>



## Description

All result cache entries related to *<object\_name\>* are refreshed with up-to-date results.



<a name="loio9d274fa7e20d4841a6017e020d871aa0__section_m1v_ycb_chb"/>

## Examples

Refresh all static result cache entries related to *<view-object\>*.

```
ALTER SYSTEM REFRESH STATIC RESULT CACHE <view-object>;
```

**Related Information**  


[M\_RESULT\_CACHE System View](../../020-System-Views-Reference/022-Monitoring-Views/m-result-cache-system-view-71e6d97.md "Provides result cache information.")

