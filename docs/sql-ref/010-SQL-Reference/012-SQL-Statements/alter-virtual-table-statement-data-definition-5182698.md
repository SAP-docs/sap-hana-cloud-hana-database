<!-- loio51826981a2d24e7aa872f4278220b579 -->

# ALTER VIRTUAL TABLE Statement \(Data Definition\)

Modifies a virtual table's column properties, and lets you refresh the metadata of a virtual table.



## Syntax

```
ALTER VIRTUAL TABLE <virtual_table_name>
  { SET PROPERTY 'name' = 'value'[, 'name2' = 'value2'[, ...] ]
    | UNSET PROPERTY 'name'[, 'name2', ...]
    | ALTER <column_name> SET PROPERTY 'name' = 'value' [, 'name2' = 'value2' [, ...] ]
    | ALTER <column_name> UNSET PROPERTY 'name'[, 'name2'[, ...] ]
    | [ CANCEL ] ADD SHARED [ SNAPSHOT ] REPLICA [ <partition_clause> ] [ <load_unit> ] [ ASYNC ]
    | ALTER REPLICA [ <partition_clause> ] [ <load_unit> ]
    | { ENABLE | DISABLE | DROP } REPLICA
    | [ CANCEL ] REFRESH SNAPSHOT REPLICA [ ASYNC ]
    | REFRESH DEFINITION }
```



## Syntax Elements


<dl>
<dt><b>

*<virtual\_table\_name\>*

</b></dt>
<dd>

Specifies a virtual table.

```
<virtual_table_name> ::= [ <schema_name>.]<identifier>
```



</dd><dt><b>

*<column\_name\>*

</b></dt>
<dd>

Specifies a virtual column.

```
<column_name> ::= <identifier>
```



</dd><dt><b>

\[ CANCEL \] ADD SHARED \[ SNAPSHOT \] REPLICA \[ *<load\_unit\>* \] \[ ASYNC \]

</b></dt>
<dd>

Adds a replica column table with replication or a snapshot of the remote source. Replication is only supported for remote sources that support real-time change data capture \(CDC\). Snapshot replicas are supported for any remote source. An additional pointer is created within the virtual table to the replica table.


<dl>
<dt><b>

CANCEL

</b></dt>
<dd>

Cancels an asynchronous creation job. Include the ASYNC keyword when using CANCEL.



</dd><dt><b>

*<partition\_clause\>*

</b></dt>
<dd>

Specifies the partitioning scheme for the replica table. Only single-level range partitions are supported, and only snapshot replicas can be partitioned.

For clauses for creating heterogeneous and non-heterogeneous partitions, see the topics on *Non-heterogeneous Create Partition Clauses* *Heterogeneous Create Partition Clauses* in this guide.

 [Non-heterogeneous Create Partition Clauses](non-heterogeneous-create-partition-clauses-ca6a99b.md)

 [Heterogeneous Create Partition Clauses](heterogeneous-create-partition-clauses-d496e58.md)



</dd><dt><b>

*<load\_unit\>*

</b></dt>
<dd>

Specifies how to load data into memory when the replica table is queried.

```
<load_unit> ::= { COLUMN | PAGE } LOADABLE
```


<dl>
<dt><b>

COLUMN LOADABLE

</b></dt>
<dd>

In-memory loading - the entire column is loaded into memory. COLUMN LOADABLE boosts performance at the cost of higher memory usage.



</dd><dt><b>

PAGE LOADABLE

</b></dt>
<dd>

In-buffer cache loading - column data is loaded by page into the buffer cache. PAGE LOADABLE reduces memory usage for specific columns by not requiring those columns to be fully memory resident. This is the default behavior for replica tables.



</dd>
</dl>



</dd><dt><b>

ASYNC

</b></dt>
<dd>

Creates the replica asynchronously.



</dd>
</dl>



</dd><dt><b>

ALTER REPLICA \[ *<partition\_clause\>* \] \[ *<load\_unit\>* \]

</b></dt>
<dd>

Alters an existing replica column table.

If the replica is shared by multiple virtual tables, you cannot alter the partitioning scheme.



</dd><dt><b>

ENABLE REPLICA

</b></dt>
<dd>

Enables the replica. This clause is not supported for snapshot replicas.



</dd><dt><b>

DISABLE REPLICA

</b></dt>
<dd>

Disables the replica. This clause is not supported for snapshot replicas.



</dd><dt><b>

\[ CANCEL \] REFRESH SNAPSHOT REPLICA \[ ASYNC \]

</b></dt>
<dd>

Refreshes the snapshot of the remote source.


<dl>
<dt><b>

CANCEL

</b></dt>
<dd>

Cancels an asynchronous refresh job. Include the ASYNC keyword when using CANCEL.



</dd><dt><b>

ASYNC

</b></dt>
<dd>

Refreshes the replica asynchronously.



</dd>
</dl>



</dd><dt><b>

DROP REPLICA

</b></dt>
<dd>

Drops an in-memory replica column table. The additional pointer to the replica table within the virtual table is removed.



</dd><dt><b>

REFRESH DEFINITION

</b></dt>
<dd>

Updates a virtual table to reflect metadata changes in the corresponding remote table.



</dd>
</dl>



## Description

Any properties that are not set by using the ALTER VIRTUAL TABLE statement are marked as read-only, and they cannot be updated by the ALTER VIRTUAL TABLE statement.

Use DROP TABLE *<table\_name\>* to drop a virtual table.



## Examples

Set a new property for the virtual table REMOTE1\_VT, then update and unset it.

```
ALTER VIRTUAL TABLE REMOTE1_VT SET PROPERTY 'name1' = 'value1';
ALTER VIRTUAL TABLE REMOTE1_VT SET PROPERTY 'name1' = 'value2';
ALTER VIRTUAL TABLE REMOTE1_VT UNSET PROPERTY 'name1';
```

Set a new property for the virtual column A in virtual table REMOTE1\_VT, then update and unset it.

```
ALTER VIRTUAL TABLE REMOTE1_VT ALTER A SET PROPERTY 'name1' = 'value1';
ALTER VIRTUAL TABLE REMOTE1_VT ALTER A SET PROPERTY 'name1' = 'value2';
ALTER VIRTUAL TABLE REMOTE1_VT ALTER A UNSET PROPERTY 'name1';
```

Add a shared replica table for the virtual table REMOTE1\_VT.

```
ALTER VIRTUAL TABLE REMOTE1_VT ADD SHARED REPLICA;
```

Asynchronously add a shared replica table for the virtual table REMOTE1\_VT.

```
ALTER VIRTUAL TABLE REMOTE1_VT ADD SHARED REPLICA ASYNC;
```

Add a shared snapshot replica table for the virtual table REMOTE1\_VT.

```
ALTER VIRTUAL TABLE REMOTE1_VT ADD SHARED SNAPSHOT REPLICA;
```

Refresh the snapshot replica for the virtual table REMOTE1\_VT.

```
ALTER VIRTUAL TABLE REMOTE1_VT REFRESH SNAPSHOT REPLICA;
```

Cancel an asynchronous refresh of the snapshot replica for the virtual table REMOTE1\_VT.

```
ALTER VIRTUAL TABLE REMOTE1_VT CANCEL REFRESH SNAPSHOT REPLICA ASYNC;
```

Set the load unit type of the replica for the virtual table REMOTE1\_VT to COLUMN LOADABLE.

```
ALTER VIRTUAL TABLE REMOTE1_VT ALTER REPLICA COLUMN LOADABLE;
```

Drop a shared replica table for the virtual table REMOTE1\_VT.

```
ALTER VIRTUAL TABLE REMOTE1_VT DROP REPLICA;
```

Add a partitioned replica table for the virtual table VT1.

```
ALTER VIRTUAL TABLE "VT1" ADD SHARED SNAPSHOT REPLICA PARTITION BY RANGE("l_orderkey")
 (PARTITION 1 <= VALUES < 10000, PARTITION 10000 <= VALUES < 20000, PARTITION 20000 <= VALUES < 30000, 
 PARTITION 30000 <= VALUES < 40000, PARTITION 40000 <= VALUES < 50000, PARTITION OTHERS) ASYNC
```

**Related Information**  


[DROP TABLE Statement \(Data Definition\)](drop-table-statement-data-definition-20d7fd2.md "Removes a physical or virtual table from the database.")

[VIRTUAL\_TABLES System View](../../020-System-Views-Reference/021-System-Views/virtual-tables-system-view-21031a8.md "Provides information about virtual tables.")

[VIRTUAL\_TABLE\_REPLICAS System View](../../020-System-Views-Reference/021-System-Views/virtual-table-replicas-system-view-ce3d19f.md "Provides information on the relationships between virtual tables and replica tables.")

[M\_EXPENSIVE\_STATEMENTS System View](../../020-System-Views-Reference/022-Monitoring-Views/m-expensive-statements-system-view-20af736.md "Provides all statements with a duration longer than a specified threshold.")

[M\_VIRTUAL\_TABLE\_REPLICA\_ACTION\_HISTORY System View](../../020-System-Views-Reference/022-Monitoring-Views/m-virtual-table-replica-action-history-system-view-855d7b6.md "Provides replica action information.")

