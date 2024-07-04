<!-- loio5c745caa0d424a9aa4803c8d6d3d81fe -->

# M\_MANAGED\_PSES System View

Provides information about managed personal security environments \(managed PSEs\).



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

PSE\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of the Managed PSE.

</td>
</tr>
<tr>
<td valign="top">

MANAGER\_TYPE

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the content provider for this Manged PSE.

</td>
</tr>
<tr>
<td valign="top">

LAST\_UPDATE

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the time, when the content of the Managed PSE was last changed.

</td>
</tr>
<tr>
<td valign="top">

LAST\_CHECK

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the time, when the content provider of the Managed PSE was last checked for an update.

</td>
</tr>
<tr>
<td valign="top">

LAST\_CHECK\_STATUS

</td>
<td valign="top">

NVARCHAR\(8\)

</td>
<td valign="top">

Displays the result of the last check of the Managed PSE.

</td>
</tr>
<tr>
<td valign="top">

LAST\_CHECK\_DETAILS

</td>
<td valign="top">

NVARCHAR\(5000\)

</td>
<td valign="top">

Displays the details of the last check of the Managed PSE.

</td>
</tr>
</table>



## Permissions

Unless otherwise specified, system views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all system views and their data regardless of the PUBLIC role and privilege grants.

**Related Information**  


[ALTER PSE Statement \(System Management\)](../../010-SQL-Reference/012-SQL-Statements/alter-pse-statement-system-management-9c22c6f.md "Modifies a PSE.")

[CREATE PSE Statement \(System Management\)](../../010-SQL-Reference/012-SQL-Statements/create-pse-statement-system-management-4d80bf6.md "Creates a personal security environment (PSE).")

[DROP PSE Statement \(System Management\)](../../010-SQL-Reference/012-SQL-Statements/drop-pse-statement-system-management-25d6795.md "Drops a PSE.")

[REFRESH PSE Statement \(System Management\)](../../010-SQL-Reference/012-SQL-Statements/refresh-pse-statement-system-management-c2f1007.md "Refreshes a managed PSE.")

[SET PSE Statement \(System Management\)](../../010-SQL-Reference/012-SQL-Statements/set-pse-statement-system-management-10fe807.md "Sets the purpose of a PSE, which is the type of trust validation for the PSE to use.")

[UNSET PSE Statement \(System Management\)](../../010-SQL-Reference/012-SQL-Statements/unset-pse-statement-system-management-4082553.md "Remove the assigned purpose for a PSE along with any assigned objects.")

