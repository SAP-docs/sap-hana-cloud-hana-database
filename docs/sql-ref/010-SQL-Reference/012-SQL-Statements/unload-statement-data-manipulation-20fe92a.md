<!-- loio20fe92a2751910148c38887562a97c5a -->

# UNLOAD Statement \(Data Manipulation\)

Unloads the column store table from memory.



<a name="loio20fe92a2751910148c38887562a97c5a__sql_unload_1sql_unload_syntax"/>

## Syntax

```
UNLOAD <table_name> [ { <partition_restriction> | <persistent_memory_clause> } ]
```



<a name="loio20fe92a2751910148c38887562a97c5a__sql_unload_1sql_load_syntax_elements"/>

## Syntax Elements


<dl>
<dt><b>

*<table\_name\>*

</b></dt>
<dd>

Unloads the specified table from memory.

```
<table_name> ::= [<schema_name>.]<identifier>

<schema_name> ::= <unicode_name>
```



</dd><dt><b>

*<partition\_restriction\>*

</b></dt>
<dd>

Unloads the specified partition\(s\) from memory. This option is supported for partitioned column store tables. For multistore tables, only partitions in default storage are supported.

```
<partition_restriction> ::=
 PARTITION ( <partition_number> [ <persistent_memory_clause> ] [, <partition_number> [ <persistent_memory_clause> ] [, ...] ] )
```

*<partition\_number\>* is the logical partition ID and is stored in the M\_CS\_PARTITIONS system view.

If *<partition\_restriction\>* is not specified, then all partitions are unloaded by default.



</dd><dt><b>

*<persistent\_memory\_clause\>*

</b></dt>
<dd>

Specifies whether persistent memory is deleted or retained when unloading a table.

```
<persistent_memory_clause> ::= { DELETE | RETAIN } PERSISTENT MEMORY
```

The default behavior is to retain the data files for real persistent memory and to delete the data files when persistent memory is configured on tmpfs.


<dl>
<dt><b>

DELETE

</b></dt>
<dd>

Deletes persistent memory for the column as part unloading the table.



</dd><dt><b>

RETAIN

</b></dt>
<dd>

Retains persistent memory for the column as part of unload table.



</dd>
</dl>



</dd>
</dl>



<a name="loio20fe92a2751910148c38887562a97c5a__sql_unload_1sql_unload_description"/>

## Description

To free up memory, use the UNLOAD statement to unload the column store table from memory. The table is loaded again on next access.

While the UNLOAD statement allows you to specify partitioned tables, the LOAD statement does not.

For more information on table partitioning, see the *SAP HANA Cloud, SAP HANA Database Administration Guide*.



<a name="loio20fe92a2751910148c38887562a97c5a__section_zp1_tnh_qbb"/>

## Permissions

You must have either the UPDATE privilege on the table or the system privilege TABLE ADMIN to execute the UNLOAD statement on a table.



<a name="loio20fe92a2751910148c38887562a97c5a__sql_unload_1sql_unload_examples"/>

## Example

Create column table A1.

```
CREATE COLUMN TABLE A1 (A INT, B INT);
```

Load table A1 into memory.

```
LOAD A1 all;
```

Unload table A1 from memory.

```
UNLOAD A1;
```

Check the load status of table A1.

```
SELECT loaded FROM m_cs_tables WHERE table_name = 'A1';
```

Delete persistent memory on partitions 1, but retain persistent memory on partition 2 when unloading g table A1.

```
UNLOAD A1 PARTITION (1 DELETE PERSISTENT MEMORY, 2 RETAIN PERSISTENT MEMORY);
```

Delete all persistent memory when unloading g table A1.

```
UNLOAD A1 DELETE PERSISTENT MEMORY;
```

**Related Information**  


[Table Partitioning](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2024_3_QRC/en-US/c2ea130bbb571014b024ffeda5090764.html "The partitioning feature of the SAP HANA database splits column-store tables horizontally into disjunctive sub-tables or partitions. In this way, large tables can be broken down into smaller, more manageable parts. Partitioning is typically used in multiple-host systems, but it may also be beneficial in single-host systems.") :arrow_upper_right:

