<!-- loiof9486656d74b4b059f53c28f7d5f8be9 -->

# ALTER SYSTEM \{ENABLE | DISABLE\} ALL \[ASYNCHRONOUS | SYNCHRONOUS\] TABLE REPLICAS Statement \(System Management\)

Activates or deactivates the overall replication operation of all replication tables or of asynchronous or synchronous tables only.



<a name="loiof9486656d74b4b059f53c28f7d5f8be9__section_vnq_pf1_5gb"/>

## Syntax - Table Replica

```
ALTER SYSTEM { ENABLE | DISABLE } ALL [ ASYNCHRONOUS | SYNCHRONOUS ] TABLE REPLICAS 
```



## Syntax Elements


<dl>
<dt><b>

ENABLE

</b></dt>
<dd>

Activates the overall replication operation of all specified replication tables.



</dd><dt><b>

DISABLE

</b></dt>
<dd>

Deactivates the overall replication operation of all specified replication tables.



</dd><dt><b>

ASYNCHRONOUS

</b></dt>
<dd>

Applies the operation to all asynchronous tables.



</dd><dt><b>

SYNCHRONOUS

</b></dt>
<dd>

Applies the operation to all synchronous tables.



</dd>
</dl>



## Description

Activates or deactivates the overall replication operation of all replication tables or of asynchronous or synchronous tables.



<a name="loiof9486656d74b4b059f53c28f7d5f8be9__section_bkb_mxx_vcb"/>

## Permissions

You must have the SERVICE ADMIN system privilege.



## Examples

Activate all synchronous table replication.

```
ALTER SYSTEM ENABLE ALL SYNCHRONOUS TABLE REPLICAS;
```

Deactivate all asynchronous table replication.

```
ALTER SYSTEM DISABLE ALL ASYNCHRONOUS TABLE REPLICAS;
```

Deactivate all table replication.

```
ALTER SYSTEM DISABLE ALL TABLE REPLICAS;
```

