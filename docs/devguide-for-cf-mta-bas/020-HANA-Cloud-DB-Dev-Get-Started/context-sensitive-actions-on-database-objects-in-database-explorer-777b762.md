<!-- loio777b7623ca9c4fb58b27ad9f2d5284a8 -->

# Context-sensitive Actions on Database Objects in Database Explorer

A list of available context-sensitive actions that can be performed on SAP HANA database objects in the database explorer.



The Database Explorer embedded in the SAP HANA Native Application extension enables you to perform actions on database objects. When you right-click a database object in the Database Explorer's *CATALOG BROWSER* pane, the context-sensitive menu displayed enables you to perform the following actions:


<table>
<tr>
<th valign="top">

Menu Option

</th>
<th valign="top">

Action

</th>
<th valign="top">

Note!

</th>
</tr>
<tr>
<td valign="top">

*Open Data*

</td>
<td valign="top">

Open the SQL console, and display the results of the data-preview SQL query that is run on the selected database artifact.

</td>
<td valign="top">

The option is only available with:

-   Tables
-   Views
-   Column views
-   Synonyms \(except synonyms of procedures\)
-   Public synonyms \(except synonyms of procedures\)



</td>
</tr>
<tr>
<td valign="top">

*Copy Name*

</td>
<td valign="top">

Copy the name of the selected database object to the clipboard

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

*Copy Full Name*

</td>
<td valign="top">

Copy to the clipboard not only the name of the selected database object but also the name of the database schema in which the object is located.

</td>
<td valign="top">

If the object is a global object without a schema, only the object name is copied.

</td>
</tr>
<tr>
<td valign="top">

*Generate CREATE Statement*

</td>
<td valign="top">

Display the SQL statement used to **create** the selected database object in a new SQL console.

</td>
<td valign="top">

This operation is only available on schema-local objects.

</td>
</tr>
<tr>
<td valign="top">

*Copy CREATE Statement*

</td>
<td valign="top">

Copy to the clipboard the SQL statement used to create the selected database object.

</td>
<td valign="top">

This operation is only available on schema-local objects.

</td>
</tr>
<tr>
<td valign="top">

*Generate SELECT Statement*

</td>
<td valign="top">

Copy the SQL statement used to **select** the database object and display it in a new SQL console, where you can run the `SELECT` statement and view the results.

</td>
<td valign="top">

The option is only available with:

-   Tables
-   Views
-   Column views
-   Synonyms \(except synonyms of procedures\)
-   Public synonyms \(except synonyms of procedures\)
-   Functions



</td>
</tr>
<tr>
<td valign="top">

*Generate INSERT Statement*

</td>
<td valign="top">

Copy the SQL statement used to **insert** the database object and display it in a new SQL console, where you can run the `INSERT` statement and view the results.

</td>
<td valign="top">

The option is only available with:

-   Tables



</td>
</tr>
<tr>
<td valign="top">

*Generate CALL Statement*

</td>
<td valign="top">

Display the SQL statement used to **call** the selected database object in a new SQL console, where you can run the `CALL` statement on the chosen database artifact \(for example, a procedure\) and view the results.

</td>
<td valign="top">

The option is only available with:

-   Procedures
-   Synonyms of procedures



</td>
</tr>
<tr>
<td valign="top">

*Generate CALL Statement with UI*

</td>
<td valign="top">

Display the SQL statement used to **call** the selected database object in the graphical user interface \(GUI\), where you can run the `CALL` statement on the chosen database object \(for example, a procedure\), provide any parameter values that are required, and view the results.

</td>
<td valign="top">

The option is only available with:

-   Procedures
-   Synonyms of procedures

> ### Tip:  
> Some types of procedure cannot be called with the GUI, for example, procedures with parameters that reference user-defined types \(`TABLE_TYPE`\). In these cases, you must run the procedure without the GUI.



</td>
</tr>
<tr>
<td valign="top">

*Open Dependency Viewer*

</td>
<td valign="top">

Display a graphical representation of the connections between the currently selected object and any dependendent objects, for example, between a database procedure, table, view, and analytic privilege.

</td>
<td valign="top">

If the selected object does not have any dependencies, no graph is displayed.

> ### Tip:  
> See *Related Information* below for more information about how to use this feature.



</td>
</tr>
</table>

**Related Information**  


[View Database Objects with the Database Explorer](view-database-objects-with-the-database-explorer-0e5ac0b.md "Check the contents of your database with SAP HANA Database Explorer.")

