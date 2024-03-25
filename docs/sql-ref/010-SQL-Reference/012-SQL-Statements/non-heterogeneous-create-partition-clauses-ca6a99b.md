<!-- loioca6a99bbfcd94be9ab8020a86f43caae -->

# Non-Heterogeneous Create Partition Clauses

Defines the various partitioning clauses available for non-heterogeneous partitions when creating a new table.




<dl>
<dt><b>

*<non\_heterogeneous\_partitions\>*

</b></dt>
<dd>

Partitions the table using a non-heterogeneous range, range-range, hash-range, hash-hash, or round-robin partitioning schema.

```
<non_heterogeneous_partitions> ::=
   { PARTITION BY <hash_partition> [ SUBPARTITION BY { <hash_partition> | <subrange_partition> } ]
     | PARTITION BY <range_partition> [ <subrange_partition> ] 
     | PARTITION BY <roundrobin_partition> [ <subrange_partition> ] }
   [ PRIMARY KEY UPDATE { ON | OFF } ]
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



</dd><dt><b>

*<part\_location\>*

</b></dt>
<dd>

Specifies the location of each HASH partition.

```
<part_location> ::= { AT LOCATION ( '<HANA_host>:<HANA_port>' } ]
```

If not specified, locations are assigned using round robin fashion.



</dd><dt><b>

*<part\_range\>*

</b></dt>
<dd>

Specifies the range specifications for a first-level range partition.

```
<part_range> ::= 
   PARTITION <range_values> [ <range_prop_list> ]
   [, PARTITION <range_values> [ <range_prop_list> ] [,...] ] 
```



</dd><dt><b>

*<part\_subrange\>*

</b></dt>
<dd>

Specifies the range specifications for a second-level range partition.

```
<part_subrange> ::= 
   PARTITION <range_values> [ <range_prop_list> ]
   [, PARTITION <range_values> [ <range_prop_list> ] [,...] ] 
```



</dd><dt><b>

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


<dl>
<dt><b>

DYNAMIC THRESHOLD *<threshold\_count\>*

</b></dt>
<dd>

The keyword DYNAMIC enables dynamic range partitioning on the table \(the default is inactive\) and THRESHOLD specifies the maximum row count in the partition before generating a new dynamic range partition from OTHERS or the priority for determining the maximum row count value. The THRESHOLD default, if not specified, is 10 000 000 \(10 million\) rows. You can define DYNAMIC on a single RANGE partition or on the second-level range of an X-RANGE partition. To enable dynamic range partitioning, the range column of OTHERS requires a NOT NULL constraint. For more information on dynamic range partitioning, see *Dynamic Range Partitioning*.



</dd>
</dl>



</dd>
</dl>


<dl>
<dt><b>

*<range\_prop\_list\>*

</b></dt>
<dd>

Specifies the properties for the partition.

```
<range_prop_list> ::= <range_prop> [ <range_prop> ...] ]

<range_prop> ::= 
   INSERT {OFF | ON}
   | AT [ LOCATION ] ( <location> )
   | <load_unit> 
   | <group_list>
   | <persistent_memory_spec_clause>
   | <numa_node_preference_clause>
```



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



</dd>
</dl>



<a name="loioca6a99bbfcd94be9ab8020a86f43caae__section_s45_55p_lgb"/>

## Description

Defines the various non-heterogeneous partitioning clauses available when creating a new table.



<a name="loioca6a99bbfcd94be9ab8020a86f43caae__section_qnd_xgv_lgb"/>

## Examples


<dl>
<dt><b>



</b></dt>
<dd>

Create a non-heterogeneous range partitioned table named P1 that has a DATE-type column A. Column U has a primary key constraint and is used as a range-partitioning column.

```
CREATE COLUMN TABLE P1 (A DATE PRIMARY KEY) PARTITION BY RANGE (A) 
   (PARTITION '2010-02-03' <= VALUES < '2011-01-01', PARTITION VALUE = '2011-05-01');
```

Create a non-heterogeneous hash partitioned table named P2, with primary key defined for columns A and B.

```
CREATE COLUMN TABLE P2 (A INT, B INT, C INT, PRIMARY KEY(A, B)) 
   PARTITION BY HASH (A, B) PARTITIONS 2;
```

Create a non-heterogeneous hash-hash partitioned table named P3, with primary key defined for columns A and B.

```
CREATE COLUMN TABLE P3 (A INT, B INT, C INT, PRIMARY KEY(A, B)) 
   PARTITION BY HASH (A, B) PARTITIONS 2 SUBPARTITION BY HASH (C) PARTITIONS 2;
```

Create a non-heterogeneous hash-range partitioned table named P4 where columns A and B define the hash partition and column C defines the range subpartition.

```
CREATE COLUMN TABLE P4 (A INT, B INT, C INT) PARTITION BY HASH (A, B) PARTITIONS 2 
   SUBPARTITION BY RANGE (C) (PARTITION 10 <= VALUES < 20);
```

Create a non-heterogeneous range-range partitioned table named P5. The OTHERS partition is defined on the first level. PERSISTENT MEMORY is enabled on both levels. The NUMA node preference is set on the first partition only.

```
CREATE COLUMN TABLE P5 (A INT, B INT) PARTITION BY RANGE (A) 
   (PARTITION 10 <= VALUES < 20 PERSISTENT MEMORY ON NUMA NODE ('3'), PARTITION OTHERS PERSISTENT MEMORY ON)
   SUBPARTITION BY RANGE (B) (PARTITION VALUES=100 PERSISTENT MEMORY ON);
```

Create a non-heterogeneous range-range partitioned table named 65 with dynamic range partitioning enabled.

```
CREATE COLUMN TABLE P6 (A INT, B INT NOT NULL) PARTITION BY RANGE (A) (PARTITION VALUES = 10) 
   SUBPARTITION BY RANGE (B) (PARTITION VALUES = 20, PARTITION OTHERS DYNAMIC THRESHOLD 2);
```



</dd>
</dl>

**Related Information**  


[Table Partitioning](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2024_1_QRC/en-US/c2ea130bbb571014b024ffeda5090764.html "The partitioning feature of the SAP HANA database splits column-store tables horizontally into disjunctive sub-tables or partitions. In this way, large tables can be broken down into smaller, more manageable parts. Partitioning is typically used in multiple-host systems, but it may also be beneficial in single-host systems.") :arrow_upper_right:

[CREATE TABLE Statement \(Data Definition\)](create-table-statement-data-definition-20d58a5.md "Creates a base or temporary table. See the CREATE VIRTUAL TABLE statement for creating virtual tables.")

[Heterogeneous Create Partition Clauses](heterogeneous-create-partition-clauses-d496e58.md "Defines the various partitioning clauses available for heterogeneous partitions when creating a new table.")

[Dynamic Range Partitioning](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2024_1_QRC/en-US/6ebea7782b9e4758baeed923e388ee32.html "Dynamic Range Partitioning is available to support the automatic maintenance of the OTHERS partition.") :arrow_upper_right:

[TABLE\_PARTITIONS System View](../../020-System-Views-Reference/021-System-Views/table-partitions-system-view-c81d9be.md "Partition-specific information for partitioned tables.")

