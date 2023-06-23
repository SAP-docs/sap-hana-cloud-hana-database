<!-- loiodfbf8bd8f9af477ba2a357c45804569e -->

# M\_PERSISTENT\_MEMORY\_VOLUME\_DATA\_FILES System View

Reports metadata statistics about files created by SAP HANA services for data storage on the persistent memory volumes.



<a name="loiodfbf8bd8f9af477ba2a357c45804569e__section_fpj_sv5_lcb"/>

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

FILE\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the file name of data block file located on persistent memory volume on Numa node of host \(for example, `000000fe0000018a-00000051-000001c2-00000001_159.fileblock`\).



</td>
</tr>
<tr>
<td valign="top">

IS\_MAPPED



</td>
<td valign="top">

NVARCHAR\(5\)



</td>
<td valign="top">

Indicates whether the data block file is memory mapped into virtual address space: TRUE or FALSE.



</td>
</tr>
<tr>
<td valign="top">

SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the size of the data block file in bytes.



</td>
</tr>
</table>

**Related Information**  


[M\_PERSISTENT\_MEMORY\_VOLUMES System View](m-persistent-memory-volumes-system-view-8aba468.md "Reports the capacity, usage and metadata of persistent memory volumes.")

[M\_PERSISTENT\_MEMORY\_VOLUME\_STATISTICS System View](m-persistent-memory-volume-statistics-system-view-33f228a.md "Reports the statistics of physical lifecycle events of blocks managed by SAP HANA services on the persistent memory volumes.")

[M\_PERSISTENT\_MEMORY\_VOLUME\_STATISTICS\_RESET System View](m-persistent-memory-volume-statistics-reset-system-view-596438f.md "Reports the statistics of physical lifecycle events of blocks managed by SAP HANA services on the persistent memory volumes since the last reset.")

[UNLOAD Statement \(Data Manipulation\)](../../010-SQL-Reference/012-SQL-Statements/unload-statement-data-manipulation-20fe92a.md "Unloads the column store table from memory.")

[M\_CATALOG\_MEMORY System View](m-catalog-memory-system-view-20a994e.md "Provides memory usage information by catalog manager.")

