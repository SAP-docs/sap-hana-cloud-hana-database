<!-- loio20c5439d75191014b9d0b604a95fb63e -->

# M\_SNAPSHOTS System View

Provides information about existing snapshots.



<a name="loio20c5439d75191014b9d0b604a95fb63e___m__s_n_a_p_s_h_o_t_s_1struct_M_SNAPSHOTS"/>

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

Displays the persistence volume ID.

</td>
</tr>
<tr>
<td valign="top">

ID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the snapshot ID.

</td>
</tr>
<tr>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the creation time.

</td>
</tr>
<tr>
<td valign="top">

PURPOSE

</td>
<td valign="top">

NVARCHAR\(24\)

</td>
<td valign="top">

Displays why the snapshot was executed.

</td>
</tr>
<tr>
<td valign="top">

FOR\_BACKUP

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays if the snapshot was created for backup: TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

ANCHOR

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the anchor.

</td>
</tr>
<tr>
<td valign="top">

REDO\_LOG\_POSITION

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the redo log position corresponding to the snapshot.

</td>
</tr>
<tr>
<td valign="top">

LAST\_COMMIT\_TIME

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the timestamp of the last commit of the snapshot.

</td>
</tr>
</table>

**Related Information**  


[M\_DATABASES System View](m-databases-system-view-dbbdc0d.md "Provides information about all databases in the system. The full content of this view is only accessible from the system database.")

[M\_MVCC\_SNAPSHOTS System View](m-mvcc-snapshots-system-view-b41f6b2.md "Provides detailed snapshot information of the Multiversion Concurrency Control (MVCC) manager.")

[Performance: Using Hints to Query Data Snapshots](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2023_4_QRC/en-US/556a518b49f84d8db770cbd068b94b65.html "Several features in SAP HANA use data snapshots to improve performance. You can use configurable hint classes as a standard way of controlling at run time how the data is selected, either from the snapshot or from the database.") :arrow_upper_right:

