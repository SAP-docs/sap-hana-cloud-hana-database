<!-- loio6d91840b7a6849a385b9e08400b81d97 -->

# ADAPTERS System View

Displays adapters available in the SAP HANA system.



<a name="loio6d91840b7a6849a385b9e08400b81d97__section_jft_ftn_bhb"/>

## Structure


<table>
<tr>
<th valign="top">

Column



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

ADAPTER\_NAME



</td>
<td valign="top">

NVARCHAR\(64\)



</td>
<td valign="top">

Displays the adapter name.



</td>
</tr>
<tr>
<td valign="top">

PROPERTIES



</td>
<td valign="top">

NVARCHAR\(1000\)



</td>
<td valign="top">

Displays the optional properties of the adapter such as display\_name and description.



</td>
</tr>
<tr>
<td valign="top">

CONFIGURATION



</td>
<td valign="top">

NCLOB



</td>
<td valign="top">

Displays the UI properties that must be displayed when configuring remote data source.



</td>
</tr>
<tr>
<td valign="top">

IS\_SYSTEM\_ADAPTER



</td>
<td valign="top">

NVARCHAR\(5\)



</td>
<td valign="top">

Displays whether the adapter is a system adapter: TRUE/FALSE.



</td>
</tr>
<tr>
<td valign="top">

IS\_ESS\_DEFINITION\_SUPPORTED



</td>
<td valign="top">

NVARCHAR\(5\)



</td>
<td valign="top">

Displays whether the procedure GET\_REMOTE\_SOURCE\_TABLE\_ESS\_DEFINITIONS is enabled for remote sources created using this adapter: TRUE/FALSE.



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

Displays the owner of the adapter.



</td>
</tr>
<tr>
<td valign="top">

HAS\_OBJECT\_PRIVILEGE



</td>
<td valign="top">

NVARCHAR\(5\)



</td>
<td valign="top">

Displays whether the adapter is authorized by object privileges: TRUE/FALSE.



</td>
</tr>
</table>



<a name="loio6d91840b7a6849a385b9e08400b81d97__section_y3k_lgj_k5b"/>

## Additional information

Owners, users granted the CREATE ADAPTER system privilege, or users having any privilege on such an adapter can see the new adapter. Users granted the ADAPTER ADMIN system privilege cannot see the new adapters.

**Related Information**  


[ADAPTER\_CAPABILITIES System View](adapter-capabilities-system-view-a1fcde3.md "Displays supported capabilities for each adapter.")

[ADAPTER\_LOCATIONS System View](adapter-locations-system-view-99d5ff2.md "Displays the location of adapters.")

[Create an SAP HANA Cloud, SAP HANA Database Remote Source](https://help.sap.com/viewer/b6c0184b46cc424b9bcce8e6aae02f97/2023_2_QRC/en-US/275839492fef49318d92d0e31656ea0a.html "Create a remote source to an SAP HANA database in another SAP HANA Cloud instance. You can also use this procedure for loopback scenarios or when creating a remote source from an SAP HANA on-premise system (SAP HANA 2.0 SPS 04 revision 45 or higher) to an SAP HANA database in SAP HANA Cloud.") :arrow_upper_right:

