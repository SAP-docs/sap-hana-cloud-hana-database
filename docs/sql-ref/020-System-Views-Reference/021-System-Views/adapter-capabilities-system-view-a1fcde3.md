<!-- loioa1fcde3545984c14a92cfb0143c3c7a6 -->

# ADAPTER\_CAPABILITIES System View

Displays supported capabilities for each adapter.



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

SOURCE\_VERSION



</td>
<td valign="top">

NVARCHAR\(64\)



</td>
<td valign="top">

Displays the source versions that are supported by the adapter.



</td>
</tr>
<tr>
<td valign="top">

CAPABILITY\_NAME



</td>
<td valign="top">

NVARCHAR\(128\)



</td>
<td valign="top">

Displays the capability name.



</td>
</tr>
<tr>
<td valign="top">

DESCRIPTION



</td>
<td valign="top">

NVARCHAR\(512\)



</td>
<td valign="top">

Displays the description of the capability.



</td>
</tr>
<tr>
<td valign="top">

SCOPE



</td>
<td valign="top">

NVARCHAR\(10\)



</td>
<td valign="top">

Displays the capability scope.



</td>
</tr>
<tr>
<td valign="top">

IS\_SDA\_SUPPORTED



</td>
<td valign="top">

NVARCHAR\(5\)



</td>
<td valign="top">

Displays whether the SDA capability is supported: TRUE/FALSE.



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

Displays whether the CDC capability is supported: TRUE/FALSE.



</td>
</tr>
</table>

**Related Information**  


[ADAPTERS System View](adapters-system-view-6d91840.md "Displays adapters available in the SAP HANA system.")

[ADAPTER\_LOCATIONS System View](adapter-locations-system-view-99d5ff2.md "Displays the location of adapters.")

