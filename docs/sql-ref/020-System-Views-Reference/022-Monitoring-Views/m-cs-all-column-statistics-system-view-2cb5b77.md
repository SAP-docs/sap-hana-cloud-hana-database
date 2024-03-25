<!-- loio2cb5b77a6d274289a0d5dcfa75c11d30 -->

# M\_CS\_ALL\_COLUMN\_STATISTICS System View

Provides information on how many scans and index searches were performed on any specified columns.




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

COLUMN\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the column name.

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

Returns the table partition ID:

-   For partitioned tables, the part ID is equal to the sequential number of the partition, starting at 1.
-   For replicated tables, the part ID is 1 for the original table and subsequent part IDs are assigned to replica tables.
-   The part ID is 0 for tables that are not partitioned.
-   A part ID value of -1 indicates that a modification of the table schema is currently in progress.



</td>
</tr>
<tr>
<td valign="top">

SCANNED\_RECORD\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of scanned rows on the main part of a specified column. The value is reset when the column is unloaded or merged.

</td>
</tr>
<tr>
<td valign="top">

INDEX\_LOOKUP\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of index lookups performed on the main part of a specified column. The value is reset when the column is unloaded or merged.

</td>
</tr>
</table>

**Related Information**  


[M\_CS\_ALL\_COLUMNS System View](m-cs-all-columns-system-view-20acf4c.md "Provides runtime information for all columns in column tables, including internal column tables.")

[CS\_ALL\_COLUMNS System View](../021-System-Views/cs-all-columns-system-view-813f1ae.md "Provides information from all columns of column tables, including internal ones.")

[CS\_CONCAT\_COLUMNS System View](../021-System-Views/cs-concat-columns-system-view-02fb9ca.md "Provides information on concat columns in the database.")

[CS\_VIEW\_COLUMNS System View](../021-System-Views/cs-view-columns-system-view-20a1288.md "Provides information about the columns defined for column store join views.")

[RENAME COLUMN Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/rename-column-statement-data-definition-20fb2b8.md "Changes the name of a column.")

[Memory Management in the Column Store](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2024_1_QRC/en-US/bd6e6be8bb5710149e34e14608e07b76.html "The column store is the part of the SAP HANA database that manages data organized in columns in memory. Tables created as column tables are stored here.") :arrow_upper_right:

[Data Compression in the Column Store](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2024_1_QRC/en-US/bd9017c8bb571014ae79efaeb46940f3.html "The column store allows for the efficient compression of data. This makes it less costly for the SAP HANA database to keep data in main memory. It also speeds up searches and calculations.") :arrow_upper_right:

[Viewing Load Unit Information for Column Store Tables in SAP HANA NSE](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2024_1_QRC/en-US/61c9c0f4379c41f3b3e1c483f2395a11.html "Several system and monitoring views provide information on load unit preferences (PAGE loadable, COLUMN loadable, or DEFAULT loadable) set for the SAP HANA NSE column-store table.") :arrow_upper_right:

[Understanding Load Unit Behavior in SAP HANA NSE Column Store Tables](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2024_1_QRC/en-US/202101e31f1a42c884dd1d2057c6a605.html "The loading behavior is determined by the load unit (one of PAGE, COLUMN, and DEFAULT) specified for the column, partition, and table in SAP HANA native storage extension (NSE) column-store tables.") :arrow_upper_right:

[Monitoring View Extensions for Column Store Paged Data Size](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2024_1_QRC/en-US/b06e99431b2740fdb4a47c7ee130f89d.html "A number of monitoring views provide information about the in-memory and on-disk size of the page-loadable data in relation to the in-memory and on-disk size of non-paged (column-loadable) data, helping you understand the effectiveness of page-loadable storage.") :arrow_upper_right:

