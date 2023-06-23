<!-- loiof3f3d2ec6f5b1014a7ade9647df0fac3 -->

# M\_CS\_LOADS System View

Provides a history of column loads.



<a name="loiof3f3d2ec6f5b1014a7ade9647df0fac3___m__c_s__l_o_a_d_s_1struct_M_CS_LOADS"/>

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

LOAD\_TIME



</td>
<td valign="top">

TIMESTAMP



</td>
<td valign="top">

Displays the timestamp of the load event.



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

Displays the column name. This is left empty if the whole table is loaded.



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

TABLE\_OID



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the object ID of the table.



</td>
</tr>
<tr>
<td valign="top">

LOAD\_DURATION



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the load duration, in milliseconds.



</td>
</tr>
<tr>
<td valign="top">

ERROR\_CODE



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Displays the error code.



</td>
</tr>
<tr>
<td valign="top">

ERROR\_TEXT



</td>
<td valign="top">

NVARCHAR\(5000\)



</td>
<td valign="top">

Displays the error text.



</td>
</tr>
<tr>
<td valign="top">

STATEMENT\_ID



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the statement ID.



</td>
</tr>
<tr>
<td valign="top">

STATEMENT\_HASH



</td>
<td valign="top">

NVARCHAR\(32\)



</td>
<td valign="top">

Displays the unique identifier for an SQL string.



</td>
</tr>
</table>

**Related Information**  


[LOAD Statement \(Data Manipulation\)](../../010-SQL-Reference/012-SQL-Statements/load-statement-data-manipulation-20f83c8.md "Explicitly loads column store table data into memory instead of upon first access.")

[Viewing Load Unit Information for Column Store Tables in SAP HANA NSE](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2023_2_QRC/en-US/61c9c0f4379c41f3b3e1c483f2395a11.html "Several system and monitoring views provide information on load unit preferences (PAGE loadable, COLUMN loadable, or DEFAULT loadable) set for the SAP HANA NSE column-store table.") :arrow_upper_right:

[Understanding Load Unit Behavior in SAP HANA NSE Column Store Tables](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2023_2_QRC/en-US/202101e31f1a42c884dd1d2057c6a605.html "The loading behavior is determined by the load unit (one of PAGE, COLUMN, and DEFAULT) specified for the column, partition, and table in SAP HANA native storage extension (NSE) column-store tables.") :arrow_upper_right:

