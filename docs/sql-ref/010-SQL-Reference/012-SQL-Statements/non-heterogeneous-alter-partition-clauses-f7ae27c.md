<!-- loiof7ae27ca1b954471a4e1a7feab2c24d7 -->

# Non-Heterogeneous Alter Partition Clauses

Modifies the partitions of an existing table with a non-heterogeneous partitioning schema.



<a name="loiof7ae27ca1b954471a4e1a7feab2c24d7__section_rtv_tk4_lgb"/>

## Syntax

```
ALTER TABLE <table_name>
   { <partition_table_clause> 
   | <add_range_clause>
   | <redefine_range_partition_clause>
   | <move_partition_clause>
   | <drop_range_partition_clause>
   | <merge_partition_clause>
   | <alter_dynamic_range_clauses>
   | <alter_dynamic_property_clause>
   | <alter_partition_numa_node_preference_clause>
   | <alter_partition_movable_clause>
   }
```




<dl>
<dt><b>

*<partition\_table\_clause\>*

</b></dt>
<dd>

Partitions an existing unpartitioned table using a non-heterogeneous partitioning schema.

```
<partition_table_clause> ::=
   { PARTITION BY <hash_partition> [ SUBPARTITION BY { <range_partition> | <hash_partition> } ]
     | PARTITION BY <range_partition> [ SUBPARTITION BY <range_partition> ]
      | PARTITION BY <roundrobin_partition> [ SUBPARTITION BY <range_partition> ] }
   [ ONLINE ]
```

Partitioning by date values requires the format YYYYMMDD, YYYY-MM-DD, or YYYY/MM/DD. Date is the most granular date time value that you can use for partitioning.

You can find more information about table partitioning in the *SAP HANA Cloud, SAP HANA Database Administration Guide*.


<dl>
<dt><b>

*<hash\_partition\>*

</b></dt>
<dd>

Partitions the created table by using a hash partitioning scheme.

```
<hash_partition> ::= 
HASH ( <partition_expression> [ , <partition_expression> [,...] ] ) 
   [ [ NO ] PRIMARY KEY CHECK ]
   PARTITIONS { <num_partitions> | GET_NUM_SERVERS() }
```



</dd><dt><b>

*<range\_partition\>*

</b></dt>
<dd>

Partitions the created table by using a first-level range partitioning scheme.

```
<range_partition> ::= RANGE ( <partition_expression> )
   [ [ NO ] PRIMARY KEY CHECK ] ( <part_range> [ , <part_range> [ ,...] ] )
```



</dd><dt><b>

*<subrange\_partition\>*

</b></dt>
<dd>

Partitions the created table by using a range partitioning scheme.

```
<subrange_partition> ::= RANGE ( <partition_expression> ) ( <part_subrange> [ , <part_subrange> [ ,...] ] )
```



</dd><dt><b>

*<roundrobin\_partition\>*

</b></dt>
<dd>

Partitions the created table by using a round-robin partitioning scheme.

```
<roundrobin_partition> ::= ROUNDROBIN PARTITIONS { <num_partitions> | GET_NUM_SERVERS() }
```



</dd>
</dl>


<dl>
<dt><b>

*<partition\_expression\>*

</b></dt>
<dd>

Declares the specifier that segregates data into partitions.

```
<partition_expression> ::= 
<column_name> [ AS <dynamic_range_data_type> ] 
   | YEAR( <part_column_name> ) 
   | MONTH( <part_column_name> )
   | HOUR( <part_column_name> 
```

When using dynamic range partitioning on the OTHER partition, only *<column\_name\>* is supported.


<dl>
<dt><b>

*<column\_name\>*

</b></dt>
<dd>

Specifies the partitioning column. The column must be of a data type supported for the partitioning scheme.


<dl>
<dt><b>

Hash partitioning

</b></dt>
<dd>

TINYINT, SMALLINT, INT, BIGINT, DECIMAL, DECIMAL\(p,s\), CLOB, NCLOB, NVARCHAR \( or VARCHAR which is an alias of NVARCHAR\), BLOB, VARBINARY, DATE, TIME, TIMESTAMP and SECONDDATE.



</dd><dt><b>

Range partitioning

</b></dt>
<dd>

STRING, TINYINT, SMALLINT, INT, BIGINT \(not supported for dynamic range partitioning\), NVARCHAR, DECIMAL\(p,s\), DATE, TIMESTAMP, SECONDDATE, FIXED, RAW \(SQL Binary/Varbinary\).



</dd>
</dl>



</dd><dt><b>

*<dynamic\_range\_data\_type\>*

</b></dt>
<dd>

Specifies the data type for dynamic range partitioning.

```
<dynamic_range_data_type> ::= { INT | DATE | BIGINT }
```



</dd><dt><b>

YEAR / MONTH / HOUR

</b></dt>
<dd>

Specifies the precision of the date based partitioning column. When partitioning by HOUR, the *<part\_range\>* must be expressed using one of the following formats:


<table>
<tr>
<td valign="top">

'YYYY-MM-DD HH'

</td>
<td valign="top">

-   Enclosed in single quotes.
-   Date delimiter is present.
-   A space exists before the hour granularity.



</td>
<td valign="top">

'2010-01-01 23'

</td>
</tr>
<tr>
<td valign="top">

'YYYYMMDDHH'

</td>
<td valign="top">

-   Enclosed in single quotes.
-   No date delimiter is present.
-   No space exists before the hour granularity.



</td>
<td valign="top">

'2010010123'

</td>
</tr>
<tr>
<td valign="top">

YYYYMMDDHH

</td>
<td valign="top">

-   Without single quotes.
-   No date delimiter is present.
-   No space exists before the hour granularity.



</td>
<td valign="top">

2010010123

</td>
</tr>
</table>



</dd>
</dl>



</dd><dt><b>

\[ NO \] PRIMARY KEY CHECK

</b></dt>
<dd>

The primary key check is performed on the first level of a range or hash partition. If not specified, the default behavior is to perform the check.



</dd><dt><b>

*<num\_partitions\>*

</b></dt>
<dd>

Specifies the number of HASH partitions to create for the table.

```
<num_partitions> ::= <unsigned_integer>
```



</dd><dt><b>

GET\_NUM\_SERVERS\(\)

</b></dt>
<dd>

Returns the number of servers/partitions according to table placement. You can find more information on table placement in the *SAP HANA Cloud, SAP HANA Database Administration Guide*.



</dd>
</dl>


<dl>
<dt><b>

ONLINE

</b></dt>
<dd>

Allows you to partition an existing table without blocking DML while the DDL is executing. ONLINE is only supported for column-store, non-replicated tables, where specifying ONLINE performs an operation that only acquires a shared table lock. The operation is still serialized with other concurrent DDL operations on the table, including other ONLINE DDL operations. The default value must be a constant value and not a function.



</dd>
</dl>


<dl>
<dt><b>

*<part\_range\>*

</b></dt>
<dd>

Specifies the range specifications for a first-level range partition.

```
<part_range> ::= 
   PARTITION <range_values> [ <range_prop_list> ]
   [, PARTITION <range_values> [ <range_prop_list> ] [,...] ] 
```


<dl>
<dt><b>

*<range\_values\>*

</b></dt>
<dd>

Specifies the values of the partition.

```
<range_values> ::= 
   <min_value> <= VALUES < <max_value>
   | VALUE[S] = <target_value>
   | <partition_others>
```

Return to [*<add\_range\_clause\>*](non-heterogeneous-alter-partition-clauses-f7ae27c.md#loiof7ae27ca1b954471a4e1a7feab2c24d7__add_range_clause), [*<redefine\_range\_partition\_clause\>*](non-heterogeneous-alter-partition-clauses-f7ae27c.md#loiof7ae27ca1b954471a4e1a7feab2c24d7__redefine_range_partition_clause)[*<drop\_range\_partition\_clause\>*](non-heterogeneous-alter-partition-clauses-f7ae27c.md#loiof7ae27ca1b954471a4e1a7feab2c24d7__drop_range_partition_clause)


<dl>
<dt><b>

*<min\_value\>*

</b></dt>
<dd>

Specifies the minimum value of the range. The value cannot be negative.

```
<min_value> ::= <string_literal> | <numeric_literal>
```



</dd><dt><b>

*<max\_value\>*

</b></dt>
<dd>

Specifies the maximum value of the range. The value cannot be negative.

```
<max_value> ::= <string_literal> | <numeric_literal>
```



</dd><dt><b>

*<target\_value\>*

</b></dt>
<dd>

Specifies a single value of the range. The value cannot be negative.

```
<target_value> ::= <string_literal> | <numeric_literal> 
```



</dd>
</dl>



</dd>
</dl>


<dl>
<dt><b>

*<partition\_others\>*

</b></dt>
<dd>

Specifies a partition for all values outside of the defined partition ranges.

```
<partition_others> ::= 
OTHERS [ DYNAMIC [ THRESHOLD <threshold_count> ] ] 
```

OTHERS can be defined on a range partition at either level.



</dd>
</dl>


<dl>
<dt><b>

DYNAMIC THRESHOLD *<threshold\_count\>*

</b></dt>
<dd>

The keyword DYNAMIC enables dynamic range partitioning on the table \(the default is inactive\) and THRESHOLD specifies the maximum row count in the partition before generating a new dynamic range partition from OTHERS or the priority for determining the maximum row count value. The THRESHOLD default, if not specified, is 10 000 000 \(10 million\) rows. You can define DYNAMIC on a single RANGE partition or on the second-level range of an X-RANGE partition. To enable dynamic range partitioning, the range column of OTHERS requires a NOT NULL constraint. For more information on dynamic range partitioning, see *Dynamic Range Partitioning*.



</dd>
</dl>



</dd><dt><b>

*<range\_prop\_list\>*

</b></dt>
<dd>

Specifies the properties for the partition.

```
<range_prop_list> ::= <range_prop> [ <range_prop> ...] ]

<range_prop> ::= 
   { INSERT {OFF | ON}
   | AT [ LOCATION ] ( <location> )
   | <load_unit> 
   | <group_list>
   | <persistent_memory_spec_clause>
   | <numa_node_preference_clause>
   | <set_movable> }
```


<dl>
<dt><b>

INSERT \{ ON | OFF \}

</b></dt>
<dd>

Specifies if INSERT statements are allowed on a partition. If defined at the first-level, it applies to all second-level partitions within the first-level partition. If defined at both the first- and second-level, any value at the second-level overrides the first-level value. If not specified, default is ON.



</dd><dt><b>

*<location\>*

</b></dt>
<dd>

Specifies where the partitions reside.

```
<location> ::= '<HANA_host>:<HANA_port>'
```

If no location is specified, then for each first-level partition, a different indexserver is selected from those available \(primary and secondary indexservers\) in a round-robin fashion, and the second-level partitions then inherit the assigned location from the parent partition.

If a location is only specified for a parent first level partition, then any child second-level partitions inherit the location of the parent.

If a location is specified for a child second-level partition, then the second-level partition is assigned to that location, regardless of any parent location specification.



</dd><dt><b>

*<load\_unit\>*

</b></dt>
<dd>

Specifies how to load data into memory when the table is queried. Specifying the load unit is only supported on column-store tables. *<load\_unit\>* can be set at column, table, and partition levels.

```
<load_unit> ::= { COLUMN | PAGE } LOADABLE
```


<dl>
<dt><b>

COLUMN LOADABLE

</b></dt>
<dd>

In-memory loading - the entire column is loaded into memory. COLUMN LOADABLE boosts performance at the cost of higher memory usage. This is the default behavior unless another value is inherited.



</dd><dt><b>

PAGE LOADABLE

</b></dt>
<dd>

In-buffer cache loading - column data is loaded by page into the buffer cache. PAGE LOADABLE reduces memory usage for specific columns by not requiring those columns to be fully memory resident.



</dd>
</dl>

In the case of competing or unspecified *<load\_unit\>* settings, the following logic is applied.

-   If there is a load unit preference specified for a column, apply that value.

-   Else if there is a load unit preference specified for the parent partition, apply that value.

-   Else if there is a load unit specified for the parent table, apply that value.

-   Else apply the default \(COLUMN LOADABLE\).




</dd><dt><b>

*<group\_list\>*

</b></dt>
<dd>

Specifies the GROUP option to apply to the specified partition.

```
<group_list> ::= <group> [ <group> ... ]

<group> ::= GROUP {NAME | TYPE | SUBTYPE } <identifier>
```

Each partition can be assigned a group name, type, and subtype. If a GROUP option already exists on a partition, then the new value overwrites the existing value.



</dd><dt><b>

*<persistent\_memory\_spec\_clause\>*

</b></dt>
<dd>

Enables or disables persistent memory storage preference at the table, range partition, or column level, depending on where the clause is situated in the CREATE statement. For example, when specified inside the *<column\_definition\>* clause, it enables or disables persistent memory storage for the column.

```
<persistent_memory_spec> ::= PERSISTENT MEMORY <pm_preference>

<pm_preference> ::= { ON | OFF }
```



</dd><dt><b>

*<numa\_node\_preference\_clause\>*

</b></dt>
<dd>

Sets the NUMA node preferences. This clause can be set in various locations such as range partition definitions \(not hash or round-robin\) and column definitions.

```
<numa_node_preference_clause> ::= NUMA NODE ( <numa_node_index_spec> )

<numa_node_index_spec> :: = <numa_node_spec> [, <numa_node_spec> [,…] 

<numa_node_spec> ::= { <integer_const> | <integer_const> TO <integer_const> }
```


<dl>
<dt><b>

*<numa\_node\_spec\>*

</b></dt>
<dd>

Specify one or more single NUMA nodes \(*<single\_node\_spec\>*\), or one or more NUMA node ranges \(*<range\_node\_spec\>*\), or a mixture of both.

NUMA node indexes should be specified in the range of 0 to one less than max\_numa\_node\_count, where max\_numa\_node\_count is the number of NUMA nodes configured for the system. If the NUMA node index specified is greater than or equal to max\_numa\_node\_count, then a random NUMA node in the range of 0 to one less than max\_numa\_node\_count is selected for allocation. For example, on a system where max\_numa\_node\_count is set to 8, if you specify a NUMA node index of 10, then any node in the range of 0 to 7 \(inclusive\) is chosen randomly for allocation.



</dd><dt><b>

*<integer\_const\>*

</b></dt>
<dd>

*<integer\_const\>* is an integer that cannot be a negative number.



</dd>
</dl>



</dd><dt><b>

*<set\_movable\>*

</b></dt>
<dd>

Specifies whether a partition is movable.

```
<set_movable> ::= [ NOT ] MOVABLE
```

If not specified, then the value is inherited from its parent partitions \(from near to far\). If none of the parents have the move property explicitly set, then the table-level moveable property value is used. If none of these apply, then the partition is moveable by default.



</dd>
</dl>

Return to [*<redefine\_range\_partition\_clause\>*](non-heterogeneous-alter-partition-clauses-f7ae27c.md#loiof7ae27ca1b954471a4e1a7feab2c24d7__redefine_range_partition_clause) or [*<numa\_node\_preference\_clause\>*](non-heterogeneous-alter-partition-clauses-f7ae27c.md#loiof7ae27ca1b954471a4e1a7feab2c24d7__numa_node_preference_clause).



</dd>
</dl>


<dl>
<dt><b>

INSERT \{ ON | OFF \}

</b></dt>
<dd>

Specifies if INSERT statements are allowed on a partition. If defined at the first-level, it applies to all second-level partitions within the first-level partition. If defined at both the first- and second-level, any value at the second-level overrides the first-level value. If not specified, default is ON.



</dd><dt><b>

*<location\>*

</b></dt>
<dd>

Specifies where the partitions reside.

```
<location> ::= '<HANA_host>:<HANA_port>'
```

If no location is specified, then for each first-level partition, a different indexserver is selected from those available \(primary and secondary indexservers\) in a round-robin fashion, and the second-level partitions then inherit the assigned location from the parent partition.

If a location is only specified for a parent first level partition, then any child second-level partitions inherit the location of the parent.

If a location is specified for a child second-level partition, then the second-level partition is assigned to that location, regardless of any parent location specification.



</dd><dt><b>

*<load\_unit\>*

</b></dt>
<dd>

Specifies how to load data into memory when the table is queried. Specifying the load unit is only supported on column-store tables. *<load\_unit\>* can be set at column, table, and partition levels.

```
<load_unit> ::= { COLUMN | PAGE } LOADABLE
```


<dl>
<dt><b>

COLUMN LOADABLE

</b></dt>
<dd>

In-memory loading - the entire column is loaded into memory. COLUMN LOADABLE boosts performance at the cost of higher memory usage. This is the default behavior unless another value is inherited.



</dd><dt><b>

PAGE LOADABLE

</b></dt>
<dd>

In-buffer cache loading - column data is loaded by page into the buffer cache. PAGE LOADABLE reduces memory usage for specific columns by not requiring those columns to be fully memory resident.



</dd>
</dl>

In the case of competing or unspecified *<load\_unit\>* settings, the following logic is applied.

-   If there is a load unit preference specified for a column, apply that value.

-   Else if there is a load unit preference specified for the parent partition, apply that value.

-   Else if there is a load unit specified for the parent table, apply that value.

-   Else apply the default \(COLUMN LOADABLE\).




</dd><dt><b>

*<group\_list\>*

</b></dt>
<dd>

Specifies the GROUP option to apply to the specified partition.

```
<group_list> ::= <group> [ <group> ... ]

<group> ::= GROUP {NAME | TYPE | SUBTYPE } <identifier>
```

Each partition can be assigned a group name, type, and subtype. If a GROUP option already exists on a partition, then the new value overwrites the existing value.



</dd><dt><b>

*<persistent\_memory\_spec\_clause\>*

</b></dt>
<dd>

Enables or disables persistent memory storage preference at the table, range partition, or column level, depending on where the clause is situated in the CREATE statement. For example, when specified inside the *<column\_definition\>* clause, it enables or disables persistent memory storage for the column.

```
<persistent_memory_spec> ::= PERSISTENT MEMORY <pm_preference>

<pm_preference> ::= { ON | OFF }
```



</dd><dt><b>

*<numa\_node\_preference\_clause\>*

</b></dt>
<dd>

Sets the NUMA node preferences. This clause can be set in various locations such as range partition definitions \(not hash or round-robin\) and column definitions.

```
<numa_node_preference_clause> ::= NUMA NODE ( <numa_node_index_spec> )

<numa_node_index_spec> :: = <numa_node_spec> [, <numa_node_spec> [,…] 

<numa_node_spec> ::= { <integer_const> | <integer_const> TO <integer_const> }
```


<dl>
<dt><b>

*<numa\_node\_spec\>*

</b></dt>
<dd>

Specify one or more single NUMA nodes \(*<single\_node\_spec\>*\), or one or more NUMA node ranges \(*<range\_node\_spec\>*\), or a mixture of both.

NUMA node indexes should be specified in the range of 0 to one less than max\_numa\_node\_count, where max\_numa\_node\_count is the number of NUMA nodes configured for the system. If the NUMA node index specified is greater than or equal to max\_numa\_node\_count, then a random NUMA node in the range of 0 to one less than max\_numa\_node\_count is selected for allocation. For example, on a system where max\_numa\_node\_count is set to 8, if you specify a NUMA node index of 10, then any node in the range of 0 to 7 \(inclusive\) is chosen randomly for allocation.



</dd><dt><b>

*<integer\_const\>*

</b></dt>
<dd>

*<integer\_const\>* is an integer that cannot be a negative number.



</dd>
</dl>



</dd><dt><b>

*<set\_movable\>*

</b></dt>
<dd>

Specifies whether a partition is movable.

```
<set_movable> ::= [ NOT ] MOVABLE
```

If not specified, then the value is inherited from its parent partitions \(from near to far\). If none of the parents have the move property explicitly set, then the table-level moveable property value is used. If none of these apply, then the partition is moveable by default.



</dd>
</dl>



</dd><dt><b>

*<add\_range\_clause\>*

</b></dt>
<dd>

Adds a range to an existing partition. Only one range can be added at a time.

```
<add_range_clause> ::= ADD PARTITION ( <column_name> ) { <range_values> | OTHERS } 
```


<dl>
<dt><b>

OTHERS

</b></dt>
<dd>

Specifies a partition for all values outside of the defined partition ranges.



</dd>
</dl>



</dd><dt><b>

*<redefine\_range\_partition\_clause\>*

</b></dt>
<dd>

Modifies the existing ranges or range properties within a non-heterogeneous partitioned table. You can add new ranges or split pr merge existing ranges, as long and the redefined ranges provide a valid partition for all existing data within the table. If a partition is empty, and it is not included in the redefined ranges, then it is dropped.

```
<redefine_range_partition_clause> ::= 
PARTITION BY RANGE (<column_name>) (  <redefine_spec> [ ,<redefine _spec> ] );
```


<dl>
<dt><b>

*<redefine\_spec\>*

</b></dt>
<dd>

Specifies the redefined range.

```
<redefine_spec> ::= { PARTITION <range_values> [ , PARTITION <range_values> [,...] 
  [, <range_prop_list> ] }
```



</dd>
</dl>



</dd><dt><b>

*<move\_partition\_clause\>*

</b></dt>
<dd>

Moves one or more existing non-heterogeneous range partition to a new location.

```
<move_partition_clause> ::= 
   MOVE [PARTITION <part_num>[, <part_num> [,...] TO <indexserver_host_port> 
            [, PARTITION <part_num> [, <part_num> [,...] ] TO <indexserver_host_port> [,...]] [PHYSICAL][ONLINE]
```

The ONLINE parameter can be specified only when moving one or more partitions to different hosts.

For example, you could include the ONLINE parameter when moving partitions 1 and 2 to MyServer1 and partitions 3 and 4 to MyServer2.

```
ALTER TABLE T1 MOVE PARTITION 1,2 TO 'MyServer1:34240', PARTITION 3,4 TO 'MyServer2' ONLINE
```

However, in case you do not use the ONLINE parameter, you can only specify one partition and one host.

```
ALTER TABLE T1 MOVE PARTITION 1 TO MyServer1:34240;
```


<dl>
<dt><b>

*<part\_num\>*

</b></dt>
<dd>

Specifies the number of the partition to be moved.

```
<part_num> ::= <unsigned_integer>
```



</dd><dt><b>

*<indexserver\_host\_port\>*

</b></dt>
<dd>

Specifies the internal indexserver host name and port number where the table is to be moved.

```
<indexserver_host_port> ::= 'host_name:port_number'
```



</dd><dt><b>

ONLINE

</b></dt>
<dd>

Allows you to partition an existing table without blocking DML while the DDL is executing. ONLINE is only supported for column-store, non-replicated tables, where specifying ONLINE performs an operation that only acquires a shared table lock. The operation is still serialized with other concurrent DDL operations on the table, including other ONLINE DDL operations. The default value must be a constant value and not a function.

If load units are not specified while repartitioning, the load unit for all new partitions and subpartitions is set to DEFAULT.



</dd><dt><b>

PHYSICAL

</b></dt>
<dd>

The PHYSICAL keyword is only for column store tables. When specified, LOBs on disk are also moved. When not specified, LOBs on disk are excluded from the move.



</dd>
</dl>



</dd><dt><b>

*<drop\_range\_partition\_clause\>*

</b></dt>
<dd>

Drops a non-heterogeneous partition from a table. Only one partition can be dropped at a time.

```
<drop_range_partition_clause> ::= DROP PARTITION { <range_values> | OTHERS }
```



</dd><dt><b>

*<merge\_partition\_clause\>*

</b></dt>
<dd>

Merges all parts of a partitioned table into a non-partitioned table.

```
<merge_partition_clause> ::= MERGE PARTITIONS AT [ LOCATION ] '<hostname>:<port_number>';
```



</dd><dt><b>

*<alter\_dynamic\_range\_clauses\>*

</b></dt>
<dd>

Defines the alter operations you can perform to dynamic range options.

```
<alter_dynamic_range_clauses> ::= 
  <add_dynamic_range>
  | <drop_dynamic_range>
  | <partition_others_dynamic_range>
```

Dynamic range partitioning is only supported for single RANGE and X-RANGE partitions. For X-RANGE, dynamic range can only be defined on the second-level partition. Dynamic range partitioning is disabled by default. PARTITION OTHERS must exist on the applicable level before you can execute alter operations on dynamic range options. For information on dynamic range partitioning, see *Dynamic Range Partitioning* in the *SAP HANA Cloud, SAP HANA Database Administration Guide*.


<dl>
<dt><b>

*<add\_dynamic\_range\>*

</b></dt>
<dd>

Creates a new partition.

```
<add_dynamic_range> ::= ADD PARTITION FROM OTHERS
```



</dd><dt><b>

*<drop\_dynamic\_range\>*

</b></dt>
<dd>

Drops empty partitions.

```
<drop_dynamic_range> ::= DROP EMPTY PARTITIONS
```



</dd><dt><b>

*<partition\_others\_dynamic\_range\>*

</b></dt>
<dd>

Specifies other supported dynamic partitioning options.

```
<partition_others_dynamic_range> ::= PARTITION OTHERS { DYNAMIC [ THRESHOLD <threshold_count> ] | NO DYNAMIC }
```

The keyword DYNAMIC enables dynamic range partitioning on the table \(the default is inactive\) and THRESHOLD specifies the maximum row count in the partition before generating a new dynamic range partition from OTHERS or the priority for determining the maximum row count value. The THRESHOLD default, if not specified, is 10 000 000 \(10 million\) rows. You can define DYNAMIC on a single RANGE partition or on the second-level range of an X-RANGE partition. To enable dynamic range partitioning, the range column of OTHERS requires a NOT NULL constraint. For more information on dynamic range partitioning, see *Dynamic Range Partitioning*.



</dd>
</dl>



</dd><dt><b>

*<alter\_dynamic\_property\_clause\>*

</b></dt>
<dd>

Change the applied property.

```
<alter_dynamic_property_clause> ::= PARTITION OTHERS <dynamic_threshold>
```


<dl>
<dt><b>

*<dynamic\_threshold\>*

</b></dt>
<dd>

Specifies the threshold to apply.

```
<dynamic_threshold> ::= DYNAMIC [ THRESHOLD <threshold_count> ]
```



</dd>
</dl>


<dl>
<dt><b>

DYNAMIC THRESHOLD *<threshold\_count\>*

</b></dt>
<dd>

The keyword DYNAMIC enables dynamic range partitioning on the table \(the default is inactive\) and THRESHOLD specifies the maximum row count in the partition before generating a new dynamic range partition from OTHERS or the priority for determining the maximum row count value. The THRESHOLD default, if not specified, is 10 000 000 \(10 million\) rows. You can define DYNAMIC on a single RANGE partition or on the second-level range of an X-RANGE partition. To enable dynamic range partitioning, the range column of OTHERS requires a NOT NULL constraint. For more information on dynamic range partitioning, see *Dynamic Range Partitioning*.



</dd>
</dl>



</dd><dt><b>

*<alter\_partition\_numa\_node\_preference\_clause\>*

</b></dt>
<dd>

Alters the NUMA node preference for the specified partition numbers. You can specify multiple partition numbers in a comma separated list.

```
<alter_partition_numa_node_preference_clause> ::= ALTER PARTITION <partition_id_list>  <numa_node_preference_clause>
```


<dl>
<dt><b>

*<partition\_id\_list\>*

</b></dt>
<dd>

Specifies the partition to apply the property to.

```
<partition_id_list> ::= ( <partition_id> [, partition_id [,...] ] )
```

```
<partition_id> ::= <unsigned_integer>
```



</dd><dt><b>

*<numa\_node\_preference\_clause\>*

</b></dt>
<dd>

Alters the NUMA node preferences. Although this clause is defined here at the table level, *<numa\_node\_preference\_clause\>* can be set in various locations such as range partition definitions \(not hash or round-robin\) and column definitions, as indicated in the syntax within the topic. *<numa\_node\_preference\_clause\>* is not supported for heterogeneous partitions.

```
<numa_node_preference_clause> ::= NUMA NODE { ( <numa_node_index_spec> ) | NULL } [ IMMEDIATE | DEFERRED ]

<numa_node_index_spec> :: = <numa_node_spec> [, <numa_node_spec> [,…] ]

<numa_node_spec> ::= { <single_node_spec> | <range_node_spec> }

<single_node_spec> :: =  <integer_const>
<range_node_spec> :: =  <integer_const> TO <integer_const>
```


<dl>
<dt><b>

NULL

</b></dt>
<dd>

To unset existing NUMA node preferences on the associated object \(table, column, partition, or replica\), specify NUMA NODE NULL.



</dd><dt><b>

IMMEDIATE, DEFERRED

</b></dt>
<dd>

Specify whether to apply the NUMA node preferences immediately \(IMMEDIATE\) or to defer applying the preferences until the next time the table is reloaded \(DEFERRED\). If you specify IMMEDIATE, then the associated table, column, or table partition is immediately moved according to the altered preference settings.



</dd><dt><b>

*<integer\_const\>*

</b></dt>
<dd>

*<integer\_const\>* cannot be a negative number.



</dd><dt><b>

*<numa\_node\_spec\>*

</b></dt>
<dd>

Specify one or more single NUMA nodes \(*<single\_node\_spec\>*\), or one or more NUMA node ranges \(*<range\_node\_spec\>*\), or a mixture of both.

NUMA node indexes should be specified in the range of 0 to one less than max\_numa\_node\_count, where max\_numa\_node\_count is the number of NUMA nodes configured for the system. If the NUMA node index specified is greater than or equal to max\_numa\_node\_count, then a random NUMA node in the range of 0 to one less than max\_numa\_node\_count is selected for allocation. For example, on a system where max\_numa\_node\_count is set to 8, if you specify a NUMA node index of 10, then any node in the range of 0 to 7 \(inclusive\) is chosen randomly for allocation.



</dd>
</dl>

Return to [*<range\_prop\_list\>*](non-heterogeneous-alter-partition-clauses-f7ae27c.md#loiof7ae27ca1b954471a4e1a7feab2c24d7__range_prop_list).



</dd>
</dl>



</dd><dt><b>

*<alter\_partition\_movable\_clause\>*

</b></dt>
<dd>

Controls whether a partition is movable.

```
<alter_partition_movable_clause> ::=
   ALTER PARTITION { <partition_id_list> | <range_list> } SET [ NOT ] MOVABLE
```



</dd>
</dl>



<a name="loiof7ae27ca1b954471a4e1a7feab2c24d7__section_s45_55p_lgb"/>

## Description

Modifies the partitions of an existing table with a non-heterogeneous partitioning schema. To modify partitions of an existing table with a heterogeneous partitioning schema, see the topic *Heterogeneous Partition Clauses* in this guide.



<a name="loiof7ae27ca1b954471a4e1a7feab2c24d7__section_tnl_jcz_nvb"/>

## Permissions

The \(non-destructive\) clauses listed below can be executed with the PARTITION ADMIN system privilege. For all other clauses, you must have the ALTER object privilege on the table to alter a partition.

-   [*<partition\_table\_clause\>*](non-heterogeneous-alter-partition-clauses-f7ae27c.md#loiof7ae27ca1b954471a4e1a7feab2c24d7__partition_table_clause)
-   [*<add\_range\_clause\>*](non-heterogeneous-alter-partition-clauses-f7ae27c.md#loiof7ae27ca1b954471a4e1a7feab2c24d7__add_range_clause)
-   [*<redefine\_range\_partition\_clause\>*](non-heterogeneous-alter-partition-clauses-f7ae27c.md#loiof7ae27ca1b954471a4e1a7feab2c24d7__redefine_range_partition_clause)
-   [*<move\_partition\_clause\>*](non-heterogeneous-alter-partition-clauses-f7ae27c.md#loiof7ae27ca1b954471a4e1a7feab2c24d7__move_partition_clause)
-   [*<merge\_partition\_clause\>*](non-heterogeneous-alter-partition-clauses-f7ae27c.md#loiof7ae27ca1b954471a4e1a7feab2c24d7__merge_partition_clause)
-   [*<alter\_dynamic\_range\_clauses\>*](non-heterogeneous-alter-partition-clauses-f7ae27c.md#loiof7ae27ca1b954471a4e1a7feab2c24d7__alter_dynamic_range_clauses)
-   [*<alter\_dynamic\_property\_clauses\>*](non-heterogeneous-alter-partition-clauses-f7ae27c.md#loiof7ae27ca1b954471a4e1a7feab2c24d7__alter_dynamic_property_clause)
-   [*<alter\_partition\_numa\_node\_preference\_clause\>*](non-heterogeneous-alter-partition-clauses-f7ae27c.md#loiof7ae27ca1b954471a4e1a7feab2c24d7__alter_partition_numa_node_preference_clause)



<a name="loiof7ae27ca1b954471a4e1a7feab2c24d7__section_enr_w4v_lgb"/>

## Examples


<dl>
<dt><b>



</b></dt>
<dd>

Convert a non-partitioned column store table named T1 to a range partitioned table.

```
CREATE COLUMN TABLE T1 (a INT, b INT);
ALTER TABLE T1 PARTITION BY RANGE (a) (PARTITION 10 <= VALUES < 20);
```

Add a new second-level partition to an existing range-partitioned table, making it a range-range partitioned table.

```
ALTER TABLE T1 PARTITION BY 
   RANGE (a) (PARTITION 10 <= VALUES < 20) SUBPARTITION BY RANGE (b) (PARTITION 100 <= VALUES < 150);
```

Redefine the existing first-level partition to ranges 10 - 15 and 15 - 20.

```
ALTER TABLE T1 PARTITION BY 
   RANGE (a) (PARTITION 10 <= VALUES < 15, PARTITION 15 <= VALUES < 20) 
   SUBPARTITION BY RANGE (b) (PARTITION 100 <= VALUES < 150);
```

Add a new partition to the second-level partition.

```
ALTER TABLE T1 ADD PARTITION (b) 150 <= VALUES < 200;
```

Move a partition.

```
ALTER TABLE T1 MOVE PARTITION 1 TO 'myhost:30201';
```

Move multiple partitions to new locations.

```
ALTER TABLE T2 MOVE PARTITION 1,2 TO 'myhost2:34240', PARTITON 3,4 TO 'myhost3:34242’ ONLINE;
```

Drop the partition range 10 - 15.

```
ALTER TABLE T1 DROP PARTITION (a) 10 <= VALUES < 15;
```

Merge all partitions into a single non-partitioned table.

```
ALTER TABLE T1 MERGE PARTITIONS; 
```

```
ALTER TABLE T1 PARTITION BY RANGE (a) (PARTITION 15 <= VALUES < 20 NUMA NODE ('3') DEFERRED);
```

Alter column table T1, setting the NUMA node preference at the partition level on NUMA node index 3. Since DEFERRED is specified, it sets only the NUMA preference for the partition; the actual allocations are made when the table is reloaded. IMMEDIATE alters column table T1, setting the NUMA node preference on partition 1, which already exists. The allocations are made immediately, and the table partition is reloaded to node 4.

```
ALTER TABLE T1 ALTER PARTITION 1 NUMA NODE ('4') IMMEDIATE;
```

Create a non-partitioned table named T2, convert the table to a range partitioned table, and then add an additional partition.

```
CREATE COLUMN TABLE T2 (a INT, b INT);
ALTER TABLE T2 PARTITION BY RANGE (a) (PARTITION VALUE = 1, PARTITION OTHERS);
ALTER TABLE T2 ADD PARTITION (a) 2 <= VALUES < 10;
```

Create a non-partitioned table named T3 and then convert the table to a range-range partitioned table.

```
CREATE COLUMN TABLE T3 (a INT, b INT);
ALTER TABLE T2 PARTITION BY RANGE (a) (PARTITION VALUE = 1, PARTITION OTHERS) 
SUBPARTITION BY RANGE (b) (PARTITION VALUE = 2);
```

Convert an existing hash partitioned table named T4 to a range partitioned table.

```
CREATE TABLE T4 (A INT, B INT) PARTITION BY HASH (A) PARTITIONS 2;
ALTER TABLE T4 PARTITION BY RANGE (A) (PARTITION 10 <= values < 20, PARTITION OTHERS);
```

Convert an existing range partitioned table named T5 to a hash partitioned table.

```
CREATE TABLE T5 (A INT, B INT) PARTITION BY RANGE (A) (PARTITION 10 <= values < 20, PARTITION OTHERS);
ALTER TABLE T5 PARTITION BY HASH (A) PARTITIONS 2;
```

This example alters table T6 to make partition 1 not movable.

```
ALTER TABLE T6 ALTER PARTITION 1 SET NOT MOVABLE;
```

This example alters table T6 to make partition 2 and 3 movable.

```
ALTER TABLE T6 ALTER PARTITION (2,3) SET MOVABLE;

```

This example alters table T7 to make the range movable.

```
ALTER TABLE T7 ALTER PARTITION RANGE (C1) ((PARTITION 100 <= VALUES < 200)) SET MOVABLE;
```


<dl>
<dt><b>

Dynamic Range Partitioning

</b></dt>
<dd>

These examples are based on table A1 using this CREATE TABLE statement.

```
CREATE COLUMN TABLE A1 (A INT, B INT NOT NULL) PARTITION BY RANGE (A) (PARTITION VALUES = 10) 
   SUBPARTITION BY RANGE (B) (PARTITION VALUES = 20, PARTITION OTHERS);
```

Enable dynamic range partitioning on the OTHERS partition with a DYNAMIC TRHRESHOLD of 100.

```
ALTER TABLE A1 PARTITION OTHERS DYNAMIC THRESHOLD 100;
```

Add another partition from OTHERS.

```
ALTER TABLE A1 ADD PARTITION FROM OTHERS;
```

Drop any empty partitions except OTHERS.

```
ALTER TABLE A1 DROP EMPTY PARTITIONS;
```

Disable dynamic range partitioning on the OTHERS partition.

```
ALTER TABLE A1 PARTITION OTHERS NO DYNAMIC;
```



</dd>
</dl>



</dd>
</dl>

**Related Information**  


[Heterogeneous Alter Partition Clauses](heterogeneous-alter-partition-clauses-a4258b8.md "Modifies the partitions of an existing table with a heterogeneous partitioning schema.")

[ALTER TABLE Statement \(Data Definition\)](alter-table-statement-data-definition-20d329a.md "Alters a base or temporary table. See the ALTER VIRTUAL TABLE statement for altering virtual tables.")

[Table Partitioning](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2024_3_QRC/en-US/c2ea130bbb571014b024ffeda5090764.html "The partitioning feature of the SAP HANA database splits column-store tables horizontally into disjunctive sub-tables or partitions. In this way, large tables can be broken down into smaller, more manageable parts. Partitioning is typically used in multiple-host systems, but it may also be beneficial in single-host systems.") :arrow_upper_right:

[TABLE\_PARTITIONS System View](../../020-System-Views-Reference/021-System-Views/table-partitions-system-view-c81d9be.md "Partition-specific information for partitioned tables.")

[Dynamic Range Partitioning](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2024_3_QRC/en-US/6ebea7782b9e4758baeed923e388ee32.html "For heterogeneous partitioning schemas dynamic range partitioning is available to support the automatic maintenance of the OTHERS partition.") :arrow_upper_right:

