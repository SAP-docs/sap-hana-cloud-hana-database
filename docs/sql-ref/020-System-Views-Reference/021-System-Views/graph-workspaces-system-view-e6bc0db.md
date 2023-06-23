<!-- loioe6bc0dbdb0a142eaaa39819848ae29ad -->

# GRAPH\_WORKSPACES System View

Provides information about graph workspaces in the database.




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

NVARCHAR \(256\)



</td>
<td valign="top">

Displays the name of the schema the workspace resides in.



</td>
</tr>
<tr>
<td valign="top">

WORKSPACE\_NAME



</td>
<td valign="top">

NVARCHAR \(256\)



</td>
<td valign="top">

Displays the workspace name.



</td>
</tr>
<tr>
<td valign="top">

CREATE\_TIMESTAMP



</td>
<td valign="top">

TIMESTAMP



</td>
<td valign="top">

Displays the workspace creation timestamp.



</td>
</tr>
<tr>
<td valign="top">

USER\_NAME



</td>
<td valign="top">

NVARCHAR \(256\)



</td>
<td valign="top">

Displays the workspace creator user name.



</td>
</tr>
<tr>
<td valign="top">

IS\_VALID



</td>
<td valign="top">

NVARCHAR \(5\)



</td>
<td valign="top">

Displays whether this workspace is valid: TRUE/FALSE.



</td>
</tr>
</table>

**Related Information**  


[CREATE GRAPH WORKSPACE Statement (Data Definition)](https://help.sap.com/viewer/11afa2e60a5f4192a381df30f94863f9/2023_2_QRC/en-US/e6e1c7e2b9064b05b26572808f941ec4.html "Creates a graph workspace.") :arrow_upper_right:

[DROP GRAPH WORKSPACE Statement (Data Definition)](https://help.sap.com/viewer/11afa2e60a5f4192a381df30f94863f9/2023_2_QRC/en-US/88c7091e96c64b819898476536f7a849.html "Drops a graph workspace.") :arrow_upper_right:

[Object Privileges (Reference)](https://help.sap.com/viewer/c82f8d6a84c147f8b78bf6416dae7290/2023_2_QRC/en-US/8978bfdfcf3b45f9acf3fdb0964d3d9c.html "Object privileges are used to allow access to and modification of database objects, such as tables and views.") :arrow_upper_right:

