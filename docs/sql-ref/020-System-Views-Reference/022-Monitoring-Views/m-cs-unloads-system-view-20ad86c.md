<!-- loio20ad86c6751910148fe5ee1c3b76cadb -->

# M\_CS\_UNLOADS System View

Provides a history of column unloads.



<a name="loio20ad86c6751910148fe5ee1c3b76cadb___m__c_s__u_n_l_o_a_d_s_1struct_M_CS_UNLOADS"/>

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

UNLOAD\_TIME



</td>
<td valign="top">

TIMESTAMP



</td>
<td valign="top">

Displays the timestamp of unload event.



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

Displays the column name. Empty if the whole table is unloaded.



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

REASON



</td>
<td valign="top">

NVARCHAR\(16\)



</td>
<td valign="top">

Displays the possible reasons for the unload. Values are LOW MEMORY, SHRINK, EXPLICIT, MERGE, or UNUSED RESOURCE. Unloads caused by a manual shrink are reported as SHRINK, whereas unloads caused by memory management's automatic shrink on out of memory \(OOM\) are reported as LOW MEMORY.



</td>
</tr>
<tr>
<td valign="top">

PERSISTENT\_MEMORY



</td>
<td valign="top">

NVARCHAR\(6\)



</td>
<td valign="top">

Displays whether persistent memory is removed as part of the unload. Values are RETAIN or DELETE. Empty if the user did not specify a value for the unload.



</td>
</tr>
</table>

**Related Information**  


[UNLOAD Statement \(Data Manipulation\)](../../010-SQL-Reference/012-SQL-Statements/unload-statement-data-manipulation-20fe92a.md "Unloads the column store table from memory.")

[Load/Unload a Column Table into/from Memory](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2023_2_QRC/en-US/c133165bbb57101493c5fb19b5b8607f.html "Under normal circumstances, the SAP HANA database manages the loading and unloading of tables into and from memory automatically, the aim being to keep all relevant data in memory. However, you can manually load and unload individual tables, as well as load table columns if necessary.") :arrow_upper_right:

