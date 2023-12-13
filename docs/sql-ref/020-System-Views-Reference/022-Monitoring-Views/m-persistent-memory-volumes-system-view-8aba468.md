<!-- loio8aba4689438e49799d9adb0fd30c0447 -->

# M\_PERSISTENT\_MEMORY\_VOLUMES System View

Reports the capacity, usage and metadata of persistent memory volumes.



<a name="loio8aba4689438e49799d9adb0fd30c0447__section_fpj_sv5_lcb"/>

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

VOLUME\_ID

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays an ID for the persistence volume.

</td>
</tr>
<tr>
<td valign="top">

NUMA\_NODE\_INDEX

</td>
<td valign="top">

SMALLINT

</td>
<td valign="top">

Displays the logical NUMA node index as in the M\_NUMA\_NODES view.

</td>
</tr>
<tr>
<td valign="top">

PATH

</td>
<td valign="top">

NVARCHAR\(512\)

</td>
<td valign="top">

Displays the absolute directory base path of persistent memory volume configured for NUMA node.

</td>
</tr>
<tr>
<td valign="top">

STORAGE\_MODE

</td>
<td valign="top">

NVARCHAR\(32\)

</td>
<td valign="top">

For internal use only.

</td>
</tr>
<tr>
<td valign="top">

FILESYSTEM\_TYPE

</td>
<td valign="top">

NVARCHAR\(32\)

</td>
<td valign="top">

Displays the filesystem type, for example, ext3, ext4, xfs.

</td>
</tr>
<tr>
<td valign="top">

IS\_DIRECT\_ACCESS\_SUPPORTED

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether Direct Access semantics are supported by the volume.

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total physical memory size, in bytes, of the persistent memory volume.

</td>
</tr>
<tr>
<td valign="top">

USED\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the used physical memory size, in bytes, of persistent memory volume.

</td>
</tr>
</table>

**Related Information**  


[M\_PERSISTENT\_MEMORY\_VOLUME\_DATA\_FILES System View](m-persistent-memory-volume-data-files-system-view-dfbf8bd.md "Reports metadata statistics about files created by SAP HANA services for data storage on the persistent memory volumes.")

[M\_PERSISTENT\_MEMORY\_VOLUME\_STATISTICS System View](m-persistent-memory-volume-statistics-system-view-33f228a.md "Reports the statistics of physical lifecycle events of blocks managed by SAP HANA services on the persistent memory volumes.")

[M\_PERSISTENT\_MEMORY\_VOLUME\_STATISTICS\_RESET System View](m-persistent-memory-volume-statistics-reset-system-view-596438f.md "Reports the statistics of physical lifecycle events of blocks managed by SAP HANA services on the persistent memory volumes since the last reset.")

[UNLOAD Statement \(Data Manipulation\)](../../010-SQL-Reference/012-SQL-Statements/unload-statement-data-manipulation-20fe92a.md "Unloads the column store table from memory.")

[M\_CATALOG\_MEMORY System View](m-catalog-memory-system-view-20a994e.md "Provides memory usage information by catalog manager.")

