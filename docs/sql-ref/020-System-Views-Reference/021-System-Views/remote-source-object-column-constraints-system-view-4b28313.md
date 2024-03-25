<!-- loio4b28313c72904fc5a747e03693846140 -->

# REMOTE\_SOURCE\_OBJECT\_COLUMN\_CONSTRAINTS System View

Provides information on limitations that apply to remote source object columns.



<a name="loio4b28313c72904fc5a747e03693846140__section_t5g_1kl_thb"/>

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

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the user name.

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

OBJECT\_NAME

</td>
<td valign="top">

NVARCHAR\(5000\)

</td>
<td valign="top">

Displays the unique name to identify the remote source object.

</td>
</tr>
<tr>
<td valign="top">

COLUMN\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of the column.

</td>
</tr>
<tr>
<td valign="top">

POSITION

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the position of the column.

</td>
</tr>
<tr>
<td valign="top">

CONSTRAINT\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the constraint name.

</td>
</tr>
<tr>
<td valign="top">

IS\_PRIMARY\_KEY

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether or not the specified key is the primary key: TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

IS\_UNIQUE\_KEY

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether or not the specified key is unique: TRUE/FALSE.

</td>
</tr>
</table>



<a name="loio4b28313c72904fc5a747e03693846140__section_irn_fy4_dzb"/>

## Permissions

Unless otherwise specified, system views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all system views and their data regardless of the PUBLIC role and privilege grants.

**Related Information**  


[REMOTE\_SOURCES System View](remote-sources-system-view-20ccdd3.md "Provides information about remote sources.")

[REMOTE\_SUBSCRIPTIONS System View](remote-subscriptions-system-view-cf68b16.md "Lists all the remote subscriptions created for a remote source.")

[CREATE REMOTE SOURCE Statement \(Access Control\)](../../010-SQL-Reference/012-SQL-Statements/create-remote-source-statement-access-control-20d4834.md "Defines an external data source that can connect to the SAP HANA database.")

[ALTER REMOTE SOURCE Statement \(Access Control\)](../../010-SQL-Reference/012-SQL-Statements/alter-remote-source-statement-access-control-f423eb4.md "Modifies the configuration of an external data source that is connected to an SAP HANA database.")

[DROP REMOTE SOURCE Statement \(Access Control\)](../../010-SQL-Reference/012-SQL-Statements/drop-remote-source-statement-access-control-20d7332.md "Removes an existing remote source.")

[Creating Remote Sources (Smart Data Access)](https://help.sap.com/viewer/477aa413a36c4a95878460696fcc8896/2024_1_QRC/en-US/e8274a1cf62b4aa5b58f261bc904a4af.html "Create a smart data access remote source using SQL syntax or the SAP HANA database explorer.") :arrow_upper_right:

[Modify a Remote Source](https://help.sap.com/viewer/477aa413a36c4a95878460696fcc8896/2024_1_QRC/en-US/f523d7ab9d134a41b3bda1a603e82c4e.html "Modify an existing remote source.") :arrow_upper_right:

[Drop a Remote Source](https://help.sap.com/viewer/477aa413a36c4a95878460696fcc8896/2024_1_QRC/en-US/62e8556f45d443998bd86552f8398978.html "Remove an existing remote source.") :arrow_upper_right:

[List Remote Sources](https://help.sap.com/viewer/477aa413a36c4a95878460696fcc8896/2024_1_QRC/en-US/924e41fc417741fb9920705f15a8fbe0.html "Provides a list of remote sources you have privilege to.") :arrow_upper_right:

[Customizing Remote Source Behavior](https://help.sap.com/viewer/477aa413a36c4a95878460696fcc8896/2024_1_QRC/en-US/0a97fa4dbb3649ccaab43bcaee95345f.html "The supported behaviors of an SAP HANA smart data access remote source may not be the same as those of the local SAP HANA Cloud, SAP HANA database. Smart data access provides a set of customizable properties, capabilities, functions, and data types to help address these differences.") :arrow_upper_right:

[CONSTRAINTS System View](constraints-system-view-209f7cf.md "Provides information about defined constraints for tables.")

