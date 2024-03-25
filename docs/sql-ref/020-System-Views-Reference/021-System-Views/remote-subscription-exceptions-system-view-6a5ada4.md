<!-- loio6a5ada48bd1e46f4849ce9c90a09d84b -->

# REMOTE\_SUBSCRIPTION\_EXCEPTIONS System View

Provides remote subscription exception information.



<a name="loio6a5ada48bd1e46f4849ce9c90a09d84b__section_oph_vfs_thb"/>

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

EXCEPTION\_OID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the exception ID.

</td>
</tr>
<tr>
<td valign="top">

OBJECT\_TYPE

</td>
<td valign="top">

NVARCHAR\(19\)

</td>
<td valign="top">

Displays the object type: REMOTE\_SOURCE/REMOTE\_SUBSCRIPTION.

</td>
</tr>
<tr>
<td valign="top">

OBJECT\_SCHEMA\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the schema name of the remote source or the remote subscription, based on the OBJECT\_TYPE.

</td>
</tr>
<tr>
<td valign="top">

OBJECT\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the object name of the remote source or remote subscription, based on the OBJECT\_TYPE.

</td>
</tr>
<tr>
<td valign="top">

EXCEPTION\_TIME

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the time when the exception was raised.

</td>
</tr>
<tr>
<td valign="top">

ERROR\_NUMBER

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the error number.

</td>
</tr>
<tr>
<td valign="top">

ERROR\_MESSAGE

</td>
<td valign="top">

NVARCHAR\(2000\)

</td>
<td valign="top">

Displays the error message.

</td>
</tr>
<tr>
<td valign="top">

COMPONENT

</td>
<td valign="top">

NVARCHAR\(11\)

</td>
<td valign="top">

Displays the component that raised the exception.

</td>
</tr>
</table>



<a name="loio6a5ada48bd1e46f4849ce9c90a09d84b__section_atm_py4_dzb"/>

## Permissions

Unless otherwise specified, system views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all system views and their data regardless of the PUBLIC role and privilege grants.

**Related Information**  


[REMOTE\_SOURCES System View](remote-sources-system-view-20ccdd3.md "Provides information about remote sources.")

[REMOTE\_SUBSCRIPTIONS System View](remote-subscriptions-system-view-cf68b16.md "Lists all the remote subscriptions created for a remote source.")

[REMOTE\_SUBSCRIPTION\_DATA\_CONTAINERS System View](remote-subscription-data-containers-system-view-9289305.md "Provides information regarding remote subscription data.")

[REMOTE\_USERS System View](remote-users-system-view-d8980f4.md "Provides information about user mappings for cross-database access.")

[CREATE REMOTE SUBSCRIPTION Statement \[Smart Data Integration\]](https://help.sap.com/viewer/7952ef28a6914997abc01745fef1b607/latest/en-US/12d89b67c7994f80bc516e30dadd3c0a.html)

[ALTER REMOTE SUBSCRIPTION Statement \[Smart Data Integration\]](https://help.sap.com/viewer/7952ef28a6914997abc01745fef1b607/latest/en-US/f88b70b3170849b0a57d4ff618887dce.html)

[DROP REMOTE SUBSCRIPTION Statement \[Smart Data Integration\]](https://help.sap.com/viewer/7952ef28a6914997abc01745fef1b607/latest/en-US/af65fc25d26c4968ac1448cf13056432.html)

