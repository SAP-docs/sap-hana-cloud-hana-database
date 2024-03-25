<!-- loio3df748d60e4343cb9937bdc76107def7 -->

# JWT\_PROVIDERS System View

Lists all of the JWT providers configured in the SAP HANA database.



<a name="loio3df748d60e4343cb9937bdc76107def7__section_y5v_3sd_rhb"/>

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

JWT\_PROVIDER\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of the JWT provider.

</td>
</tr>
<tr>
<td valign="top">

ISSUER\_NAME

</td>
<td valign="top">

NVARCHAR\(512\)

</td>
<td valign="top">

Displays the name in the issuer claim of the JWT tokens provided by this provider.

</td>
</tr>
<tr>
<td valign="top">

EXTERNAL\_IDENTITY\_CLAIM

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the claim provided in the JWT tokens to use when mapping the SAP HANA user to an external user name.

</td>
</tr>
<tr>
<td valign="top">

IS\_CASE\_SENSITIVE

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether the user mapping is case sensitive: TRUE/FALSE.

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

Displays the name of the owner of the provider.

</td>
</tr>
<tr>
<td valign="top">

PRIORITY

</td>
<td valign="top">

TINYINT

</td>
<td valign="top">

Displays the priority of the provider compared to other JWT providers with an identical issuer.

</td>
</tr>
<tr>
<td valign="top">

IS\_USER\_CREATION\_ENABLED

</td>
<td valign="top">

VARCHAR\(5\)

</td>
<td valign="top">

Displays whether the provider is allowed to create a user implicitly: TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

USER\_CREATION\_USER\_TYPE

</td>
<td valign="top">

VARCHAR\(10\)

</td>
<td valign="top">

Displays the type of user to create when user creation is enabled: STANDARD, RESTRICTED

</td>
</tr>
<tr>
<td valign="top">

USER\_CREATION\_USERGROUP

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the user group a created user will be a member of.

</td>
</tr>
</table>



<a name="loio3df748d60e4343cb9937bdc76107def7__section_snq_grb_dzb"/>

## Permissions

Unless otherwise specified, system views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all system views and their data regardless of the PUBLIC role and privilege grants.

**Related Information**  


[CREATE JWT PROVIDER Statement \(Access Control\)](../../010-SQL-Reference/012-SQL-Statements/create-jwt-provider-statement-access-control-bfe3daf.md "Defines a JWT provider in the SAP HANA database.")

[DROP JWT PROVIDER Statement \(Access Control\)](../../010-SQL-Reference/012-SQL-Statements/drop-jwt-provider-statement-access-control-e3caf68.md "Drops a JWT provider in the SAP HANA database.")

[ALTER JWT PROVIDER Statement \(Access Control\)](../../010-SQL-Reference/012-SQL-Statements/alter-jwt-provider-statement-access-control-61863f6.md "Alters a JWT provider in the SAP HANA database.")

[JWT\_USER\_MAPPINGS System View](jwt-user-mappings-system-view-49f380b.md "Lists all of the user-JWT mappings configured in the SAP HANA database.")

