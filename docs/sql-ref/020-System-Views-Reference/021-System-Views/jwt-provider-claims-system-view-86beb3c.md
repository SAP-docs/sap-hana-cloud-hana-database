<!-- loio86beb3c3974b415dbc0850afba1492b5 -->

# JWT\_PROVIDER\_CLAIMS System View

Lists the additional claims with its values for the JWT provider.



<a name="loio86beb3c3974b415dbc0850afba1492b5__section_y5v_3sd_rhb"/>

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

CLAIM



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the name of the claim.



</td>
</tr>
<tr>
<td valign="top">

OPERATION



</td>
<td valign="top">

NVARCHAR\(64\)



</td>
<td valign="top">

Specifies how the claim is used. Operation include: EQUALS, HAS MEMBER, SET APPLICATION USER.



</td>
</tr>
<tr>
<td valign="top">

VALUE



</td>
<td valign="top">

NVARCHAR\(512\)



</td>
<td valign="top">

Display the expected value of the claim in a JWT token.



</td>
</tr>
</table>



<a name="loio86beb3c3974b415dbc0850afba1492b5__section_bbs_ppd_tfb"/>

## Permissions

Users must have rights to the JWT provider to see the claims in this view.

**Related Information**  


[CREATE JWT PROVIDER Statement \(Access Control\)](../../010-SQL-Reference/012-SQL-Statements/create-jwt-provider-statement-access-control-bfe3daf.md "Defines a JWT provider in the SAP HANA database.")

[DROP JWT PROVIDER Statement \(Access Control\)](../../010-SQL-Reference/012-SQL-Statements/drop-jwt-provider-statement-access-control-e3caf68.md "Drops a JWT provider in the SAP HANA database.")

[ALTER JWT PROVIDER Statement \(Access Control\)](../../010-SQL-Reference/012-SQL-Statements/alter-jwt-provider-statement-access-control-61863f6.md "Alters a JWT provider in the SAP HANA database.")

[JWT\_USER\_MAPPINGS System View](jwt-user-mappings-system-view-49f380b.md "Lists all of the user-JWT mappings configured in the SAP HANA database.")

