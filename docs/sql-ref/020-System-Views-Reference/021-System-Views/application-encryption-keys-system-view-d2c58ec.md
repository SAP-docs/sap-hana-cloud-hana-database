<!-- loiod2c58ec7cb42470b976165d7df144291 -->

# APPLICATION\_ENCRYPTION\_KEYS System View

Provides information about encryption keys used by applications.



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

COMPONENT

</td>
<td valign="top">

NVARCHAR\(20\)

</td>
<td valign="top">

Displays the component that the key belongs to.

</td>
</tr>
<tr>
<td valign="top">

SUB\_COMPONENT

</td>
<td valign="top">

NVARCHAR\(512\)

</td>
<td valign="top">

Displays the subcomponent that the key belongs to.

</td>
</tr>
<tr>
<td valign="top">

CREATOR

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the database user or the internal subcomponent that created the key.

</td>
</tr>
<tr>
<td valign="top">

CREATE\_TIMESTAMP

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the timestamp when the key was created.

</td>
</tr>
<tr>
<td valign="top">

IS\_CURRENT

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether the key is used by the subcomponent for newly encrypted data: TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

ENCRYPTION\_ALGORITHM

</td>
<td valign="top">

NVARCHAR\(16\)

</td>
<td valign="top">

Displays the algorithm associated with this key.

</td>
</tr>
</table>



<a name="loiod2c58ec7cb42470b976165d7df144291__section_ejx_pjc_bzb"/>

## Permissions

Unless otherwise specified, system views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all system views and their data regardless of the PUBLIC role and privilege grants.

**Related Information**  


[M\_ENCRYPTION\_OVERVIEW System View](../022-Monitoring-Views/m-encryption-overview-system-view-ee1a50a.md "Reports the encryption status for all data at rest where encryption is supported.")

[ALTER SYSTEM APPLICATION ENCRYPTION Statement \(System Management\)](../../010-SQL-Reference/012-SQL-Statements/alter-system-application-encryption-statement-system-management-f425959.md "Manages encryption keys for applications that use the internal data encryption service.")

