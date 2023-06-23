<!-- loio20ccdd3975191014af6fc087f30c56da -->

# REMOTE\_SOURCES System View

Provides information about remote sources.



<a name="loio20ccdd3975191014af6fc087f30c56da___r_e_m_o_t_e__s_o_u_r_c_e_s_1struct_REMOTE_SOURCES"/>

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

REMOTE\_SOURCE\_OID



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the remote source OID..



</td>
</tr>
<tr>
<td valign="top">

REMOTE\_SOURCE\_SCHEMA\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the schema name of the remote source object.



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

ADAPTER\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the adapter name.



</td>
</tr>
<tr>
<td valign="top">

CONNECTION\_INFO



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the connection information.



</td>
</tr>
<tr>
<td valign="top">

LOCATION



</td>
<td valign="top">

NVARCHAR\(11\)



</td>
<td valign="top">

Displays the adapter location



</td>
</tr>
<tr>
<td valign="top">

AGENT\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the agent name.



</td>
</tr>
<tr>
<td valign="top">

IS\_CDC\_SUPPORTED



</td>
<td valign="top">

NVARCHAR\(5\)



</td>
<td valign="top">

Displays whether or not the CDC is supported: TRUE/FALSE.



</td>
</tr>
<tr>
<td valign="top">

IS\_REFRESH\_OBJECTS\_SUPPORTED



</td>
<td valign="top">

NVARCHAR\(5\)



</td>
<td valign="top">

Displays whether or not refresh objects is supported: TRUE/FALSE.



</td>
</tr>
<tr>
<td valign="top">

AGENT\_GROUP\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the agent group name.



</td>
</tr>
<tr>
<td valign="top">

IS\_TREE



</td>
<td valign="top">

NVARCHAR\(5\)



</td>
<td valign="top">

Displays whether or not the browsing hierarchy is deeply nested: TRUE/FALSE.



</td>
</tr>
<tr>
<td valign="top">

IS\_LINKED\_DATABASE\_SUPPORTED



</td>
<td valign="top">

NVARCHAR\(5\)



</td>
<td valign="top">

Displays whether or not the linked database is supported for this remote source: TRUE/FALSE.



</td>
</tr>
<tr>
<td valign="top">

CCM\_CONNECTION\_ID



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the CCM connection ID.



</td>
</tr>
<tr>
<td valign="top">

CCM\_CONNECTION\_VERSION



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the CCM connection VERSION.



</td>
</tr>
</table>

**Related Information**  


[CREATE REMOTE SOURCE Statement \(Access Control\)](../../010-SQL-Reference/012-SQL-Statements/create-remote-source-statement-access-control-20d4834.md "Defines an external data source that can connect to the SAP HANA database.")

[ALTER REMOTE SOURCE Statement \(Access Control\)](../../010-SQL-Reference/012-SQL-Statements/alter-remote-source-statement-access-control-f423eb4.md "Modifies the configuration of an external data source that is connected to an SAP HANA database.")

[DROP REMOTE SOURCE Statement \(Access Control\)](../../010-SQL-Reference/012-SQL-Statements/drop-remote-source-statement-access-control-20d7332.md "Removes an existing remote source.")

[Creating Remote Sources (Smart Data Access)](https://help.sap.com/viewer/b6c0184b46cc424b9bcce8e6aae02f97/2023_2_QRC/en-US/e8274a1cf62b4aa5b58f261bc904a4af.html "Create a smart data access remote source using SQL syntax or the SAP HANA database explorer.") :arrow_upper_right:

[Modify a Remote Source](https://help.sap.com/viewer/b6c0184b46cc424b9bcce8e6aae02f97/2023_2_QRC/en-US/f523d7ab9d134a41b3bda1a603e82c4e.html "Modify an existing remote source.") :arrow_upper_right:

[Drop a Remote Source](https://help.sap.com/viewer/b6c0184b46cc424b9bcce8e6aae02f97/2023_2_QRC/en-US/62e8556f45d443998bd86552f8398978.html "Remove an existing remote source.") :arrow_upper_right:

[List Remote Sources](https://help.sap.com/viewer/b6c0184b46cc424b9bcce8e6aae02f97/2023_2_QRC/en-US/924e41fc417741fb9920705f15a8fbe0.html "Provides a list of remote sources you have privilege to.") :arrow_upper_right:

[Customizing Remote Source Behavior](https://help.sap.com/viewer/b6c0184b46cc424b9bcce8e6aae02f97/2023_2_QRC/en-US/0a97fa4dbb3649ccaab43bcaee95345f.html "The supported behaviors of an SAP HANA smart data access remote source may not be the same as those of the local SAP HANA Cloud, SAP HANA database. Smart data access provides a set of customizable properties, capabilities, functions, and data types to help address these differences.") :arrow_upper_right:

