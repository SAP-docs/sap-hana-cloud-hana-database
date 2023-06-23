<!-- loio99d5ff2d7d234f0d9c379147ee6b941a -->

# ADAPTER\_LOCATIONS System View

Displays the location of adapters.



<a name="loio99d5ff2d7d234f0d9c379147ee6b941a__section_fpd_wtn_bhb"/>

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

LOCATION



</td>
<td valign="top">

NVARCHAR\(11\)



</td>
<td valign="top">

Displays the location of the adapter: 'indexserver', 'dpserver', 'agent'.



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

CONFIGURATION



</td>
<td valign="top">

NCLOB



</td>
<td valign="top">

Displays the configuration of the adapter.



</td>
</tr>
<tr>
<td valign="top">

PROPERTIES



</td>
<td valign="top">

NCLOB



</td>
<td valign="top">

Displays the properties of the adapter.



</td>
</tr>
</table>

**Related Information**  


[ADAPTERS System View](adapters-system-view-6d91840.md "Displays adapters available in the SAP HANA system.")

[ADAPTER\_CAPABILITIES System View](adapter-capabilities-system-view-a1fcde3.md "Displays supported capabilities for each adapter.")

