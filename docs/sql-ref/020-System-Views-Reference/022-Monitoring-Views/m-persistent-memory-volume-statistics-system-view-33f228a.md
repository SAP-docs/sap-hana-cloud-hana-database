<!-- loio33f228a8898b462b989406643ca091f8 -->

# M\_PERSISTENT\_MEMORY\_VOLUME\_STATISTICS System View

Reports the statistics of physical lifecycle events of blocks managed by SAP HANA services on the persistent memory volumes.



<a name="loio33f228a8898b462b989406643ca091f8__section_fpj_sv5_lcb"/>

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

TOTAL\_ACTIVE\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total number of active blocks from persistent memory volume. This counter is computed as a sum of loaded or created blocks but excludes deleted blocks.

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_ACTIVE\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total size, in bytes, of active blocks from persistent memory volume. This counter is computed as a sum of loaded or created blocks but excludes deleted blocks.

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_CREATE\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total number of newly created \(that is, temporary\) blocks from the persistent memory volume.

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_CREATE\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total size, in bytes, of the newly created temporary blocks from the persistent memory volume.

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_COMMIT\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total number of the permanently persisted blocks from the persistent memory volume.

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_COMMIT\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total size, in bytes, of the permanently persisted blocks from the persistent memory volume.

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_DELETE\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total number of deleted blocks from the persistent memory volume.

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_DELETE\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total size, in bytes, of the deleted blocks from the persistent memory volume.

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_DESTROY\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total number of destroyed blocks \(no refcount\) from the persistent memory volume.

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_DESTROY\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total size, in bytes, of the destroyed blocks \(no refcount\) from the persistent memory volume.

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_LOAD\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total number of loaded/initialized blocks from the persistent memory volume upon service restart.

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_LOAD\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total size, in bytes, of loaded/initialized blocks from the persistent memory volume upon service restart.

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_MAPPED\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total number of blocks mapped into virtual memory from the persistent memory volume.

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_MAPPED\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total size, in bytes, of blocks mapped into virtual memory from the persistent memory volume.

</td>
</tr>
</table>

**Related Information**  


[M\_PERSISTENT\_MEMORY\_VOLUME\_DATA\_FILES System View](m-persistent-memory-volume-data-files-system-view-dfbf8bd.md "Reports metadata statistics about files created by SAP HANA services for data storage on the persistent memory volumes.")

[M\_PERSISTENT\_MEMORY\_VOLUMES System View](m-persistent-memory-volumes-system-view-8aba468.md "Reports the capacity, usage and metadata of persistent memory volumes.")

[M\_PERSISTENT\_MEMORY\_VOLUME\_STATISTICS\_RESET System View](m-persistent-memory-volume-statistics-reset-system-view-596438f.md "Reports the statistics of physical lifecycle events of blocks managed by SAP HANA services on the persistent memory volumes since the last reset.")

[UNLOAD Statement \(Data Manipulation\)](../../010-SQL-Reference/012-SQL-Statements/unload-statement-data-manipulation-20fe92a.md "Unloads the column store table from memory.")

[M\_CATALOG\_MEMORY System View](m-catalog-memory-system-view-20a994e.md "Provides memory usage information by catalog manager.")

