<!-- loiod8980f4706004249b6a36090a8061137 -->

# REMOTE\_USERS System View

Provides information about user mappings for cross-database access.



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

USER\_NAME

</td>
<td valign="top">

NVARCHAR \(256\)

</td>
<td valign="top">

Displays the name of the user in the local database.

</td>
</tr>
<tr>
<td valign="top">

REMOTE\_USER\_NAME

</td>
<td valign="top">

NVARCHAR \(256\)

</td>
<td valign="top">

Displays the name of the user in the remote database.

</td>
</tr>
<tr>
<td valign="top">

REMOTE\_DATABASE\_NAME

</td>
<td valign="top">

NVARCHAR \(256\)

</td>
<td valign="top">

Displays the name of the remote database.

</td>
</tr>
</table>



<a name="loiod8980f4706004249b6a36090a8061137__section_khm_vy4_dzb"/>

## Additional Information

Unless otherwise specified, system views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all system views and their data regardless of the PUBLIC role and privilege grants.

**Related Information**  


[REMOTE\_SOURCES System View](remote-sources-system-view-20ccdd3.md "Provides information about remote sources.")

[REMOTE\_SUBSCRIPTIONS System View](remote-subscriptions-system-view-cf68b16.md "Lists all the remote subscriptions created for a remote source.")

[CREATE USER Statement \(Access Control\)](../../010-SQL-Reference/012-SQL-Statements/create-user-statement-access-control-20d5ddb.md "Creates a new database user.")

[ALTER USER Statement \(Access Control\)](../../010-SQL-Reference/012-SQL-Statements/alter-user-statement-access-control-20d3459.md "Modifies the database user.")

[DROP USER Statement \(Access Control\)](../../010-SQL-Reference/012-SQL-Statements/drop-user-statement-access-control-20d8d33.md "Deletes a database user.")

