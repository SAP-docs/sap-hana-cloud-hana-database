<!-- loiod496e58ce9b54bac9674beda4a636946 -->

# Heterogeneous Create Partition Clauses

Defines the various partitioning clauses available for heterogeneous partitions when creating a new table.




<dl>
<dt><b>

*<heterogeneous\_partitions\>*

</b></dt>
<dd>

Partitions the new table using a heterogeneous range, range-range, or range-hash partitioning scheme. For more information on partitioning schema, see *Table Partitioning* in the *SAP HANA Cloud, SAP HANA Database Administration Guide*.

```
<heterogeneous_partitions> ::= PARTITION BY RANGE ( <partition_expression> )
   [ [ NO ] PRIMARY KEY CHECK ] ( <part_spec> [, <part_spec> [,...] ] )
   [ PRIMARY KEY UPDATE { ON | OFF } ]

<part_spec> ::= 
   { ( <part_range> [, <part_range> [,...] ) ] [ <subpart_by_clause> ] 
   | ( <part_range> ) [ <subpart_by_clause> ] }

<subpart_by_clause> ::= SUBPARTITION BY { <sub_part_range> | <sub_part_hash> }
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



</dd><dt><b>

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

Specifies the range for the first- or second-level partition.

```
<part_range> ::= PARTITION <range_values> [ <range_prop_list> ]
```



</dd><dt><b>

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
OTHERS [ DYNAMIC [ {THRESHOLD <threshold_count> ] ] | [ DYNAMIC INTERVAL <interval> ]
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

*<sub\_range\_col\_def\>*

</b></dt>
<dd>

Specifies the subpartitioning column. If this is the first subpartition in the partitioned table, then specify *<partition\_expression\>*. For all subsequent range subpartitions added or referenced, specify *<exist\_subpart\_col\_name\>*, the name of the existing range subpartitioning column.



</dd>
</dl>



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

Specifies where the partitions reside.

```
<loc_list> ::= <location> [, <location> [,...] ]

<location> ::= '<HANA_host>:<HANA_port>'
```



</dd>
</dl>



</dd><dt><b>

PRIMARY KEY UPDATE \{ ON | OFF \}

</b></dt>
<dd>

Specifies if UPDATE statements are allowed on primary key columns.



</dd>
</dl>



</dd>
</dl>



<a name="loiod496e58ce9b54bac9674beda4a636946__section_s45_55p_lgb"/>

## Description

Defines the various heterogeneous partitioning clauses available when creating a new table.Specifies if UPDATE statements are allowed on primary key columns. If not specified, then the default is ON.



<a name="loiod496e58ce9b54bac9674beda4a636946__section_qnd_xgv_lgb"/>

## Examples


<dl>
<dt><b>



</b></dt>
<dd>

Create a single level range partitioned heterogeneous table. This table has no subpartitions defined.

```
CREATE COLUMN TABLE A1 (I INT, J INT, K INT, PRIMARY KEY(I, J)) 
   PARTITION BY RANGE (I) ((PARTITION 10 <= VALUES < 20, PARTITION 20 <= VALUES < 30));
```

Create a multi-level range-range partitioned heterogeneous table.

```
CREATE COLUMN TABLE A2 (I INT, J INT, K INT, PRIMARY KEY(I, J)) 
   PARTITION BY RANGE (I) ((PARTITION 10 <= VALUES < 20, PARTITION 20 <= VALUES < 30)
      SUBPARTITION BY RANGE (J) (PARTITION 100 <= VALUES < 150, PARTITION VALUE = 200));
```

Create a heterogeneous multi-level partitioned table. The table has three first-level partitions. The first partition has the ranges 10-20 and 20-30. The second partition has the target value 40. The final partition is OTHERS for any values outside the scope of the first to partitions. The first two partitions each have a subpartition defined. Each range or target value of the first-level partitions has its own properties defined. The two subpartitions are same type \(range\) and reference the same column \(B\). The subpartitions also have dynamic range partitioning enabled.

```
CREATE COLUMN TABLE A3 (A INT, B INT NOT NULL, C INT) PARTITION BY RANGE (A)
   ((PARTITION 10 <= VALUES < 20 GROUP NAME 'GRP 1' INSERT OFF, PARTITION 20 <= VALUES < 30 GROUP NAME 'GRP 1' INSERT OFF) 
      SUBPARTITION BY RANGE(B) (PARTITION 0 <= VALUES < 10 PAGE LOADABLE GROUP SUBTYPE 'GRP 1a', PARTITION 10 <= VALUES < 
           100 GROUP SUBTYPE 'GRP 1b' INSERT OFF PAGE LOADABLE, PARTITION OTHERS DYNAMIC THRESHOLD 2),
    (PARTITION VALUES = 40 GROUP NAME 'GRP 2' INSERT OFF COLUMN LOADABLE)
      SUBPARTITION BY RANGE(B) (PARTITION 0 <= VALUES < 10 GROUP SUBTYPE 'GRP 2a', PARTITION OTHERS DYNAMIC THRESHOLD 2),
    (PARTITION OTHERS));

```

Create a heterogeneous partitioned table with dynamic range partitioning enabled. This table has two first-level ranges. The first partition has a range of 10-20. The second partition has a target value of 30. Each partition has it own subpartition. The first subpartition has a range of 100-150. The second subpartition has a target value of 200. Both subpartitions have dynamic range partitioning enabled with a threshold of 3.

```
CREATE COLUMN TABLE T4 (A INT, B INT NOT NULL) PARTITION BY RANGE (A)
   ((PARTITION 10 <= VALUES < 20) SUBPARTITION BY RANGE (B) (PARTITION 100 <= VALUES < 150, PARTITION OTHERS DYNAMIC THRESHOLD 3),
    (PARTITION VALUES = 30) SUBPARTITION BY RANGE (B) (PARTITION VALUES = 200, PARTITION OTHERS DYNAMIC THRESHOLD 3));
```

Create a heterogeneous partitioned table. There are three first-level \(10-20, 30, and 40-50\), each with different properties defined. The first two partitions share the same subpartition. There are two second-level hash partitions, each referencing the same group of columns \(A, C\). On the first subpartition, column A has a DATE data type, with the precision YEAR applied at the subpartition level.

```
CREATE COLUMN TABLE A5 (A DATE, B INT, C INT) PARTITION BY RANGE (B) 
   ((PARTITION 10 <= VALUES < 20 INSERT ON PAGE LOADABLE, PARTITION VALUES = 30 COLUMN LOADABLE GROUP NAME 'HR') 
       SUBPARTITION BY HASH (YEAR(a), c) PARTITIONS 4,
    (PARTITION 40 <= VALUES < 50 PAGE LOADABLE GROUP NAME 'HR') 
       SUBPARTITION BY HASH (YEAR(a), c) PARTITIONS 4);
```



</dd>
</dl>

**Related Information**  


[Table Partitioning](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2023_4_QRC/en-US/c2ea130bbb571014b024ffeda5090764.html "The partitioning feature of the SAP HANA database splits column-store tables horizontally into disjunctive sub-tables or partitions. In this way, large tables can be broken down into smaller, more manageable parts. Partitioning is typically used in multiple-host systems, but it may also be beneficial in single-host systems.") :arrow_upper_right:

[CREATE TABLE Statement \(Data Definition\)](create-table-statement-data-definition-20d58a5.md "Creates a base or temporary table. See the CREATE VIRTUAL TABLE statement for creating virtual tables.")

[Non-Heterogeneous Create Partition Clauses](non-heterogeneous-create-partition-clauses-ca6a99b.md "Defines the various partitioning clauses available for non-heterogeneous partitions when creating a new table.")

[Dynamic Range Partitioning](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2023_4_QRC/en-US/6ebea7782b9e4758baeed923e388ee32.html "Dynamic Range Partitioning is available to support the automatic maintenance of the OTHERS partition.") :arrow_upper_right:

[SAP HANA Native Storage Extension](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2023_4_QRC/en-US/4efaa94f8057425c8c7021da6fc2ddf5.html "SAP HANA native storage extension is a general-purpose, built-in warm data store in SAP HANA that lets you manage less-frequently accessed data without fully loading it into memory. It integrates disk-based or flash-drive based database technology with the SAP HANA in-memory database for an improved price-performance ratio.") :arrow_upper_right:

[TABLE\_PARTITIONS System View](../../020-System-Views-Reference/021-System-Views/table-partitions-system-view-c81d9be.md "Partition-specific information for partitioned tables.")

