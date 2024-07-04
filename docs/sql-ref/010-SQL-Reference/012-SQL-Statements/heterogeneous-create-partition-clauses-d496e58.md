<!-- loiod496e58ce9b54bac9674beda4a636946 -->

# Heterogeneous Create Partition Clauses

Defines the various partitioning clauses available for heterogeneous partitions when creating a new table.




<dl>
<dt><b>

*<heterogeneous\_partitions\>*

</b></dt>
<dd>

Partitions the new table using a heterogeneous range. Partitions can be up to three levels, using one of the following schemas: RANGE-RANGE, RANGE-HASH, RANGE-RANGE-RANGE, or RANGE-RANGE-HASH. For more information on partitioning schema, see *Table Partitioning* in the *SAP HANA Cloud, SAP HANA Database Administration Guide*.

```
<heterogeneous_partitions> ::= 
   PARTITION BY RANGE ( <partition_expression> )
   [ [ NO ] PRIMARY KEY CHECK ] ( <part_spec> [, <part_spec> [,...] ] )
   [ DYNAMIC RANGE CHECK INTERVAL <dynamic_check_interval> ]

<part_spec> ::= 
   ( <part_range> [, <part_range> [,...] ] ) [ <subpart1_by_clause> [ <subpart2_by_clause> ] ]
```

All subpartitions of a common level must be of the same type and reference the same column or in the case of a hash subpartition the same group of columns. For example, if the first-level subpartition is RANGE using column B, then all additional first-level subpartitions must be RANGE using column B. If the first-level subpartition is HASH, referencing columns B and C, then all first-level subpartitions must be HASH referencing the same group of columns. The same column reference cannot be used on different subpartition levels regardless of type. For example, if PARTITION BY RANGE *<partition\_expression\>* references column A, then neither *<subpart1\_by\_clause\>* or *<subpart2\_by\_clause\>* can reference column A. If *<subpart1\_by\_clause\>* references column B, then *<subpart2\_by\_clause\>* can't reference column A or B.


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

Specifies the range for the first-, second-, or third-level partition.

```
<part_range> ::= PARTITION <range_values> [ <range_prop_list> ]
```



</dd><dt><b>

*<range\_values\>*

</b></dt>
<dd>

Specifies the values of the range partition.

```
<range_values> ::= 
   { <min_value> <= VALUES < <max_value>
   | VALUE[S] = <target_value>
   | <partition_others> }
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




<dl>
<dt><b>

*<dynamic\_direction\>*

</b></dt>
<dd>

Specifies the direction in which dynamic range generates new range partitions.

```
<dynamic_direction> ::=
   { BIDIRECTIONAL
   | DECREASING
   | INCREASING }
```

DECREASING generates new range partitions towards negative infinity. BIDIRECTIONAL generates new range partitions towards both negative infinity and positive infinity. If not specified, then INCREASING \(default\) is used to generate new range partitions towards positive infinity.



</dd><dt><b>

*<dynamic\_threshold\_count\>*

</b></dt>
<dd>

The keyword DYNAMIC enables dynamic range partitioning on the table \(default is inactive\) and THRESHOLD specifies the maximum row count in the partition before generating a new dynamic range partition from OTHERS or the priority for determining the maximum row count value. The THRESHOLD default, if not specified, is 100 000 000 rows. You can only define DYNAMIC on a single range partition or on any range subpartition. For more information on dynamic range partitioning, see *Dynamic Range Partitioning*.



</dd><dt><b>

*<dynamic\_interval\>*

</b></dt>
<dd>

Specifies a dynamic interval for the range OTHERS partition. The interval is between the last range partition and new partition created dynamically.

```
<dynamic_interval> ::= <interval_value> <interval_type>

<interval_value>  ::= <unsigned_integer>
<interval_type> ::= [ YEAR | MONTH | HOUR ]
```

Dynamic interval is only supported when the partition column type is TINYINT, SMALLINT, INT, BIGINT, DATE, SECONDDATE or LONGDATE. If no *<interval\_type\>* is specified, INT is used implicitly.



</dd><dt><b>

*<distance\_interval\>*

</b></dt>
<dd>

Calculates the distance of each partition by comparing with the maximum value of the partition group. If it is equal to or greater than the preset distance, then dynamic aging deems it to be a warm partition and converts the partition into PAGE LOADABLE. The criteria to convert a partition to PAGE LOADABLE is:

-   The partition's load unit property is not explicit COLUMN LOADABLE.
-   The partition does not derive COLUMN LOADABLE from its parent partitions or table.
-   The partition does not have sub partitions.
-   The partition contains data. If it's empty but its next partition is deemed to be warm partition, then it is still be converted.
-   The calculated distance \>= the preset distance threshold.



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
   { INSERT {OFF | ON}
   | AT [ LOCATION ] ( <location> )
   | <load_unit><group_list>
   | <persistent_memory_spec>
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

If not specified, then the value is inherited from its parent partitions \(from near to far\). If none of the parents have the move property explicitly set, then the table-level movable property value is used. If none of these apply, then the partition is movable by default.



</dd>
</dl>



</dd><dt><b>

*<subpart1\_by\_clause\>*

</b></dt>
<dd>

Specifies a range or hash subpartition.

```
<subpart1_by_clause> ::= 
   SUBPARTITION BY { <subpart1_range> | <subpart1_hash> }
```


<dl>
<dt><b>

*<subpart1\_range\>*

</b></dt>
<dd>

Specifies the first-level range subpartition.

```
<subpart1_range> ::= 
   RANGE ( <sub_range_lev1_col_def> ) ( <part_range> [, <part_range> [,...] ] [ <subpart2_by_clause> ] )
```


<dl>
<dt><b>

*<sub\_range\_lev1\_col\_def\>*

</b></dt>
<dd>

Specifies the referencing column for the initial first-level subpartition. For all subsequent first-level subpartitions, specify the column defined for the initial first-level subpartition.



</dd>
</dl>


<dl>
<dt><b>

*<subpart2\_by\_clause\>*

</b></dt>
<dd>

Specifies the second-level subpartition type. It can be a RANGE or HASH subpartition.

```
<subpart2_by_clause> ::= 
   SUBPARTITION BY { <subpart2_range> | <subpart2_hash>
```


<dl>
<dt><b>

*<subpart2\_range\>*

</b></dt>
<dd>

```
<subpart2_range> ::= 
      RANGE ( <subpart_lev2_col_def> ) ( <part_range> [, <part_range> [,...] ] )
```



</dd><dt><b>

*<subpart\_lev2\_col\_def\>*

</b></dt>
<dd>

Specifies the referencing column for the initial second-level subpartition. For all subsequent second-level subpartitions, specify the column defined for the initial second-level subpartition.



</dd><dt><b>

*<subpart2\_hash\>*

</b></dt>
<dd>

Specifies the second-level hash subpartition.

```
<subpart2_hash> ::= 
   HASH ( <subpart_lev2_col_def> ) PARTITIONS <num_partitions> [ AT [ LOCATION ] ( <loc_list_lev2> ) ]

```



</dd><dt><b>

*<loc\_list\_lev2\>*

</b></dt>
<dd>

Specifies where the partitions reside.

```
<loc_list_lev2> ::= <location> [, <location> [,...] ]

<location> ::= '<HANA_host>:<HANA_port>'
```



</dd>
</dl>



</dd>
</dl>



</dd><dt><b>

*<subpart1\_hash\>*

</b></dt>
<dd>

Specifies the first-level hash subpartition.

```
<subpart1_hash> ::= 
   HASH ( <subpart_lev1_col_def> ) PARTITIONS <num_partitions> [ AT [ LOCATION ] ( <loc_list> ) ]
```

With the exception of LOCATION, all hash partitions share the same properties.


<dl>
<dt><b>

*<subpart\_lev1\_col\_def\>*

</b></dt>
<dd>

Specifies the referencing column for the initial first-level subpartition. For all subsequent first-level subpartitions, specify the column defined for the initial first-level subpartition.



</dd><dt><b>

*<loc\_list\_lev1\>*

</b></dt>
<dd>

Specifies where the partitions reside.

```
<loc_list_lev1> ::= <location> [, <location> [,...] ]

<location> ::= '<HANA_host>:<HANA_port>'
```



</dd>
</dl>



</dd>
</dl>



</dd><dt><b>

*<dynamic\_check\_interval\>*

</b></dt>
<dd>

Specifies the interval, in minutes, for the minimum background dynamic range trigger interval on the table. The valid range is 1-1440000. Set to 0 to disable the background dynamic range trigger on this table until the property is unset, or reset with a new value. If not set, it uses the global background dynamic range trigger interval, which has a default value 15 minutes.



</dd>
</dl>



</dd>
</dl>



<a name="loiod496e58ce9b54bac9674beda4a636946__section_s45_55p_lgb"/>

## Description

Defines the various heterogeneous partitioning clauses available when creating a new table.



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

Create a multilevel heterogeneous partitioned table and then applies the *<load\_unit\>* attribute first by partition number \(1\) and then to partition range \(10 to 20\).

```
CREATE COLUMN TABLE T6 (a INT, b INT) PARTITION BY RANGE(a) 
   ((PARTITION 10 <= VALUES < 20) SUBPARTITION BY RANGE (b) (PARTITION VALUES=100));

ALTER TABLE T4 ALTER PARTITION 1 COLUMN LOADABLE;
ALTER TABLE T4 ALTER PARTITION RANGE (a) ((PARTITION 10 <= VALUES < 20) 
   SUBPARTITION BY RANGE (b) (PARTITION VALUES = 100)) PAGE LOADABLE;
```

Creates a heterogeneous partitioned table with a dynamic distance interval of 200.

```
CREATE TABLE A7 (A int NOT NULL, B int) PARTITION BY RANGE (A) (
  PARTITION 1 <= VALUES < 100,
  PARTITION 100 <= VALUES < 200,
  PARTITION OTHERS DYNAMIC DISTANCE 200 PAGE LOADABLE);
```

Creates a table with decreasing numbered dynamic ranges.

```
CREATE TABLE A8 (C1 INT NOT NULL) PARTITION BY RANGE (C1) (
  PARTITION OTHERS DYNAMIC DECREASING THRESHOLD 2);
```

Creates a table with dynamic range numbers that both increase and decrease.

```
CREATE TABLE A9 (C1 INT NOT NULL) PARTITION BY RANGE (C1) (
  PARTITION OTHERS DYNAMIC BIDIRECTIONAL INTERVAL 2);
```

Create a dynamic range table with a check interval of 20 minutes:

```
CREATE TABLE A10 (C1 INT NOT NULL) PARTITION BY RANGE (C1) (
  (PARTITION 1 <= VALUES < 100, PARTITION OTHERS DYNAMIC INTERVAL 10)) DYNAMIC RANGE CHECK INTERVAL 20;
```

Created a partitioned table with some partitions movable and some not.

```
CREATE COLUMN TABLE A11 (C1 INT, C2 INT) PARTITION BY RANGE (C1) (
  (PARTITION VALUE = 1) SUBPARTITION BY RANGE (C2) (PARTITION VALUE = 1, PARTITION VALUE = 2 MOVABLE, PARTITION VALUE = 3 NOT MOVABLE),
  (PARTITION VALUE = 2 MOVABLE) SUBPARTITION BY RANGE (C2) (PARTITION VALUE = 1, PARTITION VALUE = 2 MOVABLE, PARTITION VALUE = 3 NOT MOVABLE),
  (PARTITION VALUE = 3 NOT MOVABLE) SUBPARTITION BY RANGE (C2) (PARTITION VALUE = 1, PARTITION VALUE = 2 MOVABLE, PARTITION VALUE = 3 NOT MOVABLE)
  );
```

Create a heterogeneous partitioned table with a distance of 200.

```
CREATE TABLE A6 (C1 INT NOT NULL, C2 INT) PARTITION BY RANGE (C1) 
   ((PARTITION 1 <= VALUES < 100, PARTITION 100 <= VALUES < 200, PARTITION OTHERS DYNAMIC DISTANCE 200 PAGE LOADABLE ));
```



</dd>
</dl>

**Related Information**  


[Table Partitioning](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2024_3_QRC/en-US/c2ea130bbb571014b024ffeda5090764.html "The partitioning feature of the SAP HANA database splits column-store tables horizontally into disjunctive sub-tables or partitions. In this way, large tables can be broken down into smaller, more manageable parts. Partitioning is typically used in multiple-host systems, but it may also be beneficial in single-host systems.") :arrow_upper_right:

[CREATE TABLE Statement \(Data Definition\)](create-table-statement-data-definition-20d58a5.md "Creates a base or temporary table. See the CREATE VIRTUAL TABLE statement for creating virtual tables.")

[Non-Heterogeneous Create Partition Clauses](non-heterogeneous-create-partition-clauses-ca6a99b.md "Defines the various partitioning clauses available for non-heterogeneous partitions when creating a new table.")

[Dynamic Range Partitioning](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2024_3_QRC/en-US/6ebea7782b9e4758baeed923e388ee32.html "For heterogeneous partitioning schemas dynamic range partitioning is available to support the automatic maintenance of the OTHERS partition.") :arrow_upper_right:

[SAP HANA Native Storage Extension](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2024_3_QRC/en-US/4efaa94f8057425c8c7021da6fc2ddf5.html "SAP HANA native storage extension is a general-purpose, built-in warm data store in SAP HANA that lets you manage less-frequently accessed data without fully loading it into memory. It integrates disk-based or flash-drive based database technology with the SAP HANA in-memory database for an improved price-performance ratio.") :arrow_upper_right:

[TABLE\_PARTITIONS System View](../../020-System-Views-Reference/021-System-Views/table-partitions-system-view-c81d9be.md "Partition-specific information for partitioned tables.")

