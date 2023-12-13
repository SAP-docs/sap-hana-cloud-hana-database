<!-- loio21031a8775191014bd929f35e4263f06 -->

# VIRTUAL\_TABLES System View

Provides information about virtual tables.



<a name="loio21031a8775191014bd929f35e4263f06___v_i_r_t_u_a_l__t_a_b_l_e_s_1struct_VIRTUAL_TABLES"/>

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

REMOTE\_SOURCE\_SCHEMA\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the schema name of the remote source object.

</td>
</tr>
<tr>
<td valign="top">

REMOTE\_SOURCE\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the remote source name.

</td>
</tr>
<tr>
<td valign="top">

REMOTE\_DB\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the remote database name.

</td>
</tr>
<tr>
<td valign="top">

REMOTE\_OWNER\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the remote schema name that owns the remote object.

</td>
</tr>
<tr>
<td valign="top">

REMOTE\_OBJECT\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the remote object name.

</td>
</tr>
<tr>
<td valign="top">

IS\_INSERTABLE

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether or not INSERT is supported: TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

IS\_UPDATABLE

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether or not UPDATE is supported: TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

IS\_DELETABLE

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether or not DELETE is supported: TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

IS\_UPSERTABLE

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether or not UPSERT is supported: TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

IS\_SELECTABLE

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether or not SELECT is supported: TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

IS\_REMOTE\_SUBSCRIPTION\_SUPPORTED

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether or not REMOTE SUBSCRIPTION is supported: TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

IS\_REMOTE\_SUBSCRIPTION\_TRANSACTIONAL

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether or not transactional REMOTE SUBSCRIPTION is supported: TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

HAS\_REPLICA

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether or not the virtual table has a replica: TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

IS\_CDC\_SUPPORTED

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether or not the CDC capability is supported: TRUE/FALSE.

</td>
</tr>
</table>



<a name="loio21031a8775191014bd929f35e4263f06__section_l4g_2b1_fzb"/>

## Additional Information

Unless otherwise specified, system views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all system views and their data regardless of the PUBLIC role and privilege grants.

**Related Information**  


[CREATE VIRTUAL TABLE Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/create-virtual-table-statement-data-definition-d2a0406.md "Creates a virtual table at a remote source.")

[ALTER VIRTUAL TABLE Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/alter-virtual-table-statement-data-definition-5182698.md "Modifies a virtual table's column properties, and lets you refresh the metadata of a virtual table.")

[VIRTUAL\_TABLE\_PARAMETERS System View](virtual-table-parameters-system-view-95054e1.md "Provides a list of parameters of the virtual tables that refer to column views in a remote SAP HANA database.")

[VIRTUAL\_TABLE\_PROPERTIES System View](virtual-table-properties-system-view-88396eb.md "Provides the properties set on virtual tables.")

[Managing Virtual Tables](https://help.sap.com/viewer/477aa413a36c4a95878460696fcc8896/2023_4_QRC/en-US/d16e86e414b54cd0b6facd4f6a2e7e01.html "Virtual tables point to remote tables or views in a remote source. When SQL queries are executed on a virtual table, they access the remote data as if it were stored locally.") :arrow_upper_right:

[Create a Virtual Table](https://help.sap.com/viewer/477aa413a36c4a95878460696fcc8896/2023_4_QRC/en-US/4ef3f55395dc47a89462b77b56d71f7f.html "Create a virtual table from the remote object of a remote source.") :arrow_upper_right:

[Delete a Virtual Table](https://help.sap.com/viewer/477aa413a36c4a95878460696fcc8896/2023_4_QRC/en-US/ebcb10f2c2d44b3294dfb0cadd88c396.html "Delete an existing virtual table from your schema using the SAP HANA database explorer.") :arrow_upper_right:

[List All Virtual Tables](https://help.sap.com/viewer/477aa413a36c4a95878460696fcc8896/2023_4_QRC/en-US/f4badb298616428ba585f68d4c68daa1.html "Provides a list of all virtual tables you have privilege to.") :arrow_upper_right:

[List Virtual Tables by Schema](https://help.sap.com/viewer/477aa413a36c4a95878460696fcc8896/2023_4_QRC/en-US/682a0b4ee20349a0b36d3d940a6efaa0.html "Display the virtual tables of a remote source by schema using SQL syntax.") :arrow_upper_right:

[Refresh a Virtual Table](https://help.sap.com/viewer/477aa413a36c4a95878460696fcc8896/2023_4_QRC/en-US/14ea22d516634790a29c2e3676dcb9b1.html "Update a virtual table to reflect metadata changes in the corresponding remote source table using SQL syntax.") :arrow_upper_right:

