<!-- loio22f628bdb85d4ccd885cf642d3fd31c4 -->

# DROP WORKLOAD CLASS Statement \(Workload Management\)

Removes workload classes.



## Syntax

```
DROP WORKLOAD CLASS <workload_class_name>
```



## Syntax Elements


<dl>
<dt><b>

*<workload\_class\_name\>*

</b></dt>
<dd>

Removes the specified workload class.

```
<workload_class_name> ::= <identifier>
```



</dd>
</dl>



## Description

Removes workload classes.



<a name="loio22f628bdb85d4ccd885cf642d3fd31c4__section_fyf_gxx_vcb"/>

## Permissions

The use of this statement requires the WORKLOAD ADMIN system privilege.



## Examples

Drop the workload class “MyWorkloadClass”.

```
DROP WORKLOAD CLASS "MyWorkloadClass";
```

**Related Information**  


[WORKLOAD\_CLASSES System View](../../020-System-Views-Reference/021-System-Views/workload-classes-system-view-d520e47.md "Provides information about available workload classes.")

