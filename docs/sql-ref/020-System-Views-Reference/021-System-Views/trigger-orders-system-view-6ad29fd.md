<!-- loio6ad29fd74b424d97b4476f648e3385e7 -->

# TRIGGER\_ORDERS System View

Provides information about trigger order for triggers in the database.



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

REFERENCED\_SCHEMA\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the schema name of the referenced trigger.



</td>
</tr>
<tr>
<td valign="top">

REFERENCED\_TRIGGER\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the name of the referenced trigger.



</td>
</tr>
<tr>
<td valign="top">

REFERENCED\_TRIGGER\_OID



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the object ID of the referenced trigger.



</td>
</tr>
<tr>
<td valign="top">

ORDER\_TYPE



</td>
<td valign="top">

NVARCHAR\(10\)



</td>
<td valign="top">

Displays the type of ordering: FOLLOWS/PRECEDES.



</td>
</tr>
</table>

**Related Information**  


[TRIGGERS System View](triggers-system-view-2101f6d.md "Provides information about triggers that are defined for tables.")

[CREATE TRIGGER Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/create-trigger-statement-data-definition-20d5a65.md "Creates a trigger on a table or view.")

[DROP TRIGGER Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/drop-trigger-statement-data-definition-20d81ec.md "Deletes a trigger.")

