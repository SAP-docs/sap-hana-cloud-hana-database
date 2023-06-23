<!-- loio00257f0a8244471e8fe1ca0670323f4e -->

# M\_CS\_INDEXES System View

Provides information for column store indexes.



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

HOST



</td>
<td valign="top">

NVARCHAR\(64\)



</td>
<td valign="top">

Displays the host name.



</td>
</tr>
<tr>
<td valign="top">

PORT



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Displays the internal port.



</td>
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

TABLE\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the table name.



</td>
</tr>
<tr>
<td valign="top">

INDEX\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the index name.



</td>
</tr>
<tr>
<td valign="top">

PART\_ID



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Displays the partition ID. Returns the following:

-   For partitioned tables, the part ID is equal to the sequential number of the partition, starting at 1.
-   In the case of replicated tables, the part ID is 1 for the original table and subsequent part IDs are assigned to replica tables.
-   The part ID is 0 for tables that are not partitioned.
-   A part ID value of -1 indicates that a modification of the table schema is in progress.



</td>
</tr>
<tr>
<td valign="top">

HASH\_COLLISION\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the count of hash collisions aggregated over all values.



</td>
</tr>
<tr>
<td valign="top">

CONCAT\_COLUMN\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the name of the concat column in the case of multi-column indexes. This is empty in the case of a single-column index.



</td>
</tr>
<tr>
<td valign="top">

MEMORY\_SIZE\_IN\_TOTAL



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the total size of the concat plus the sum of the inverted index sizes of the single index columns in bytes.



</td>
</tr>
<tr>
<td valign="top">

MEMORY\_SIZE\_IN\_CONCAT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the total size of the concat in bytes.



</td>
</tr>
<tr>
<td valign="top">

MOST\_SELECTIVE\_COLUMN\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the name of the most selective index column of a composite index. The most selective column is the one with lowest cost value.



</td>
</tr>
<tr>
<td valign="top">

INVERTED\_INDIVIDUAL\_COST



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the cost value for INVERTED INDIVIDUAL index type. This cost value is an indicator for the possible performance impact when switching between different index-types. A high cost value indicates a possible high overhead when using INVERTED INDIVIDUAL index-type compared to INVERTED VALUE index-type. A cost value of 1 indicates that there is no overhead. For non composite or non-unique indexes the value is -1, which indicates that no cost value is available.



</td>
</tr>
</table>

**Related Information**  


[INDEXES System View](../021-System-Views/indexes-system-view-20a7044.md "Provides information about indexes on tables.")

[CREATE INDEX Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/create-index-statement-data-definition-20d44b4.md "Creates an index on a table column.")

[ALTER INDEX Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/alter-index-statement-data-definition-20d014b.md "Alters an index.")

[DROP INDEX Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/drop-index-statement-data-definition-20d6f4e.md "Removes an index.")

[Changing the Load Units for Indexes Using ALTER INDEX](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2023_2_QRC/en-US/02dc395617744584aa464f3e5e5ee509.html "") :arrow_upper_right:

