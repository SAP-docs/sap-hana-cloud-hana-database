<!-- loio2ce6f2191a044c4a99a351f12f573a3c -->

# GRAPH\_WORKSPACE\_COLUMNS System View

Provides information on the constituent entities and columns of graph workspaces.




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

The workspace schema name.



</td>
</tr>
<tr>
<td valign="top">

WORKSPACE\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

The workspace name.



</td>
</tr>
<tr>
<td valign="top">

ENTITY\_TYPE



</td>
<td valign="top">

NVARCHAR\(6\)



</td>
<td valign="top">

The entity type \(VERTEX or EDGE\).



</td>
</tr>
<tr>
<td valign="top">

ENTITY\_SCHEMA\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

The entity object schema name.



</td>
</tr>
<tr>
<td valign="top">

ENTITY\_TABLE\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

The entity object table or view name.



</td>
</tr>
<tr>
<td valign="top">

ENTITY\_COLUMN\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

The entity object column name.



</td>
</tr>
<tr>
<td valign="top">

ENTITY\_ROLE



</td>
<td valign="top">

NVARCHAR\(6\)



</td>
<td valign="top">

The role of column \(KEY, SOURCE, or TARGET. NULL for vertex or edge properties\).



</td>
</tr>
<tr>
<td valign="top">

ENTITY\_ROLE\_POSITION



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

The position of the column in a composite key, source, or target \(otherwise NULL\).



</td>
</tr>
<tr>
<td valign="top">

ENTITY\_LABEL



</td>
<td valign="top">

NVARCHAR\(5000\)



</td>
<td valign="top">

The explicitly defined label of the vertex or edge table the column belongs to \(otherwise NULL\).



</td>
</tr>
<tr>
<td valign="top">

REFERENCED\_SCHEMA\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

For the edge source and target columns, the schema name of the referenced vertex table \(NULL for all other columns\).



</td>
</tr>
<tr>
<td valign="top">

REFERENCED\_TABLE\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

For the edge source and target columns, the table name of the referenced vertex table \(NULL for all other columns\).



</td>
</tr>
</table>

**Related Information**  


[CREATE GRAPH WORKSPACE Statement (Data Definition)](https://help.sap.com/viewer/11afa2e60a5f4192a381df30f94863f9/2023_2_QRC/en-US/e6e1c7e2b9064b05b26572808f941ec4.html "Creates a graph workspace.") :arrow_upper_right:

[DROP GRAPH WORKSPACE Statement (Data Definition)](https://help.sap.com/viewer/11afa2e60a5f4192a381df30f94863f9/2023_2_QRC/en-US/88c7091e96c64b819898476536f7a849.html "Drops a graph workspace.") :arrow_upper_right:

[Object Privileges (Reference)](https://help.sap.com/viewer/c82f8d6a84c147f8b78bf6416dae7290/2023_2_QRC/en-US/8978bfdfcf3b45f9acf3fdb0964d3d9c.html "Object privileges are used to allow access to and modification of database objects, such as tables and views.") :arrow_upper_right:

[Graph Metadata Views](https://help.sap.com/viewer/11afa2e60a5f4192a381df30f94863f9/2023_2_QRC/en-US/5526e356098a40caa67e0e717dd85064.html "") :arrow_upper_right:

