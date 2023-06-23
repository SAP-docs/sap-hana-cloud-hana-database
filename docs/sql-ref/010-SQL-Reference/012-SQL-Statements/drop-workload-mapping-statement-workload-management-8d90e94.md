<!-- loio8d90e94880924f7d957ba73db7e7db17 -->

# DROP WORKLOAD MAPPING Statement \(Workload Management\)

Drops a workload mapping.



## Syntax

```
DROP WORKLOAD MAPPING <mapping_name>
```



## Syntax Elements


<dl>
<dt><b>

*<mapping\_name\>*

</b></dt>
<dd>

Specifies the workload mapping to drop.

```
<mapping_name> ::= <identifier>
```



</dd>
</dl>



## Description

Drops a workload mapping.



<a name="loio8d90e94880924f7d957ba73db7e7db17__section_bkb_mxx_vcb"/>

## Permissions

The use of this statement requires the WORKLOAD ADMIN system privilege.



## Examples

Remove the workload mapping "MyWorkloadMapping".

```
DROP WORKLOAD MAPPING "MyWorkloadMapping";
```

**Related Information**  


[WORKLOAD\_MAPPINGS System View](../../020-System-Views-Reference/021-System-Views/workload-mappings-system-view-89a0660.md "Provides information about available workload mappings.")

