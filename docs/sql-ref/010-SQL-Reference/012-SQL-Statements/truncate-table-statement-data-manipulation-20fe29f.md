<!-- loio20fe29f0751910149904f0c5c3201cfa -->

# TRUNCATE TABLE Statement \(Data Manipulation\)

Deletes all rows from a table or projection view.



<a name="loio20fe29f0751910149904f0c5c3201cfa__sql_truncate_table_1sql_truncate_table_syntax"/>

## Syntax

```
TRUNCATE TABLE <table_name> [ PARTITION 
   { ( <partition_list> )
   | <truncate_partition_spec> } ]
```



<a name="loio20fe29f0751910149904f0c5c3201cfa__sql_truncate_table_1sql_truncate_table_syntax_elements"/>

## Syntax Elements


<dl>
<dt><b>

*<table\_name\>*

</b></dt>
<dd>

Specifies the name of a table or projection view.

```
<table_name> ::= [[<database_name>.]<schema_name>.]<identifier>

<schema_name> ::= <unicode_name>
```

For linked database, *<database\_name\>* is the name of the remote source. *<identifier\>* is the name of the table on the remote source.



</dd><dt><b>

*<partition\_list\>*

</b></dt>
<dd>

Specifies the list of logical partition IDs of the partitions to truncate.

```
<partition_list> ::= <partition_id> [, <partition_list>]

<partition_id> ::= <unsigned_integer>
```

This can be done only for column store tables. Partitions in remote tables \(those from a different tenant\) and replicated tables \(with either an OSTR/ATR replica\) cannot be truncated.

Logical partition IDs are listed in the PART\_ID column in TABLE\_PARTITIONS.



</dd><dt><b>

*<truncate\_partition\_spec\>*

</b></dt>
<dd>

```
<truncate_partition_spec> ::=
   RANGE (<exist_part_column_name> ) 
            ( ( <part_range_list> ) [ SUBPARTITION BY { <sub_part_range> | <sub_part_hash> } ] )

<part_range_list> ::= part_range [, <part_range> [,...] ]
```


<dl>
<dt><b>

*<part\_range\>*

</b></dt>
<dd>

Specifies the range for the first- or second-level range partition.

```
<part_range> ::= PARTITION <range_values>
```


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



</dd>
</dl>



</dd>
</dl>


<dl>
<dt><b>

*<sub\_part\_range\>*

</b></dt>
<dd>

Specifies the range subpartition.

```
<sub_part_range> ::= RANGE ( <sub_range_col_def> ) ( <part_range> [, <part_range> [,...] ] )

<sub_range_col_def> ::= { <exist_subpart_col_name> | <partition_expression> }
```

All subpartitions must be of the same type and reference the same column or in the case of a hash subpartition the same group of columns. Mixed range and hash subpartitions are not supported. If the first subpartition is a range using column B, then all additional subpartition must be ranges using column B. If the first subpartition is a hash, referencing columns B and C, then all subpartitions must hash referencing the same group of column.s


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
</dl>


<dl>
<dt><b>

*<sub\_part\_hash\>*

</b></dt>
<dd>

Specifies the hash subpartition.

```
<sub_part_hash> ::= HASH ( <sub_hash_col_def> ) PARTITIONS <num_partitions>

<sub_hash_col_def> ::= { <exist_col_grp_list> | <partition_expression> [,<partition_expression> [,...] ] }
```

All subpartitions must be of the same type and reference the same column or in the case of a hash subpartition the same group of columns. Mixed range and hash subpartitions are not supported. If the first subpartition is a range using column B, then all additional subpartition must be ranges using column B. If the first subpartition is a hash, referencing columns B and C, then all subpartitions must hash referencing the same group of columns. All hash partitions share the same properties.



</dd>
</dl>



</dd>
</dl>



<a name="loio20fe29f0751910149904f0c5c3201cfa__sql_truncate_table_1sql_truncate_table_description"/>

## Description

TRUNCATE TABLE is faster than DELETE FROM when deleting all records from a table, but TRUNCATE TABLE cannot be rolled back. To roll back from record deletion, use the DELETE statement.

TRUNCATE TABLE causes an implicit commit.

TRUNCATE TABLE is also supported in DDL auto commit mode OFF, except for local and global temporary column tables. A TRUNCATE TABLE on temporary column tables cannot be rolled back, but it does not commit changes on other database objects.

In the documentation, TRUNCATE TABLE is included with the DML statements because its purpose is to delete table data and users typically associate it with a DML statement. However, TRUNCATE TABLE behaves as a DDL statement \(that is, it causes an implicit commit\) if run when the transaction mode AUTOCOMMIT DDL is set to ON \(SET TRANSACTION statement\).

SQLScript transactions normally run in AUTOCOMMIT DDL OFF, so an implicit commit is not performed for TRUNCATE TABLE.

TRUNCATE TABLE is allowed on a history table associated with a system-versioned table. When you execute a TRUNCATE TABLE statement on the system-versioned table, truncated records are not archived in the associated history table.



<a name="loio20fe29f0751910149904f0c5c3201cfa__sql_truncate_table_1sql_truncate_table_examples"/>

## Example

Create table A.

```
CREATE ROW TABLE A (A INT PRIMARY KEY, B INT);
```

Truncate the contents of table A.

```
TRUNCATE TABLE A;
```

Create table T1.

```
CREATE COLUMN TABLE T1 (A INT,B INT)
PARTITION BY RANGE (A) ((PARTITION 1 <= VALUES < 5, PARTITION 5 <= VALUES < 20, PARTITION OTHERS)
SUBPARTITION BY RANGE (B) (PARTITION 1 <= VALUES < 100, PARTITION 100 <= VALUES < 200));

```

Truncate logical partitions 2 and 3.

```
TRUNCATE TABLE T1 PARTITION (2,3);
```

**Related Information**  


[DELETE Statement \(Data Manipulation\)](delete-statement-data-manipulation-20d6169.md "Deletes records from a table where a specified condition is met.")

[Truncating Partitions](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2023_4_QRC/en-US/006600b969204574b90c6746ca27a394.html "You can use the SQL TRUNCATE statement to delete the content of specific partitions of a table.") :arrow_upper_right:

[TABLE\_PARTITIONS System View](../../020-System-Views-Reference/021-System-Views/table-partitions-system-view-c81d9be.md "Partition-specific information for partitioned tables.")

