<!-- loiod2353ea5d2951014bb61c0df540ffc42 -->

# TABLE\_REPLICAS System View

Provides information about replicated tables and their replicas.



<a name="loiod2353ea5d2951014bb61c0df540ffc42___t_a_b_l_e__r_e_p_l_i_c_a_s_1struct_TABLE_REPLICAS"/>

## Structure


<table>
<tr>
<th valign="top">

Column name

</th>
<th valign="top">

Data type

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

SCHEMA\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the schema name.

</td>
</tr>
<tr>
<td valign="top">

SOURCE\_TABLE\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the source table name.

</td>
</tr>
<tr>
<td valign="top">

SOURCE\_TABLE\_TYPE

</td>
<td valign="top">

NVARCHAR\(16\)

</td>
<td valign="top">

Displays the source table type.

</td>
</tr>
<tr>
<td valign="top">

REPLICA\_SCHEMA\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the replica schema name.

</td>
</tr>
<tr>
<td valign="top">

REPLICA\_TABLE\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the replica name.

</td>
</tr>
<tr>
<td valign="top">

REPLICA\_TABLE\_TYPE

</td>
<td valign="top">

NVARCHAR\(16\)

</td>
<td valign="top">

Displays the replica table type.

</td>
</tr>
<tr>
<td valign="top">

REPLICA\_TYPE

</td>
<td valign="top">

NVARCHAR\(16\)

</td>
<td valign="top">

Displays the replica type.

</td>
</tr>
<tr>
<td valign="top">

HAS\_DIFFERENT\_PARTITIONS

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether the replica table has different partitions from the source table.

</td>
</tr>
<tr>
<td valign="top">

HAS\_DIFFERENT\_COLUMNS

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether the replica table has different columns from the source table.

</td>
</tr>
</table>



<a name="loiod2353ea5d2951014bb61c0df540ffc42__section_cmt_kxz_2zb"/>

## Permissions

Unless otherwise specified, system views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all system views and their data regardless of the PUBLIC role and privilege grants.

**Related Information**  


[ALTER SYSTEM \{ENABLE | DISABLE\} ALL \[ASYNCHRONOUS | SYNCHRONOUS\] TABLE REPLICAS Statement \(System Management\)](../../010-SQL-Reference/012-SQL-Statements/alter-system-enable-disable-all-asynchronous-synchronous-table-replicas-stat-f948665.md "Activates or deactivates the overall replication operation of all replication tables or of asynchronous or synchronous tables only.")

[M\_TABLE\_REPLICAS System View](../022-Monitoring-Views/m-table-replicas-system-view-9f8f350.md "This document provides detailed information on both synchronous and asynchronous table replicas. Remote table replication should be shown only in M_REMOTE_TABLE_REPLICAS.")

[M\_TABLE\_REPLICAS\_RESET System View](../022-Monitoring-Views/m-table-replicas-reset-system-view-66d9c9d.md "Provides detailed information on asynchronous/synchronous table replicas.")

[Table Replication](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2024_3_QRC/en-US/33dd5d248add4b7a8c085846748b80ba.html "In a scale-out system tables (or selected columns of column store tables) may be replicated to multiple hosts. This can help to reduce network traffic when, for example, slowly-changing master data often has to be joined with tables, or partitions of tables, that are located on other hosts.") :arrow_upper_right:

[Operations for Asynchronous Table Replication](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2024_3_QRC/en-US/5d469886636248ddb5414afb11fbce20.html "There are a number of operations you can perform on replica tables such as querying, adding, deactivating, dropping, and monitoring tables.") :arrow_upper_right:

[Configure Asynchronous Table Replication](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2024_3_QRC/en-US/f47260743ed145558c515f9106a0319c.html "To set up asynchronous table replication you create a replica schema, create replica tables, handle large column store tables and activate replication on the system.") :arrow_upper_right:

[Table Replication Limitations](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2024_3_QRC/en-US/7683a6b0e9f649808cb956cd50087c5f.html "General restrictions that apply to the use of table replication.") :arrow_upper_right:

[Asynchronous Table Replication](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2024_3_QRC/en-US/604ac507d6494e9eb70e5256220c5018.html "Asynchronous table replication can help reduce workload on hosts by balancing load across replica tables on worker hosts in a distributed SAP HANA system.") :arrow_upper_right:

[Synchronous Table Replication](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2024_3_QRC/en-US/6173b69c6a5343e0b4a1a8b21cb504fb.html "With synchronous table replication the source and replica are always synchronized, this is therefore a more transparent solution.") :arrow_upper_right:

[Row to Column Table Replication](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2024_3_QRC/en-US/9e93b74902684b4291304f2fac5590ce.html "You can replicate data from row store tables to column store replicas, for mixed data types this may give optimal performance.") :arrow_upper_right:

[Configure Synchronous Table Replication](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2024_3_QRC/en-US/5532ba76350543c7867e91c266056025.html "You can configure synchronous replication using the SQL editor simply by adding replica tables.") :arrow_upper_right:

[Table Placement Rules for Replicas](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2024_3_QRC/en-US/266f9d2a727148f586d7bfb2a0cc4df8.html "The following SQL commands create table placement rules for replica schema, which can be used to create or add replica tables.") :arrow_upper_right:

[Operations for Synchronous Replication](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2024_3_QRC/en-US/9bb41349f18c40e1bbe5b38b2ff63227.html "There are a number of operations you can perform for synchronous replication such as activating or deactivating replication, and dropping replica tables.") :arrow_upper_right:

