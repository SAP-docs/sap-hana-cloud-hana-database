<!-- loioa4258b865710423b8712b06fb5b8e7c5 -->

# Heterogeneous Alter Partition Clauses

Modifies the partitions of an existing table with a heterogeneous partitioning schema.



<a name="loioa4258b865710423b8712b06fb5b8e7c5__section_rtv_tk4_lgb"/>

## Syntax

```
ALTER TABLE <table_name>
   { <partition_table_clause>
   | <add_partition_clauses>
   | <redefine_partition_clause>
   | <move_partition_clauses>
   | <drop_partition_clauses>
   | <merge_partition_clause>
   | <alter_dynamic_range_clauses>
   | <alter_dynamic_property_clause>
   | <alter_partition_load_unit_clause>
   | <alter_partition_group_clauses>
   }

```




<dl>
<dt><b>

*<partition\_table\_clause\>*

</b></dt>
<dd>

Partitions an existing unpartitioned table using a heterogeneous range, range-range, or range-hash partitioning scheme.

```
<partition_table_clause> ::= PARTITION BY RANGE (<partition_expression>) 
   [ [ NO ] PRIMARY KEY CHECK ] ( <part_spec> [, <part_spec> [,...] ] ) [ ONLINE ]

<part_spec> ::= 
   { ( <part_range> [, <part_range> [,...] ] ) [ <subpart_by_clause> ] 
   | ( <part_range> ) [ <subpart_by_clause> ] }

<subpart_by_clause> ::= SUBPARTITION BY { sub_part_range | <sub_part_hash> } }
```

All subpartitions must be of the same type and reference the same column or in the case of a hash subpartition the same group of columns. Mixed range and hash subpartitions are not supported. If the first subpartition is a range using column B, then all additional subpartition must be ranges using column B. If the first subpartition is a hash, referencing columns B and C, then all subpartitions must hash referencing the same group of columns.


<dl>
<dt><b>

*<partition\_expression\>*

</b></dt>
<dd>

Declares the specifier that segregates data into partitions.

```
<partition_expression> ::= 
   { <column_name>
   | YEAR( <column_name> )
   | MONTH( <column_name> )
   | HOUR( <column_name> )
   }
```

To use dynamic range partitioning, only *<column\_name\>* is supported for the partitioning column containing the OTHERS partition.


<dl>
<dt><b>

*<column\_name\>*

</b></dt>
<dd>

Specifies the partitioning column. The column must be of a data type supported for the partitioning scheme.


<dl>
<dt><b>

Hash partitions

</b></dt>
<dd>

TINYINT, SMALLINT, INT, BIGINT, DECIMAL, DECIMAL\(p,s\), CLOB, NCLOB, VARCHAR, NVARCHAR, BLOB, VARBINARY, DATE, TIME, TIMESTAMP and SECONDDATE.



</dd><dt><b>

Range partitions

</b></dt>
<dd>

STRING, TINYINT, SMALLINT, INT, BIGINT, NVARCHAR, DECIMAL\(p,s\), DATE, TIMESTAMP, SECONDDATE, FIXED, RAW \(SQL Binary/Varbinary\).



</dd>
</dl>



</dd>
</dl>


<dl>
<dt><b>

HOUR / YEAR / MONTH

</b></dt>
<dd>

Specifies the precision of the date based partitioning column.



</dd>
</dl>



</dd><dt><b>

\[ NO \] PRIMARY KEY CHECK

</b></dt>
<dd>

The primary key check is performed on the first level of a partition. If not specified, the default behavior is to perform the check.



</dd><dt><b>

*<part\_range\>*

</b></dt>
<dd>

Specifies the range for the first- or second-level range partition.

```
<part_range> ::= PARTITION <range_values> [ <range_prop_list> ]
```

Return to [*<add\_partition\_clauses\>*.](heterogeneous-alter-partition-clauses-a4258b8.md#loioa4258b865710423b8712b06fb5b8e7c5__add_partition_clauses)


<dl>
<dt><b>

*<range\_values\>*

</b></dt>
<dd>

Specifies the values of the first- or second-level range partition.

```
<range_values> ::= 
   <min_value> <= VALUES < <max_value>
   | VALUE[S] = <target_value>
   | <partition_others>
```

Return to [*<redefine\_partition\_clause\>*](heterogeneous-alter-partition-clauses-a4258b8.md#loioa4258b865710423b8712b06fb5b8e7c5__redefine_partition_clause), [*<move\_partition\_clauses\>*](heterogeneous-alter-partition-clauses-a4258b8.md#loioa4258b865710423b8712b06fb5b8e7c5__move_partition_clauses), [*<drop\_partition\_clauses\>*](heterogeneous-alter-partition-clauses-a4258b8.md#loioa4258b865710423b8712b06fb5b8e7c5__drop_partition_clauses), [*<alter\_partition\_load\_unit\_clause\>*](heterogeneous-alter-partition-clauses-a4258b8.md#loioa4258b865710423b8712b06fb5b8e7c5__alter_partition_load_unit_clause), or [*<alter\_partition\_group\_clauses\>*](heterogeneous-alter-partition-clauses-a4258b8.md#loioa4258b865710423b8712b06fb5b8e7c5__alter_partition_group_clauses).


<dl>
<dt><b>

*<min\_value\>*

</b></dt>
<dd>

Specifies the minimum value of a first- or second-level range partition. The value cannot be negative.

```
<min_value> ::= <string_literal> | <numeric_literal>
```



</dd><dt><b>

*<max\_value\>*

</b></dt>
<dd>

Specifies the maximum value of a first- or second-level range partition. The value cannot be negative.

```
<max_value> ::= <string_literal> | <numeric_literal>
```



</dd><dt><b>

*<target\_value\>*

</b></dt>
<dd>

Specifies a single value of a first- or second-level range partition. The value cannot be negative.

```
<target_value> ::= <string_literal> | <numeric_literal> 
```



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
   { OTHERS [ DYNAMIC [ {THRESHOLD <threshold_count> ] ]
   | [ DYNAMIC INTERVAL <interval>  ] }
```


<dl>
<dt><b>

DYNAMIC THRESHOLD *<threshold\_count\>*

</b></dt>
<dd>

The keyword DYNAMIC enables dynamic range partitioning on the table \(default is inactive\) and THRESHOLD specifies the maximum row count in the partition before generating a new dynamic range partition from OTHERS or the priority for determining the maximum row count value. The THRESHOLD default, if not specified, is 100 000 000 rows. You can only define DYNAMIC on a single range partition or on any range subpartition. For more information on dynamic range partitioning, see *Dynamic Range Partitioning*.



</dd><dt><b>

DYNAMIC INTERVAL

</b></dt>
<dd>

Specifies a dynamic interval for the range OTHERS partition. The interval is between the last range partition and new partition created dynamically.

```
<interval> ::= <interval_value> <interval_type>

<interval_value>  ::= <unsigned_integer>
<interval_type> ::= [ YEAR | MONTH | HOUR ]
```

Dynamic interval is only supported when the partition column type is TINYINT, SMALLINT, INT, BIGINT, DATE, SECONDDATE or LONGDATE. If no *<interval\_type\>* is specified, INT is used implicitly.



</dd>
</dl>



</dd>
</dl>



</dd><dt><b>

*<range\_prop\_list\>*

</b></dt>
<dd>

Specifies the first- or second-level properties for the range partition.

```
<range_prop_list> ::= <part_property> [ <part_property> ...]

<part_property> ::= 
   INSERT {OFF | ON}
   | AT [ LOCATION ] ( <location> )
   | <load_unit> 
   | <group_list>
   | <persistent_memory_spec>
   | <numa_node_preference_clause>
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

*<persistent\_memory\_spec\>*

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
<numa_node_preference_clause> ::= NUMA NODE { ( <numa_node_index_spec> )

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



</dd>
</dl>



</dd>
</dl>



</dd><dt><b>

*<sub\_part\_range\>*

</b></dt>
<dd>

Specifies the range subpartition.

```
<sub_part_range> ::= RANGE ( <sub_range_col_def> ) ( <part_range> [, <part_range> [,...] ] )

<sub_range_col_def> ::= { <exist_subpart_col_name> | <partition_expression> }
```

All subpartitions must be of the same type and reference the same column or in the case of a hash subpartition the same group of columns. Mixed range and hash subpartitions are not supported. If the first subpartition is a range using column B, then all additional subpartition must be ranges using column B. If the first subpartition is a hash, referencing columns B and C, then all subpartitions must hash referencing the same group of columns.


<dl>
<dt><b>

*<exist\_part\_column\_name\>*

</b></dt>
<dd>

Specifies the name of the existing first-level range partitioning column.



</dd><dt><b>

*<sub\_range\_col\_def\>*

</b></dt>
<dd>

Specifies the subpartitioning column. If this is the first subpartition in the partitioned table, then specify *<partition\_expression\>*. For all subsequent range subpartitions added or referenced, specify *<exist\_subpart\_col\_name\>*, the name of the existing range subpartitioning column.



</dd>
</dl>



</dd>
<dd>

Return to [*<partition\_table\_clause\>*](heterogeneous-alter-partition-clauses-a4258b8.md#loioa4258b865710423b8712b06fb5b8e7c5__partition_table_clause), [*<add\_partition\_clauses\>*](heterogeneous-alter-partition-clauses-a4258b8.md#loioa4258b865710423b8712b06fb5b8e7c5__add_partition_clauses) or [*<redefine\_partition\_clause\>*](heterogeneous-alter-partition-clauses-a4258b8.md#loioa4258b865710423b8712b06fb5b8e7c5__redefine_partition_clause).



</dd><dt><b>

*<sub\_part\_hash\>*

</b></dt>
<dd>

Specifies the hash subpartition.

```
<sub_part_hash> ::= HASH ( <sub_hash_col_def> ) PARTITIONS <num_partitions> [ AT [ LOCATION ] ( <loc_list> ) ]

<sub_hash_col_def> ::= { <exist_col_grp_list> | <partition_expression> [,<partition_expression> [,...] ] }
```

All subpartitions must be of the same type and reference the same column or in the case of a hash subpartition the same group of columns. Mixed range and hash subpartitions are not supported. If the first subpartition is a range using column B, then all additional subpartition must be ranges using column B. If the first subpartition is a hash, referencing columns B and C, then all subpartitions must hash referencing the same group of columns. With the exception of LOCATION, all hash partitions share the same properties.


<dl>
<dt><b>

*<sub\_hash\_col\_def\>*

</b></dt>
<dd>

Specifies the subpartitioning column. If this is the first subpartition in the partitioned table, then specify *<partition\_expression\>*. For all subsequent hash subpartitions added or referenced, specify *<exist\_col\_grp\_list\>*, the name of the existing hash partitioning column or group of columns.



</dd><dt><b>

*<loc\_list\>*

</b></dt>
<dd>

Specifies where the hash partition resides.

> ### Note:  
> When the number of target partitions is a multiple of the number of source partitions, they are distributed across the available index servers in a round-robin style. However, in cases where the number of target partitions is not a multiple of the source partitions, all the target partitions are stored at the location of the first source partition.

```
<loc_list> ::= <location> [ , <location> [,...] ]

<location> ::= '<HANA_host>:<HANA_port>'
```



</dd>
</dl>

Return to [*<partition\_table\_clause\>*](heterogeneous-alter-partition-clauses-a4258b8.md#loioa4258b865710423b8712b06fb5b8e7c5__partition_table_clause), [*<add\_partition\_clauses\>*](heterogeneous-alter-partition-clauses-a4258b8.md#loioa4258b865710423b8712b06fb5b8e7c5__add_partition_clauses) or [*<redefine\_partition\_clause\>*](heterogeneous-alter-partition-clauses-a4258b8.md#loioa4258b865710423b8712b06fb5b8e7c5__redefine_partition_clause).



</dd><dt><b>

ONLINE

</b></dt>
<dd>

Allows you to partition an existing table without blocking DML while the DDL is executing. ONLINE is only supported for column-store, non-replicated tables, where specifying ONLINE performs an operation that only acquires a shared table lock. The operation is still serialized with other concurrent DDL operations on the table, including other ONLINE DDL operations. The default value must be a constant value and not a function.

If load units are not specified while repartitioning, the load unit for all new partitions and subpartitions is set to DEFAULT.



</dd>
</dl>



</dd><dt><b>

*<add\_partition\_clauses\>*

</b></dt>
<dd>

Defines the alter operations to add first- and second-level partitions to an existing partitioned table.


<dl>
<dt><b>

*<add\_partition\_clause\>*

</b></dt>
<dd>

Adds a new first-level partition, with an optional subpartition, to an existing partitioned table.

```
<add_partition_clause> ::= ADD PARTITION RANGE ( <exist_part_column_name> ) ( ( <part_range_list> )
   [ SUBPARTITION BY { <sub_part_range> | <sub_part_hash> } ] );

<part_range_list> ::= <part_range> [, <part_range> [,...] ]
```

*<exist\_part\_column\_name\>* is the name of the existing first-level range partitioning column.

You can also add a partition by redefining existing partition ranges. See [*<redefine\_partition\_clause\>*](heterogeneous-alter-partition-clauses-a4258b8.md#loioa4258b865710423b8712b06fb5b8e7c5__redefine_partition_clause).



</dd><dt><b>

*<add\_subpart\_clause\>*

</b></dt>
<dd>

Adds a new range subpartition to an existing first-level range partition.

```
<add_partition_clause> ::= ALTER PARTITION RANGE (<exist_part_column_name>) ( ( <part_range_list> ) )
   PARTITION BY RANGE ( <sub_range_column_def> ) ( ( <subpart_range_list> ) );

<part_range_list> ::= <part_range> [, <part_range> [,...] ]
<sub_range_col_def> ::= { <exist_subpart_col_name> | <partition_expression> }
<subpart_range_list> ::= <part_range> [, <part_range> [,...] ]
```

If data exists in the table, then the subpartition specifications must account for all data within the partitioning column. For example, if a table contains the data rows \(10, 100\) and \(10, 200\), and the first-level partitioning column is the first column, then the subpartition range must include both values of column two. You could specify a range \(100 - 200\) or fixed values \(100, 200\). You could also include the OTHERS partition to account for later values added, which might fall outside the subpartition range.

To add a hash subpartition to an existing first-level range partition, use the *<redefine\_partition\_clause\>* syntax.


<dl>
<dt><b>

*<sub\_range\_col\_def\>*

</b></dt>
<dd>

Specifies the subpartitioning column. If this is the first subpartition in the partitioned table, then specify *<partition\_expression\>*. For all subsequent range subpartitions added or referenced, specify *<exist\_subpart\_col\_name\>*, the name of the existing range subpartitioning column.



</dd>
</dl>



</dd>
</dl>



</dd><dt><b>

*<redefine\_partition\_clause\>*

</b></dt>
<dd>

Modifies the existing ranges and the INSERT property of the first- and second-level partitions. The new ranges must provide a valid partition for all existing data within the table. If a partition or subpartition is empty, and it is not included in the redefined ranges, then it is dropped.

```
<redefine_partition_clause> ::= PARTITION BY RANGE (<exist_partition_column_name>) 
( ( <redefine_part_range_list> ) [ SUBPARTITION BY { <sub_part_range> | <sub_part_hash> } )

<redefine_part_range_list> ::= <redefine_part_range> [, <redefine_part_range> [,...] ]
```


<dl>
<dt><b>

*<exist\_part\_column\_name\>*

</b></dt>
<dd>

Specifies the name of the existing first-level range partitioning column.



</dd><dt><b>

*<redefine\_part\_range\>*

</b></dt>
<dd>

Specifies the range values for the redefined first-level range partition.

```
<redefine_part_range> ::= PARTITION <range_values> [ INSERT {OFF | ON} ]
```



</dd>
</dl>



</dd><dt><b>

*<move\_partition\_clauses\>*

</b></dt>
<dd>

Defines the alter operations to move partitions to a new location.


<dl>
<dt><b>

*<move\_range\_part\>*

</b></dt>
<dd>

Move a first- or second-level range partition to a new location.

```
<move_range_part> ::= 
   MOVE PARTITION <partition_number>[,.<partition_number>[,...].] TO ( <host>:<port> )
      [, PARTITION <partition_number>[,.<partition_number>[,...].]  TO ( <host>:<port> ) [ ONLINE ]
   | MOVE PARTITION <move_range_clause> TO ( <host>:<port> )
```

The ONLINE parameter can be specified only when moving one or more partitions to different hosts. For example, you could include it when moving partitions 1 and 2 to MyServer1 and partitions 3 and 4 to MyServer2.

```
ALTER TABLE T1 MOVE PARTITION 1,2 TO 'MyServer1:34240', PARTITION 3,4 TO 'MyServer2' ONLINE
```

But not when moving just partitions 1 and 2 to MyServer1.

```
ALTER TABLE T1 MOVE PARTITION 1,2 TO MyServer1:34240;
```

If you specify only the parent first-level partition, then all child partitions are also moved to the same location. If you specify a subpartition, then only the subpartition is moved.


<dl>
<dt><b>

*<partition\_number\>*

</b></dt>
<dd>

Specifies the first-level partition number to move. You cannot move only a second-level partition by partition number. To determine the value, use the TABLE\_PARTITIONS system view.



</dd><dt><b>

*<move\_range\_clause\>*

</b></dt>
<dd>

Specifies the first-or second-level range partition to move.

```
<move_range_clause> ::= RANGE ( <exist_partition_column_name> ) ( <move_range_spec> [, <move_range_spec> [,...] ] )

<move_range_spec> ::= ( <move_range_list> ) [ SUBPARTITION BY RANGE ( <exist_subpart_column_name> ) ( <move_range_list> ) ]
<move_range_list> ::= <move_range> [, <move_range> [,...] ]
<move_range> ::= PARTITION <range_values>
```


<dl>
<dt><b>

*<exist\_part\_column\_name\>*

</b></dt>
<dd>

Specifies the name of the existing first-level range partitioning column.



</dd><dt><b>

*<exist\_subpart\_column\_name\>*

</b></dt>
<dd>

Specifies the name of the existing range subpartitioning column.



</dd>
</dl>



</dd>
</dl>



</dd><dt><b>

*<move\_hash\_part\>*

</b></dt>
<dd>

Move a hash subpartition to a new location.

```
<move_range> ::= MOVE SUBPARTITIONS OF <move_hash> TO ( <move_loc_list> );
```


<dl>
<dt><b>

*<move\_hash\>*

</b></dt>
<dd>

Specifies the range partitions containing the hash partitions to move.

```
<move_hash> ::= RANGE ( <exist_part_column_name> ) ( ( PARTITION <range_values> ) )
```



</dd><dt><b>

*<move\_loc\_list\>*

</b></dt>
<dd>

Specifies the new locations for the hash subpartition.

```
<move_loc_list> ::= '<move_loc>' [, '<move_loc>' [,...] ]

<move_loc>::= <host>:<port>
```

Locations are assigned in the order they are specified. If you specify more locations than available hash partitions, unused locations are ignored. If you specify less locations than available hash partitions, the location restarts with the first location in the list. For example, if there are three hash partitions but only two locations are specified, partition three is assigned to location one.

For a hash subpartition with multiple partitions, you cannot move a single partition. The location list applies to all partitions, assigned in the order listed, but moving a partition to its same location results in the partition remaining stationary. To move specific partitions to specific locations, order the list a locations to match the order of the partitions. For example, the hash subpartition has three partitions, assigned to locA, locB, and locC respectively. To move partition 1 only, list the locations as locD, locB, locC. Partition 1 moves from locA to locD and partitions 2 and 3 move to their same location, effectively remaining unmoved.



</dd>
</dl>



</dd>
</dl>



</dd><dt><b>

*<drop\_partition\_clauses\>*

</b></dt>
<dd>

Defines the alter operations to drop range partitions. Hash partitions cannot be dropped.


<dl>
<dt><b>

*<drop\_partition\_clause\>*

</b></dt>
<dd>

Drops a first-level range partition and all associated subpartitions. Dropping a partition deletes any data contained within the partition or associated subpartition.

```
<drop_part_range> ::= DROP PARTITION RANGE (<exist_part_column_name>) ( ( <drop_part_range> [, <drop_part_range> ] ) );
```



</dd>
<dd>


<dl>
<dt><b>

*<exist\_part\_column\_name\>*

</b></dt>
<dd>

Specifies the name of the existing first-level range partitioning column.



</dd><dt><b>

*<drop\_part\_range\>*

</b></dt>
<dd>

Specifies the first-level range being dropped.

```
<drop_part_range> ::= PARTITION <range_values>
```



</dd>
</dl>



</dd><dt><b>

*<drop\_subpart\_clause\>*

</b></dt>
<dd>

Drops a range subpartition. Dropping the last range subpartition deletes the first-level range partition as well.

```
<drop_subpart_clause> ::= ALTER PARTITION RANGE (<exist_part_column_name>) ( (<part_range_drop> ) )
   DROP PARTITION RANGE (<exist_part_column_name>) ( ( <range_values> [, <range_values> [,...] ] ) )
```


<dl>
<dt><b>

*<exist\_part\_column\_name\>*

</b></dt>
<dd>

Specifies the name of the existing first-level range partitioning column.



</dd><dt><b>

*<part\_range\_drop\>*

</b></dt>
<dd>

Specifies the first-level range partition containing the range subpartition being dropped.

```
<part_range_drop> ::= <drop_part_range> 
```



</dd>
</dl>



</dd>
</dl>



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
```

Dynamic range is only supported for single range and range-range partitions. For range-range partitions, dynamic range partitions can only be defined on subpartitions. Dynamic range partitioning is disable by default. The OTHERS partition must exist on the applicable level before you can alter dynamic range partition options. For information on dynamic range partitioning, see *Dynamic Range Partitioning* in the *SAP HANA Cloud, SAP HANA Database Administration Guide*.

To enable or disable dynamic range partitioning or modify the threshold on an existing subpartition, redefine the partitions and add or remove the keywords DYNAMIC or DYNAMIC THRESHOLD to/from the existing OTHERS partition.


<dl>
<dt><b>

*<add\_dynamic\_range\>*

</b></dt>
<dd>

Creates a new dynamic range OTHERS partition.

```
<add_dynamic_range> ::= ADD PARTITION FROM OTHERS;
```



</dd><dt><b>

*<drop\_dynamic\_range\>*

</b></dt>
<dd>

Drops empty partitions.

```
<drop_dynamic_range> ::= DROP EMPTY PARTITIONS;
```



</dd>
</dl>



</dd><dt><b>

*<alter\_dynamic\_property\_clause\>*

</b></dt>
<dd>

Change the applied property.

```
<alter_dynamic_property_clause> ::= 
   ALTER PARTITION <partition_ids> <dynamic_property>
```


<dl>
<dt><b>

*<partition\_ids\>*

</b></dt>
<dd>

Specifies the partition to apply the property to.

```
<partition_ids> ::= 
   { <unsigned_integer> [, <unsigned_integer>... 
   | OTHERS 
   }
```



</dd><dt><b>

*<dynamic\_property\>*

</b></dt>
<dd>

Specifies the property to apply.

```
<dynamic_property> ::= 
   { DYNAMIC { [ THRESHOLD <threshold_count> ] | INTERVAL <interval> } 
   | NO DYNAMIC }
```


<dl>
<dt><b>

DYNAMIC THRESHOLD *<threshold\_count\>*

</b></dt>
<dd>

The keyword DYNAMIC enables dynamic range partitioning on the table \(default is inactive\) and THRESHOLD specifies the maximum row count in the partition before generating a new dynamic range partition from OTHERS or the priority for determining the maximum row count value. The THRESHOLD default, if not specified, is 100 000 000 rows. You can only define DYNAMIC on a single range partition or on any range subpartition. For more information on dynamic range partitioning, see *Dynamic Range Partitioning*.



</dd><dt><b>

DYNAMIC INTERVAL

</b></dt>
<dd>

Specifies a dynamic interval for the range OTHERS partition. The interval is between the last range partition and new partition created dynamically.

```
<interval> ::= <interval_value> <interval_type>

<interval_value>  ::= <unsigned_integer>
<interval_type> ::= [ YEAR | MONTH | HOUR ]
```

Dynamic interval is only supported when the partition column type is TINYINT, SMALLINT, INT, BIGINT, DATE, SECONDDATE or LONGDATE. If no *<interval\_type\>* is specified, INT is used implicitly.



</dd>
</dl>



</dd>
</dl>



</dd><dt><b>

*<alter\_partition\_load\_unit\_clause\>*

</b></dt>
<dd>

Alters the paging attributes for a range partition or subpartition.

```
<alter_partition_load_unit_clause> ::= ALTER PARTITION {<partition_id_list> | <range> } <load_unit>;
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



</dd>
</dl>


<dl>
<dt><b>

*<range\>*

</b></dt>
<dd>

Specifies the partition or subpartition range to alter.

```
<range> ::= RANGE ( <exist_part_column_name> ) ( ( <alter_load_unit_range_list>) [ SUBPARTITION BY { <sub_range> | <sub_hash> } ] );

<alter_load_unit_range_list> ::= PARTITION <range_values> [, PARTITION <range_values> [,...] ]
```



</dd><dt><b>

*<exist\_part\_column\_name\>*

</b></dt>
<dd>

Specifies the name of the existing first-level range partitioning column.



</dd><dt><b>

*<sub\_range\>*

</b></dt>
<dd>

Specifies the range of the range subpartition to alter.

```
<sub_range> ::= RANGE ( <exist_part_column_name> ) ( PARTITION <range_values> [,...] )
```



</dd><dt><b>

*<sub\_hash\>*

</b></dt>
<dd>

Specifies the hash subpartition.

```
<sub_hash> ::= HASH ( <exist_part_column_name> ) PARTITIONS <num_partitions>
```



</dd><dt><b>

*<load\_unit\>*

</b></dt>
<dd>

Specifies how to load data into memory when the table is queried. Specifying the load unit is only supported on column-store tables.

```
<load_unit> ::= { COLUMN | PAGE | DEFAULT } LOADABLE
```

In the case of competing or unspecified *<load\_unit\>* settings, the logic described in CREATE TABLE for *<load\_unit\>* is applied.


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



</dd><dt><b>

DEFAULT LOADABLE

</b></dt>
<dd>

If you specify DEFAULT, then there is no explicit preference for the paging attribute that is used when the results are loaded from the table. If there is an inherited loading unit from another object, then that loading unit is used.



</dd>
</dl>



</dd>
</dl>



</dd><dt><b>

*<alter\_partition\_group\_clauses\>*

</b></dt>
<dd>

Defines the alter operations you can perform with regards to setting and unsetting range partition group options.

```
<alter_partition_group_clauses> ::= 
   <set_partition_group_partitionid_clause>
   | <unset_replica_partition_partitionid_clause>
   | <set_partition_group_range_clause>
   | <unset_partition_group_range_clause>
   | <set_partion_replica_group_partitionid_clause>
   | <unset_partion_replica_group_partitionid_clause>
```


<dl>
<dt><b>

*<set\_partition\_group\_partitionid\_clause\>*

</b></dt>
<dd>

Specifies the group options to set on the specified rangeGROUP options are only supported on range partitions in a range, range-range, or range-hash partition schema.

```
<set_partition_group_partitionid_clause> ::= 
  ALTER PARTITION <group_partition_id_list> SET <group_list>
```

Use the M\_TABLE\_PARTITIONS view to see effective group values \(after applying inheritance from parent levels\).


<dl>
<dt><b>

*<group\_partition\_id\_list\>*

</b></dt>
<dd>

Specifies the numerical value of the partition.

```
<partition_id_list> ::= <partition_id> | '(' <partition_id> [, <partition_id>...] ')'
```

To determine the value, use the TABLE\_PARTITIONS system view.



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



</dd>
</dl>



</dd><dt><b>

*<unset\_partition\_group\_partitionid\_clause\>*

</b></dt>
<dd>

Removes all GROUP options \(NAME, TYPE, SUBTYPE\) applied to the specified partitions.

```
<unset_partition_group_partitionid_clause> ::= 
  ALTER PARTITION <partition_id_list>  UNSET GROUP
```



</dd><dt><b>

*<set\_partition\_group\_range\_clause\>*

</b></dt>
<dd>

Specifies the group options to set on the specified range partition or subpartition.

```
<set_partition_group_range_clause> ::= 
  ALTER PARTITION <group_range> SET <group_list> [ CASCADE ]
```

GROUP options are only supported on range partitions in a range, range-range, or range-hash partition schema. Use the M\_TABLE\_PARTITIONS view to see effective group values \(after applying inheritance from parent levels\).


<dl>
<dt><b>

*<group\_range\>*

</b></dt>
<dd>

Specifies the ranges of the range partition to apply the GROUP option to.

```
<group_range> ::= RANGE ( <exist_part_column_name> ) ( ( <part_range_list> )
   [SUBPARTITION BY RANGE ( <exist_part_column_name> ) ( <subpart_range_list> ) [,...] )

<part_range_list> ::= PARTITION <range_values> ] [, PARTITION <range_values> [,...] ]
<subpart_range_list> ::= PARTITION <range_values> ] [, PARTITION <range_values> [,...] ]
```



</dd><dt><b>

*<exist\_part\_column\_name\>*

</b></dt>
<dd>

Specifies the name of the existing first-level range partitioning column.



</dd><dt><b>

CASCADE

</b></dt>
<dd>

Applies the property change to all subpartitions within the specified range. This clause is only supported with the *<group\_range\>* option.



</dd>
</dl>



</dd><dt><b>

*<unset\_partition\_group\_range\_clause\>*

</b></dt>
<dd>

Removes all GROUP options \(NAME, TYPE, SUBTYPE\) applied to the specified partition.

```
<unset_partition_group_range_clause> ::= 
   ALTER PARTITION <group_range> } UNSET GROUP [ CASCADE ]
```



</dd><dt><b>

*<set\_partition\_replica\_group\_partitionid\_clause\>*

</b></dt>
<dd>

Specifies the group options to set on the specified replica partition.

```
<set_partition_replica_group_partitionid_clause> ::= 
   ALTER REPLICA PARTITION <partition_id_list> SET <group_list>
   [AT <replica_locations> ]
```

GROUP options are only supported on range partitions in a range, range-range, or range-hash partition schema. Use the M\_TABLE\_PARTITIONS view to see effective group values \(after applying inheritance from parent levels\).


<dl>
<dt><b>

*<replica\_locations\>*

</b></dt>
<dd>

Adds the replica to the specified locations.

```
<replica_locations> ::= { <indexserver_host_port> | ( <indexserver_host_port>, … ) }

<indexserver_host_port> ::= '<host_name>:<port_number>'
```

If *<replica\_locations\>* is not specified, then the replica table is added based on the table placement rule. If no table placement rule is also defined, then the replica table is added one of the worker nodes that is not a source table location and where there is not already an existing replica of the table. If there are no more replica nodes to add a replica table, then an error is returned.



</dd>
</dl>



</dd><dt><b>

*<unset\_partition\_replica\_group\_partitionid\_clause\>*

</b></dt>
<dd>

Removes all GROUP options \(NAME, TYPE, SUBTYPE\) applied to the specified partition id.

```
<unset_partition_replica_group_partitionid_clause> ::= 
   ALTER REPLICA PARTITION <partition_id_list> UNSET GROUP [ AT <replica_locations> ]
```



</dd>
</dl>



</dd>
</dl>



<a name="loioa4258b865710423b8712b06fb5b8e7c5__section_s45_55p_lgb"/>

## Description

Modifies the partitions of an existing table with a heterogeneous partitioning schema. To modify partitions of an existing table with a non-heterogeneous partitioning schema, see the topic *Non-heterogeneous Partition Clauses* in this guide.



<a name="loioa4258b865710423b8712b06fb5b8e7c5__section_tnl_jcz_nvb"/>

## Permissions

The \(non-destructive\) clauses listed below can be executed with the PARTITION ADMIN system privilege. For all other clauses, you must have the ALTER object privilege on the table to alter a partition.

-   [*<partition\_table\_clause\>*](heterogeneous-alter-partition-clauses-a4258b8.md#loioa4258b865710423b8712b06fb5b8e7c5__partition_table_clause)
-   [*<add\_partition\_clauses\>*](heterogeneous-alter-partition-clauses-a4258b8.md#loioa4258b865710423b8712b06fb5b8e7c5__add_partition_clauses)
-   [*<redefine\_partition\_clause\>*](heterogeneous-alter-partition-clauses-a4258b8.md#loioa4258b865710423b8712b06fb5b8e7c5__redefine_partition_clause)
-   [*<move\_partition\_clauses\>*](heterogeneous-alter-partition-clauses-a4258b8.md#loioa4258b865710423b8712b06fb5b8e7c5__move_partition_clauses)
-   [*<merge\_partition\_clause\>*](heterogeneous-alter-partition-clauses-a4258b8.md#loioa4258b865710423b8712b06fb5b8e7c5__merge_partition_clause)
-   [*<alter\_dynamic\_range\_clauses\>*](heterogeneous-alter-partition-clauses-a4258b8.md#loioa4258b865710423b8712b06fb5b8e7c5__alter_dynamic_range_clauses)
-   [*<alter\_dynamic\_property\_clause\>*](heterogeneous-alter-partition-clauses-a4258b8.md#loioa4258b865710423b8712b06fb5b8e7c5__alter_dynamic_property_clause)
-   [*<alter\_partition\_load\_unit\_clause\>*](heterogeneous-alter-partition-clauses-a4258b8.md#loioa4258b865710423b8712b06fb5b8e7c5__alter_partition_load_unit_clause)
-   [*<alter\_partition\_group\_clauses\>*](heterogeneous-alter-partition-clauses-a4258b8.md#loioa4258b865710423b8712b06fb5b8e7c5__alter_partition_group_clauses)



<a name="loioa4258b865710423b8712b06fb5b8e7c5__section_qpv_1pv_lgb"/>

## Examples


<dl>
<dt><b>



</b></dt>
<dd>

Convert the non-partitioned table T1 to a range-range partitioned table. The table has four first-level partitions \(10-20,20-30,40,OTHERS\). Range 10-20 has three subpartition ranges \(0-10, 10-100, others\). Range 40 has two subpartitions ranges \(0-10, OTHERS\). Both subpartitions have dynamic range partitioning enabled.

```
CREATE COLUMN TABLE T1 (a INT, b INT NOT NULL);

ALTER TABLE T1 PARTITION BY RANGE (a)
   ((PARTITION 10 <= VALUES < 20 INSERT OFF, PARTITION 20 <= VALUES < 30 INSERT OFF) 
       SUBPARTITION BY RANGE (b) (PARTITION 0 <= VALUES < 10, PARTITION 10 <= VALUES < 100, PARTITION OTHERS DYNAMIC THRESHOLD 2),
    (PARTITION VALUES = 40)
       SUBPARTITION BY RANGE(B) (PARTITION 0 <= VALUES < 10, PARTITION OTHERS DYNAMIC THRESHOLD 2),
    (PARTITION OTHERS));
```

Convert the non-partitioned table T2 to a range-hash partitioned table. The first level has two partition ranges \(10-20, 20-30\). The INSERT OFF property means you can't add data to the partitions. The second level is a hash with two partitions.

```
CREATE COLUMN TABLE T2 (a INT, b INT);

ALTER TABLE T2 PARTITION BY RANGE (a) ((PARTITION 10 <= VALUES < 20 INSERT OFF, PARTITION 20 <= VALUES < 30 INSERT OFF) 
   SUBPARTITION BY HASH (b) PARTITIONS 2);
```

Add a new first-level range partition 41-50 to table T1. The new partition has a subpartition with one range 0-10.

```
ALTER TABLE T1 ADD PARTITION RANGE (a) ((PARTITION 41 <= VALUES < 50)
   SUBPARTITION by RANGE (b) (PARTITION 0 <= VALUES < 10));
```

Redefine the existing first-level partition range 10-20 to ranges 5-10 and 15-20. Each redefined range retains its original subpartition. All existing range values must be accounted for in the redefined structure or they will be dropped if they do not contain data.

```
ALTER TABLE T1 PARTITION BY RANGE (a)
   ((PARTITION 5 <= VALUES < 10, PARTITION 10 <= VALUES < 20 INSERT OFF, PARTITION 20 <= VALUES < 30 INSERT OFF)
        SUBPARTITION BY RANGE (b) (PARTITION 0 <= VALUES < 10, PARTITION 10 <= VALUES < 100, PARTITION OTHERS DYNAMIC THRESHOLD 2),
    (PARTITION VALUES = 40) SUBPARTITION BY RANGE(B) (PARTITION 0 <= VALUES < 10, PARTITION OTHERS DYNAMIC THRESHOLD 2),
    (PARTITION 41 <= VALUES < 50) SUBPARTITION by RANGE (b) (PARTITION 0 <= VALUES < 10),
    (PARTITION OTHERS));
```

Move partition 1 \(range 5-10\) on table T1 to host myhost on port 30203.

```
ALTER TABLE T1 MOVE PARTITION 1 TO 'myhost:30203';
```

Move range 5-10 with subpartition range 0 - 10 on table T1 to host myhost on port 30203.

```
ALTER TABLE T1 MOVE RANGE (a) ((PARTITION 5 <= VALUES < 10) SUBPARTITION BY RANGE (b) (PARTITION 0 <= VALUES < 10)) TO 'myhost:30203';
```

Move the hash subpartition of range 10-20 on table T2 to host myhost1 port 30203 and myhost2 port 30203.

```
ALTER TABLE T2 MOVE SUBPARTITIONS OF RANGE (a) ((PARTITION 10 <= VALUES < 20) to ('myhost1:30203', 'myhost2:30203);
```

Drop the first-level partition range 5-10 on table 1. The subpartitions for that range only are dropped. The subpartition ranges 10-20 and 20-30 remain.

```
ALTER TABLE T1 DROP PARTITION RANGE (a) ((PARTITION 5 <= VALUES < 10));
```

Drop subpartition range 10-100 in range 10-20 on table T1.

```
ALTER TABLE T1 ALTER PARTITION RANGE (a) ((PARTITION 10 <= VALUES < 20)) DROP PARTITION RANGE (b) ((PARTITION 10 <= VALUES < 100));
```

Assign the group name GROUP1 to partition 2 on table T1.

```
ALTER TABLE T1 ALTER PARTITION 2 SET GROUP NAME "GROUP1";
```

Assign the group name GROUP2 to partitions 1 and 2 on table T1.

```
ALTER TABLE T1 ALTER PARTITION (1,2) SET GROUP NAME "GROUP2";

```

Assign the group name GROUP2 and the group type HR to the partition range 10 - 20 and all its subpartitions on table T1.

```
ALTER TABLE T1 ALTER PARTITION RANGE (a) ((PARTITION 20 <= VALUES < 30)) SET GROUP NAME "GROUP2" GROUP TYPE "HR" CASCADE;
```

Remove the GROUP value from partition 2 on table T1.

```
ALTER TABLE T1 ALTER PARTITION 2 UNSET GROUP;
```

Remove the GROUP value from partitions 1 and 2 on table T1.

```
ALTER TABLE T1 ALTER PARTITION (1,2) UNSET GROUP;
```

Remove the GROUP value from the partition range 10 -20 and its subpartitions on table T1.

```
ALTER TABLE T1 ALTER PARTITION RANGE (a) ((PARTITION 20 <= VALUES < 30)) UNSET GROUP CASCADE;
```

This example creates a multilevel heterogeneous partitioned table and then applies the *<load\_unit\>* attribute first by partition number \(1\) and then to partition range \(10 to 20\).

```
CREATE COLUMN TABLE T4 (a INT, b INT) PARTITION BY RANGE(a) 
   ((PARTITION 10 <= VALUES < 20) SUBPARTITION BY RANGE (b) (PARTITION VALUES=100));

ALTER TABLE T4 ALTER PARTITION 1 COLUMN LOADABLE;
ALTER TABLE T4 ALTER PARTITION RANGE (a) ((PARTITION 10 <= VALUES < 20) 
   SUBPARTITION BY RANGE (b) (PARTITION VALUES = 100)) PAGE LOADABLE;
```


<dl>
<dt><b>

Dynamic Range Partitioning

</b></dt>
<dd>

These examples are based on table A1 using this CREATE TABLE statement.

```
CREATE COLUMN TABLE A1 (A INT, B INT NOT NULL) PARTITION BY RANGE (A) 
   ((PARTITION 10 <= VALUES < 20) 
      SUBPARTITION BY RANGE (B) (PARTITION 15 <= VALUES < 20, PARTITION OTHERS),
    (PARTITION VALUES = 30) 
      SUBPARTITION BY RANGE (B) (PARTITION VALUES=20, PARTITION OTHERS),
    (PARTITION OTHERS));
```

Enable dynamic range partitioning on range 10-20, subpartition 15-20 on table A1.

```
ALTER TABLE A1 PARTITION BY RANGE (A) 
   ((PARTITION 10 <= VALUES < 20) 
      SUBPARTITION BY RANGE (B) (PARTITION 15 <= VALUES < 20, PARTITION OTHERS DYNAMIC),
    (PARTITION VALUES = 30) 
      SUBPARTITION BY RANGE (B) (PARTITION VALUES=20, PARTITION OTHERS),
    (PARTITION OTHERS));
```

Add another partition from OTHERS on table A1.

```
ALTER TABLE A1 ADD PARTITION FROM OTHERS;
```

Drop any empty partitions except OTHERS on table A1.

```
ALTER TABLE A1 DROP EMPTY PARTITIONS;
```

Set the threshold to 2 for dynamic range partitioning on the subpartition of range 10-20 on table A1.

```
ALTER TABLE A1 PARTITION BY RANGE (A) 
   ((PARTITION 10 <= VALUES < 20) 
      SUBPARTITION BY RANGE (B) (PARTITION 15 <= VALUES < 20, PARTITION OTHERS DYNAMIC THRESHOLD 2),
    (PARTITION VALUES = 30) 
      SUBPARTITION BY RANGE (B) (PARTITION VALUES = 20, PARTITION OTHERS),
    (PARTITION OTHERS));
```

Disable dynamic range partitioning on the subpartition on range 10-20 on table A1.

```
ALTER TABLE A1 PARTITION BY RANGE (A) 
   ((PARTITION 10 <= VALUES < 20) 
      SUBPARTITION BY RANGE (B) (PARTITION 15 <= VALUES < 20, PARTITION OTHERS),
    (PARTITION VALUES = 30) 
      SUBPARTITION BY RANGE (B) (PARTITION VALUES = 20, PARTITION OTHERS),
    (PARTITION OTHERS));
```


<dl>
<dt><b>

Redefine Partitions

</b></dt>
<dd>

Alter the load unit of any range partition in default storage:

```
ALTER TABLE A1 PARTITION BY RANGE (A)
   (PARTITION 0 <= VALUES < 10 PAGE LOADABLE,
    PARTITION OTHERS COLUMN LOADABLE);
```



</dd>
</dl>



</dd>
</dl>



</dd>
</dl>

**Related Information**  


[Non-Heterogeneous Alter Partition Clauses](non-heterogeneous-alter-partition-clauses-f7ae27c.md "Modifies the partitions of an existing table with a non-heterogeneous partitioning schema.")

[ALTER TABLE Statement \(Data Definition\)](alter-table-statement-data-definition-20d329a.md "Alters a base or temporary table. See the ALTER VIRTUAL TABLE statement for altering virtual tables.")

[Table Partitioning](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2024_1_QRC/en-US/c2ea130bbb571014b024ffeda5090764.html "The partitioning feature of the SAP HANA database splits column-store tables horizontally into disjunctive sub-tables or partitions. In this way, large tables can be broken down into smaller, more manageable parts. Partitioning is typically used in multiple-host systems, but it may also be beneficial in single-host systems.") :arrow_upper_right:

[Dynamic Range Partitioning](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2024_1_QRC/en-US/6ebea7782b9e4758baeed923e388ee32.html "Dynamic Range Partitioning is available to support the automatic maintenance of the OTHERS partition.") :arrow_upper_right:

[SAP HANA Native Storage Extension](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2024_1_QRC/en-US/4efaa94f8057425c8c7021da6fc2ddf5.html "SAP HANA native storage extension is a general-purpose, built-in warm data store in SAP HANA that lets you manage less-frequently accessed data without fully loading it into memory. It integrates disk-based or flash-drive based database technology with the SAP HANA in-memory database for an improved price-performance ratio.") :arrow_upper_right:

[TABLE\_PARTITIONS System View](../../020-System-Views-Reference/021-System-Views/table-partitions-system-view-c81d9be.md "Partition-specific information for partitioned tables.")

