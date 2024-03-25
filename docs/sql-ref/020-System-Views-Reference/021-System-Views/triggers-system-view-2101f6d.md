<!-- loio2101f6db7519101493d39a89898b9480 -->

# TRIGGERS System View

Provides information about triggers that are defined for tables.



<a name="loio2101f6db7519101493d39a89898b9480___t_r_i_g_g_e_r_s_1struct_TRIGGERS"/>

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

Displays the schema name of the trigger.

</td>
</tr>
<tr>
<td valign="top">

TRIGGER\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the trigger name.

</td>
</tr>
<tr>
<td valign="top">

TRIGGER\_OID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the object ID of the trigger.

</td>
</tr>
<tr>
<td valign="top">

OWNER\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of the trigger owner.

</td>
</tr>
<tr>
<td valign="top">

OWNER\_OID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the object ID of the trigger owner.

</td>
</tr>
<tr>
<td valign="top">

SUBJECT\_TABLE\_SCHEMA

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the schema name of the table, the trigger is defined for.

</td>
</tr>
<tr>
<td valign="top">

SUBJECT\_TABLE\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the table name of the table, the trigger is defined for.

</td>
</tr>
<tr>
<td valign="top">

TRIGGER\_ACTION\_TIME

</td>
<td valign="top">

NVARCHAR\(10\)

</td>
<td valign="top">

Displays the time the trigger is executed: BEFORE, AFTER, or INSTEAD OF the specified event.

</td>
</tr>
<tr>
<td valign="top">

TRIGGER\_EVENT

</td>
<td valign="top">

NVARCHAR\(20\)

</td>
<td valign="top">

Displays the event the trigger is defined for: combination of DELETE, INSERT, or UPDATE.

</td>
</tr>
<tr>
<td valign="top">

TRIGGERED\_ACTION\_LEVEL

</td>
<td valign="top">

NVARCHAR\(9\)

</td>
<td valign="top">

Displays the level of the event where the triggered action happens: ROW/STATEMENT.

</td>
</tr>
<tr>
<td valign="top">

DEFINITION

</td>
<td valign="top">

NCLOB

</td>
<td valign="top">

Displays the query string of the trigger.

</td>
</tr>
<tr>
<td valign="top">

IS\_VALID

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether the trigger is valid or not: TRUE/FALSE. This becomes FALSE when its base objects are changed or dropped.

</td>
</tr>
<tr>
<td valign="top">

IS\_ENABLED

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether the trigger is enabled or not: TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

CREATE\_TIME

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the time that the trigger was created.

</td>
</tr>
</table>



<a name="loio2101f6db7519101493d39a89898b9480__section_eyy_tqv_11c"/>

## Permissions

Unless otherwise specified, system views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all system views and their data regardless of the PUBLIC role and privilege grants.

**Related Information**  


[TRIGGER\_ORDERS System View](trigger-orders-system-view-6ad29fd.md "Provides information about trigger order for triggers in the database.")

[CREATE TRIGGER Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/create-trigger-statement-data-definition-20d5a65.md "Creates a trigger on a table or view.")

[DROP TRIGGER Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/drop-trigger-statement-data-definition-20d81ec.md "Deletes a trigger.")

