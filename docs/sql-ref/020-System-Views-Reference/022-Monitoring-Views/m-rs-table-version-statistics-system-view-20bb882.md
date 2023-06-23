<!-- loio20bb882f75191014b1fddb636c3891e8 -->

# M\_RS\_TABLE\_VERSION\_STATISTICS System View

Provides information on row table versions: detailed version counts and used sizes.



<a name="loio20bb882f75191014b1fddb636c3891e8___m__r_s__t_a_b_l_e__v_e_r_s_i_o_n__s_t_a_t_i_s_t_i_c_s_1struct_M_RS_TABLE_VERSION_STATISTICS"/>

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

Displays the name of the schema to which the container belongs.



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

Displays the table name of the container.



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

CONTAINER\_ID



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Indicates that some tables may have several containers to store its data. The container ID is a unique identifier for each container.



</td>
</tr>
<tr>
<td valign="top">

VERSION\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of all versions in the container. This includes all versions regardless of their version type and status.



</td>
</tr>
<tr>
<td valign="top">

INSERT\_VERSION\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of insert-versions in the container.



</td>
</tr>
<tr>
<td valign="top">

UPDATE\_VERSION\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of update-versions in the container.



</td>
</tr>
<tr>
<td valign="top">

DELETE\_VERSION\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of delete-versions in the container.



</td>
</tr>
<tr>
<td valign="top">

COMMITTED\_VERSION\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of all committed versions in the container \(includes all types\).



</td>
</tr>
<tr>
<td valign="top">

COMMITTED\_INSERT\_VERSION\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of committed insert-versions in the container.



</td>
</tr>
<tr>
<td valign="top">

COMMITTED\_UPDATE\_VERSION\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of committed update-versions in the container.



</td>
</tr>
<tr>
<td valign="top">

COMMITTED\_DELETE\_VERSION\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of committed delete-versions in the container.



</td>
</tr>
<tr>
<td valign="top">

UNCOMMITTED\_VERSION\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of all uncommitted versions in the container \(includes all types\).



</td>
</tr>
<tr>
<td valign="top">

UNCOMMITTED\_INSERT\_VERSION\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of uncommitted insert-versions in the container.



</td>
</tr>
<tr>
<td valign="top">

UNCOMMITTED\_UPDATE\_VERSION\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of uncommitted update-versions in the container.



</td>
</tr>
<tr>
<td valign="top">

UNCOMMITTED\_DELETE\_VERSION\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of uncommitted delete-versions in the container.



</td>
</tr>
<tr>
<td valign="top">

VERSION\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the used size of the versions in the container in bytes. This includes all versions regardless of their version type and status.



</td>
</tr>
<tr>
<td valign="top">

INSERT\_VERSION\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the used size of the insert-versions in the container in bytes.



</td>
</tr>
<tr>
<td valign="top">

UPDATE\_VERSION\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the used size of update-versions in the container in bytes.



</td>
</tr>
<tr>
<td valign="top">

DELETE\_VERSION\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the used size of delete-versions in the container in bytes.



</td>
</tr>
<tr>
<td valign="top">

COMMITTED\_VERSION\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the used size of all of the committed versions in the container \(includes all types\) in bytes.



</td>
</tr>
<tr>
<td valign="top">

COMMITTED\_INSERT\_VERSION\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the used size of committed insert-versions in the container in bytes.



</td>
</tr>
<tr>
<td valign="top">

COMMITTED\_UPDATE\_VERSION\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the used size of committed update-versions in the container in bytes.



</td>
</tr>
<tr>
<td valign="top">

COMMITTED\_DELETE\_VERSION\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the used size of committed delete-versions in the container in bytes.



</td>
</tr>
<tr>
<td valign="top">

UNCOMMITTED\_VERSION\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the used size of all uncommitted versions in the container \(includes all types\) in bytes.



</td>
</tr>
<tr>
<td valign="top">

UNCOMMITTED\_INSERT\_VERSION\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the used size of uncommitted insert-versions in the container in bytes.



</td>
</tr>
<tr>
<td valign="top">

UNCOMMITTED\_UPDATE\_VERSION\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the used size of uncommitted update-versions in the container in bytes.



</td>
</tr>
<tr>
<td valign="top">

UNCOMMITTED\_DELETE\_VERSION\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the used size of uncommitted delete-versions in the container in bytes.



</td>
</tr>
<tr>
<td valign="top">

MIN\_COMMIT\_ID



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Indicates that each committed version has its commit ID. MIN\_COMMIT\_ID refers to the minimum value of commit ID among all committed versions.



</td>
</tr>
<tr>
<td valign="top">

IS\_SYSTEM\_TABLE



</td>
<td valign="top">

NVARCHAR\(5\)



</td>
<td valign="top">

Returns TRUE if the table's schema is SYS, or if the table schema or name starts with \_SYS\_.



</td>
</tr>
</table>

**Related Information**  


[M\_RS\_MEMORY System View](m-rs-memory-system-view-20bb47a.md "Provides RS memory statistics.")

[M\_RS\_INDEXES System View](m-rs-indexes-system-view-20bb03a.md "Provides the statistics for B-tree and CPB-tree indexes.")

[M\_RS\_TABLES System View](m-rs-tables-system-view-20bbc60.md "Provides information about row tables, including detailed table sizes and record count.")

[System-Versioned Tables](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2023_2_QRC/en-US/91302b26f62c4433bbc58e0a951cdc1d.html "System-versioned tables are part of the SQL standard. They support the tracking of changes on column store tables by capturing the validity period of each record.") :arrow_upper_right:

