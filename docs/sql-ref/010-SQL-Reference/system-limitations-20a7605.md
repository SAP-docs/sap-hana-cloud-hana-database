<!-- loio20a760537519101497e3cfe07b348f3c -->

# System Limitations

Limitations to take into consideration when administering an SAP HANA Cloud database.



Aside from the table below, most system limits can also be viewed by querying the M\_SYSTEM\_LIMITS system view \(`SELECT * FROM M_SYSTEM_LIMITS;`\). However, your values might differ depending on the hardware and software configuration your system uses.


<table>
<tr>
<td valign="top">

**Limitation Area** 

</td>
<td valign="top">

**Limit** 

</td>
<td valign="top">

**M\_SYSTEM\_LIMITS view name for the limitation** 

</td>
</tr>
<tr>
<td valign="top">

Database size limit

</td>
<td valign="top">

Row Store: 1,945 GB

Column Store: Dependent on size of physical memory

</td>
<td valign="top">

MAXIMUM\_SIZE\_OF\_ROW\_STORE

</td>
</tr>
<tr>
<td valign="top">

Number of locks

</td>
<td valign="top">

Unlimited for record locks,

16,383 for table locks

</td>
<td valign="top">

MAXIMUM\_NUMBER\_OF\_TABLE\_LOCKS

</td>
</tr>
<tr>
<td valign="top">

Number of simultaneous connections to the SAP HANA database

</td>
<td valign="top">

500 \* number of vCPUs, to a maximum of 30,000

</td>
<td valign="top">

MAXIMUM\_NUMBER\_OF\_SESSIONS

</td>
</tr>
<tr>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

**Schema Limitations** 

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Number of schemas per SAP HANA instance

</td>
<td valign="top">

Maximum value of BIGINT data type

</td>
<td valign="top">



</td>
</tr>
<tr>
<td valign="top">

Identifier length

</td>
<td valign="top">

127 bytes

</td>
<td valign="top">

MAXIMUM\_LENGTH\_OF\_IDENTIFIER

</td>
</tr>
<tr>
<td valign="top">

Length of an alias name

</td>
<td valign="top">

128 characters

</td>
<td valign="top">

MAXIMUM\_LENGTH\_OF\_ALIAS\_NAME

</td>
</tr>
<tr>
<td valign="top">

Table name length

</td>
<td valign="top">

Same as Identifier length

</td>
<td valign="top">

MAXIMUM\_LENGTH\_OF\_IDENTIFIER

</td>
</tr>
<tr>
<td valign="top">

Column name length

</td>
<td valign="top">

Same as Identifier length

</td>
<td valign="top">

MAXIMUM\_LENGTH\_OF\_IDENTIFIER

</td>
</tr>
<tr>
<td valign="top">

Length of a string literal

</td>
<td valign="top">

8 MB

</td>
<td valign="top">

MAXIMUM\_LENGTH\_OF\_STRING\_LITERAL

</td>
</tr>
<tr>
<td valign="top">

Number of hex characters in a binary literal

</td>
<td valign="top">

8,192 Bytes

</td>
<td valign="top">

MAXIMUM\_LENGTH\_OF\_BINARY\_LITERAL

</td>
</tr>
<tr>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

**Tables and View Limitations** 

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Number of columns in a table

</td>
<td valign="top">

64,000

This limit can vary based on context, for example, in the context of virtual tables, SAP HANA may be limited by the capabilities of the remote system and the limit of the other DBMS may apply instead. In cases such as this, the limit that is met first becomes the actual limit.

</td>
<td valign="top">

MAXIMUM\_NUMBER\_OF\_COLUMNS\_IN\_TABLE

</td>
</tr>
<tr>
<td valign="top">

Number of columns in a row table

</td>
<td valign="top">

1,000

</td>
<td valign="top">

MAXIMUM\_NUMBER\_OF\_COLUMNS\_IN\_ROW\_TABLE

</td>
</tr>
<tr>
<td valign="top">

Number of columns in a view

</td>
<td valign="top">

64,000

</td>
<td valign="top">

MAXIMUM\_NUMBER\_OF\_COLUMNS\_IN\_VIEW

</td>
</tr>
<tr>
<td valign="top">

Number of rows in each table

</td>
<td valign="top">

Limited by storage size RS: 1,945 GB/sizeof\(row\),

CS: 2,100,000,000 \* number of partitions

</td>
<td valign="top">



</td>
</tr>
<tr>
<td valign="top">

Length of a row

</td>
<td valign="top">

Limited by RS storage size \(1,945 GB per index server\)

</td>
<td valign="top">



</td>
</tr>
<tr>
<td valign="top">

Size of a non-partitioned table

</td>
<td valign="top">

Limited by RS storage size \(1,945 GB per index server\)

</td>
<td valign="top">



</td>
</tr>
<tr>
<td valign="top">

Number of partitions in a CS table

</td>
<td valign="top">

16,000

</td>
<td valign="top">

MAXIMUM\_NUMBER\_OF\_PARTITIONS\_IN\_CSTABLE

</td>
</tr>
<tr>
<td valign="top">

Number of triggers per table per DML statement

</td>
<td valign="top">

1,024

</td>
<td valign="top">

MAXIMUM\_NUMBER\_OF\_TRIGGERS\_PER\_TABLE\_PER\_DML

</td>
</tr>
<tr>
<td valign="top">

Number of records per \(non-partitioned\) table

</td>
<td valign="top">

2,100,000,000

</td>
<td valign="top">



</td>
</tr>
<tr>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

**Indexes and Constraints** 

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Number of indexes for a table

</td>
<td valign="top">

1,023

</td>
<td valign="top">

MAXIMUM\_NUMBER\_OF\_INDEXES\_IN\_TABLE

</td>
</tr>
<tr>
<td valign="top">

Number of primary key columns in each table

</td>
<td valign="top">

16

</td>
<td valign="top">

MAXIMUM\_NUMBER\_OF\_COLUMNS\_IN\_PRIMARY\_KEY

</td>
</tr>
<tr>
<td valign="top">

Number of primary key columns in each column store table

</td>
<td valign="top">

1,000

</td>
<td valign="top">

MAXIMUM\_NUMBER\_OF\_COLUMNS\_IN\_PRIMARY\_KEY\_IN\_COLUMN\_TABLE

</td>
</tr>
<tr>
<td valign="top">

Number of columns in an index

</td>
<td valign="top">

16

</td>
<td valign="top">

MAXIMUM\_NUMBER\_OF\_COLUMNS\_IN\_INDEX

</td>
</tr>
<tr>
<td valign="top">

Number of columns in a UNIQUE constraint

</td>
<td valign="top">

16

</td>
<td valign="top">

MAXIMUM\_NUMBER\_OF\_COLUMNS\_IN\_UNIQUE\_CONSTRAINT

</td>
</tr>
<tr>
<td valign="top">

Size of sum of primary key, index, UNIQUE constraint

</td>
<td valign="top">

16,384 Bytes

</td>
<td valign="top">

MAXIMUM\_SIZE\_OF\_KEY\_IN\_INDEX

</td>
</tr>
<tr>
<td valign="top">

Number of indexes in row store

</td>
<td valign="top">

256,000

</td>
<td valign="top">



</td>
</tr>
<tr>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
<td valign="top">



</td>
</tr>
<tr>
<td valign="top">

**SQL** 

</td>
<td valign="top">

 

</td>
<td valign="top">



</td>
</tr>
<tr>
<td valign="top">

Length of an SQL statement

</td>
<td valign="top">

2,147,483,648 Bytes

</td>
<td valign="top">

MAXIMUM\_LENGTH\_OF\_SQL\_STATEMENT

</td>
</tr>
<tr>
<td valign="top">

Depth of SQL view nesting

</td>
<td valign="top">

128

</td>
<td valign="top">

MAXIMUM\_DEPTH\_OF\_SQL\_VIEW\_NESTING

</td>
</tr>
<tr>
<td valign="top">

Maximum depth of SQL parse tree

This limitation does not show in M\_SYSTEM\_LIMITS unless a limit is configured to something other than 0 \(no limit\) using the max\_parse\_tree\_depth parameter in `indexerver.ini`.

</td>
<td valign="top">

0

0 \(unlimited\)

</td>
<td valign="top">

MAXIMUM\_DEPTH\_OF\_SQL\_PARSE\_TREE

</td>
</tr>
<tr>
<td valign="top">

Maximum depth of joins in a statement.

This limitation does not show in M\_SYSTEM\_LIMITS unless a limit is configured to something other than 0 \(no limit\) using the max\_join\_depth parameter in `indexerver.ini`.

</td>
<td valign="top">

0

</td>
<td valign="top">

MAXIMUM\_DEPTH\_OF\_JOINS

</td>
</tr>
<tr>
<td valign="top">

Number of columns in an ORDER BY

</td>
<td valign="top">

65,535

</td>
<td valign="top">

MAXIMUM\_NUMBER\_OF\_COLUMNS\_IN\_ORDER\_BY

</td>
</tr>
<tr>
<td valign="top">

Number of columns in a GROUP BY

</td>
<td valign="top">

65,535

</td>
<td valign="top">

MAXIMUM\_NUMBER\_OF\_COLUMNS\_IN\_GROUP\_BY

</td>
</tr>
<tr>
<td valign="top">

Number of elements in IN predicates

</td>
<td valign="top">

65,535

</td>
<td valign="top">

MAXIMUM\_NUMBER\_OF\_COLUMNS\_IN\_IN\_PREDICATE

</td>
</tr>
<tr>
<td valign="top">

Number of elements in SELECT clause

</td>
<td valign="top">

65,535

</td>
<td valign="top">

MAXIMUM\_NUMBER\_OF\_OUTPUT\_COLUMNS\_IN\_STATEMENT

</td>
</tr>
<tr>
<td valign="top">

Number of tables in a statement.

This limitation does not show in M\_SYSTEM\_LIMITS unless a limit is configured to something other than 0 \(no limit\) using the max\_table\_count\_in\_statement parameter in indexerver.ini.

</td>
<td valign="top">

0

</td>
<td valign="top">

MAXIMUM\_NUMBER\_OF\_TABLES\_IN\_STATEMENT

</td>
</tr>
<tr>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
<td valign="top">



</td>
</tr>
<tr>
<td valign="top">

**LOB Limitations** 

</td>
<td valign="top">



</td>
<td valign="top">



</td>
</tr>
<tr>
<td valign="top">

Maximum size of an in-memory LOB for a column store table

</td>
<td valign="top">

2 GB

</td>
<td valign="top">

MAXIMUM\_SIZE\_OF\_MEMORY\_LOB\_IN\_COLUMN\_STORE

</td>
</tr>
<tr>
<td valign="top">

Maximum size of an in-memory LOB for a row store table

</td>
<td valign="top">

2 GB

</td>
<td valign="top">

MAXIMUM\_SIZE\_OF\_MEMORY\_LOB\_IN\_ROW\_STORE

</td>
</tr>
<tr>
<td valign="top">

Maximum size of a packed LOB

</td>
<td valign="top">

1,013,760 bytes

</td>
<td valign="top">

MAXIMUM\_SIZE\_OF\_PACKED\_LOB

</td>
</tr>
<tr>
<td valign="top">

Maximum size of a LOB on disk

</td>
<td valign="top">

4,294,967,295 bytes

</td>
<td valign="top">

MAXIMUM\_SIZE\_OF\_DISK\_LOB

</td>
</tr>
<tr>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

**Procedures** 

</td>
<td valign="top">

 

</td>
<td valign="top">



</td>
</tr>
<tr>
<td valign="top">

Size of all stored procedures

</td>
<td valign="top">

1,945 GB

</td>
<td valign="top">

MAXIMUM\_SIZE\_OF\_ALL\_STORED\_PROCEDURES

</td>
</tr>
<tr>
<td valign="top">

Size of a procedure definition

</td>
<td valign="top">

2 GB

</td>
<td valign="top">

MAXIMUM\_SIZE\_OF\_PROCEDURE\_DEFINITION

</td>
</tr>
<tr>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

**Auditing** 

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Maximum number of files

</td>
<td valign="top">

999

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Default timestamp format

</td>
<td valign="top">

ISO format \(YYYY-MM-DDTHH:MM:SS.000000Z\)

</td>
<td valign="top">

 

</td>
</tr>
</table>

**Related Information**  


[M\_SYSTEM\_LIMITS System View](../020-System-Views-Reference/022-Monitoring-Views/m-system-limits-system-view-20c6023.md "Provides system limit information.")

