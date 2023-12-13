<!-- loio3a827da524694d00a9d5f66e12935396 -->

# PINNED\_SQL\_PLANS System View

Provides information on currently pinned SQL plans and corresponding hints.



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

PINNED\_PLAN\_ID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the pinned ID.

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

Displays the volume ID.

</td>
</tr>
<tr>
<td valign="top">

USER\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of the user who prepared the plan.

</td>
</tr>
<tr>
<td valign="top">

SESSION\_USER\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the session user name who prepared the plan. This is the same value as displayed in the USER\_NAME column in the M\_CONNECTIONS monitored view.

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

Displays the schema name that the SQL plan belongs to.

</td>
</tr>
<tr>
<td valign="top">

STATEMENT\_STRING

</td>
<td valign="top">

NCLOB

</td>
<td valign="top">

Displays the statement string.

</td>
</tr>
<tr>
<td valign="top">

STATEMENT\_HASH

</td>
<td valign="top">

NVARCHAR\(32\)

</td>
<td valign="top">

Displays the MD5 hash value.

</td>
</tr>
<tr>
<td valign="top">

IS\_INTERNAL

</td>
<td valign="top">

TINYINT

</td>
<td valign="top">

Displays whether the plan is executed from a database internal connection or a remote connection: TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

ABAP\_VARCHAR\_MODE

</td>
<td valign="top">

TINYINT

</td>
<td valign="top">

Displays whether the value ABAP NVARCHAR mode is enabled: TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

PIN\_TIME

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the timestamp when the plan was pinned.

</td>
</tr>
<tr>
<td valign="top">

LAST\_MODIFY\_TIME

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the timestamp when the plan was modified.

</td>
</tr>
<tr>
<td valign="top">

HINT\_STRING

</td>
<td valign="top">

NCLOB

</td>
<td valign="top">

Displays the text string to indicate a hint was applied.

</td>
</tr>
<tr>
<td valign="top">

SESSION\_PROPERTIES

</td>
<td valign="top">

NVARCHAR\(500\)

</td>
<td valign="top">

Displays the composed variables from the session context.

</td>
</tr>
</table>



<a name="loio3a827da524694d00a9d5f66e12935396__section_dvv_rr4_dzb"/>

## Permissions

Unless otherwise specified, system views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all system views and their data regardless of the PUBLIC role and privilege grants.

**Related Information**  


[ALTER SYSTEM \{PIN | UNPIN\} SQL PLAN CACHE ENTRY Statement \(System Management\)](../../010-SQL-Reference/012-SQL-Statements/alter-system-pin-unpin-sql-plan-cache-entry-statement-system-management-68e2f7a.md "Provides a runtime mechanism to bind the target query and hints to the Hint Table to force the compilation of the target query with the hint.")

