<!-- loio49f380b049a243f48873d52707504f57 -->

# JWT\_USER\_MAPPINGS System View

Lists all of the user-JWT mappings configured in the SAP HANA database.



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

Displays the SAP HANA user name.



</td>
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

EXTERNAL\_IDENTITY



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the name of the user known to the JWT provider.



</td>
</tr>
</table>

**Related Information**  


[CREATE JWT PROVIDER Statement \(Access Control\)](../../010-SQL-Reference/012-SQL-Statements/create-jwt-provider-statement-access-control-bfe3daf.md "Defines a JWT provider in the SAP HANA database.")

[DROP JWT PROVIDER Statement \(Access Control\)](../../010-SQL-Reference/012-SQL-Statements/drop-jwt-provider-statement-access-control-e3caf68.md "Drops a JWT provider in the SAP HANA database.")

[ALTER JWT PROVIDER Statement \(Access Control\)](../../010-SQL-Reference/012-SQL-Statements/alter-jwt-provider-statement-access-control-61863f6.md "Alters a JWT provider in the SAP HANA database.")

[JWT\_PROVIDERS System View](jwt-providers-system-view-3df748d.md "Lists all of the JWT providers configured in the SAP HANA database.")

