<!-- loioae89f25f4a4140f0b712e3b07f62f6a8 -->

# REMOTE\_SOURCE\_OBJECT\_COLUMN\_DESCRIPTIONS System View

Provides remote source object column description information.



<a name="loioae89f25f4a4140f0b712e3b07f62f6a8__section_ux2_3kl_thb"/>

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

LANGUAGE\_CODE



</td>
<td valign="top">

NVARCHAR\(2\)



</td>
<td valign="top">

Displays the language code.



</td>
</tr>
<tr>
<td valign="top">

DESCRIPTION



</td>
<td valign="top">

NVARCHAR\(5000\)



</td>
<td valign="top">

Displays the description of the specified column.



</td>
</tr>
</table>

**Related Information**  


[REMOTE\_SOURCES System View](remote-sources-system-view-20ccdd3.md "Provides information about remote sources.")

[REMOTE\_SUBSCRIPTIONS System View](remote-subscriptions-system-view-cf68b16.md "Lists all the remote subscriptions created for a remote source.")

[REMOTE\_SUBSCRIPTION\_DATA\_CONTAINERS System View](remote-subscription-data-containers-system-view-9289305.md "Provides information regarding remote subscription data.")

[CREATE REMOTE SOURCE Statement \(Access Control\)](../../010-SQL-Reference/012-SQL-Statements/create-remote-source-statement-access-control-20d4834.md "Defines an external data source that can connect to the SAP HANA database.")

[ALTER REMOTE SOURCE Statement \(Access Control\)](../../010-SQL-Reference/012-SQL-Statements/alter-remote-source-statement-access-control-f423eb4.md "Modifies the configuration of an external data source that is connected to an SAP HANA database.")

[DROP REMOTE SOURCE Statement \(Access Control\)](../../010-SQL-Reference/012-SQL-Statements/drop-remote-source-statement-access-control-20d7332.md "Removes an existing remote source.")

[Creating Remote Sources (Smart Data Access)](https://help.sap.com/viewer/b6c0184b46cc424b9bcce8e6aae02f97/2023_2_QRC/en-US/e8274a1cf62b4aa5b58f261bc904a4af.html "Create a smart data access remote source using SQL syntax or the SAP HANA database explorer.") :arrow_upper_right:

[Modify a Remote Source](https://help.sap.com/viewer/b6c0184b46cc424b9bcce8e6aae02f97/2023_2_QRC/en-US/f523d7ab9d134a41b3bda1a603e82c4e.html "Modify an existing remote source.") :arrow_upper_right:

[Drop a Remote Source](https://help.sap.com/viewer/b6c0184b46cc424b9bcce8e6aae02f97/2023_2_QRC/en-US/62e8556f45d443998bd86552f8398978.html "Remove an existing remote source.") :arrow_upper_right:

[List Remote Sources](https://help.sap.com/viewer/b6c0184b46cc424b9bcce8e6aae02f97/2023_2_QRC/en-US/924e41fc417741fb9920705f15a8fbe0.html "Provides a list of remote sources you have privilege to.") :arrow_upper_right:

[Customizing Remote Source Behavior](https://help.sap.com/viewer/b6c0184b46cc424b9bcce8e6aae02f97/2023_2_QRC/en-US/0a97fa4dbb3649ccaab43bcaee95345f.html "The supported behaviors of an SAP HANA smart data access remote source may not be the same as those of the local SAP HANA Cloud, SAP HANA database. Smart data access provides a set of customizable properties, capabilities, functions, and data types to help address these differences.") :arrow_upper_right:
