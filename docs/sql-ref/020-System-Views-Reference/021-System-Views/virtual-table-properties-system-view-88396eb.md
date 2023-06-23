<!-- loio88396eb7582241669fe1e28ce1b78b1b -->

# VIRTUAL\_TABLE\_PROPERTIES System View

Provides the properties set on virtual tables.



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

Displays the schema name of the virtual table.



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

Displays the virtual table name.



</td>
</tr>
<tr>
<td valign="top">

PROPERTY



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the property name.



</td>
</tr>
<tr>
<td valign="top">

VALUE



</td>
<td valign="top">

NCLOB



</td>
<td valign="top">

Displays the property value.



</td>
</tr>
<tr>
<td valign="top">

IS\_READ\_ONLY



</td>
<td valign="top">

NVARCHAR\(5\)



</td>
<td valign="top">

Displays whether or not the property is read-only: TRUE/FALSE.



</td>
</tr>
</table>

**Related Information**  


[VIRTUAL\_TABLES System View](virtual-tables-system-view-21031a8.md "Provides information about virtual tables.")

[CREATE VIRTUAL TABLE Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/create-virtual-table-statement-data-definition-d2a0406.md "Creates a virtual table at a remote source.")

[ALTER VIRTUAL TABLE Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/alter-virtual-table-statement-data-definition-5182698.md "Modifies a virtual table's column properties, and lets you refresh the metadata of a virtual table.")

[VIRTUAL\_TABLE\_PARAMETERS System View](virtual-table-parameters-system-view-95054e1.md "Provides a list of parameters of the virtual tables that refer to column views in a remote SAP HANA database.")

[VIRTUAL\_TABLE\_PROPERTIES System View](virtual-table-properties-system-view-88396eb.md "Provides the properties set on virtual tables.")

[Managing Virtual Tables](https://help.sap.com/viewer/b6c0184b46cc424b9bcce8e6aae02f97/2023_2_QRC/en-US/d16e86e414b54cd0b6facd4f6a2e7e01.html "Virtual tables point to remote tables or views in a remote source. When SQL queries are executed on a virtual table, they access the remote data as if it were stored locally.") :arrow_upper_right:

[Create a Virtual Table](https://help.sap.com/viewer/b6c0184b46cc424b9bcce8e6aae02f97/2023_2_QRC/en-US/4ef3f55395dc47a89462b77b56d71f7f.html "Create a virtual table from the remote object of a remote source.") :arrow_upper_right:

[Delete a Virtual Table](https://help.sap.com/viewer/b6c0184b46cc424b9bcce8e6aae02f97/2023_2_QRC/en-US/ebcb10f2c2d44b3294dfb0cadd88c396.html "Delete an existing virtual table from your schema using the SAP HANA database explorer.") :arrow_upper_right:

[List All Virtual Tables](https://help.sap.com/viewer/b6c0184b46cc424b9bcce8e6aae02f97/2023_2_QRC/en-US/f4badb298616428ba585f68d4c68daa1.html "Provides a list of all virtual tables you have privilege to.") :arrow_upper_right:

[List Virtual Tables by Schema](https://help.sap.com/viewer/b6c0184b46cc424b9bcce8e6aae02f97/2023_2_QRC/en-US/682a0b4ee20349a0b36d3d940a6efaa0.html "Display the virtual tables of a remote source by schema using SQL syntax.") :arrow_upper_right:

[Refresh a Virtual Table](https://help.sap.com/viewer/b6c0184b46cc424b9bcce8e6aae02f97/2023_2_QRC/en-US/14ea22d516634790a29c2e3676dcb9b1.html "Update a virtual table to reflect metadata changes in the corresponding remote source table using SQL syntax.") :arrow_upper_right:

