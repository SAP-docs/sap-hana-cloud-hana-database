<!-- loio3769f7f1d32d4ec599c49389a944db3e -->

# M\_AFL\_STATES System View

Provides information about AFL states.



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

STATE\_ID

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the ID of the state.

</td>
</tr>
<tr>
<td valign="top">

AREA\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of the area.

</td>
</tr>
<tr>
<td valign="top">

DESCRIPTION

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the state description.

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

Displays the time when the state was created.

</td>
</tr>
<tr>
<td valign="top">

LAST\_ACCESS\_TIMESTAMP

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the time stamp of the last access.

</td>
</tr>
<tr>
<td valign="top">

HOST

</td>
<td valign="top">

NVARCHAR\(64\)

</td>
<td valign="top">

Displays the host name.

</td>
</tr>
<tr>
<td valign="top">

PORT

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the internal port.

</td>
</tr>
</table>



<a name="loio3769f7f1d32d4ec599c49389a944db3e__section_bd4_sh2_qbc"/>

## Permissions

Unless otherwise specified, monitoring views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all monitoring views and their data regardless of the PUBLIC role and privilege grants.

**Related Information**  


[M\_AFL\_FUNCTIONS System View](m-afl-functions-system-view-654db9b.md "Provides application function execution information.")

[AFL\_FUNCTIONS System View](../021-System-Views/afl-functions-system-view-209d7b2.md "Provides information about available AFL functions.")

[AFL\_FUNCTION\_PARAMETERS System View](../021-System-Views/afl-function-parameters-system-view-d1fce26.md "Provides information about parameters of AFL functions.")

[AFL\_PACKAGES System View](../021-System-Views/afl-packages-system-view-209dae2.md "Provides information about available AFL packages.")

[AFL\_TEXTS System View](../021-System-Views/afl-texts-system-view-d1fd8aa.md "Provides information about available AFL texts.")

[AFL\_FUNCTION\_PROPERTIES System View](../021-System-Views/afl-function-properties-system-view-209d4b7.md "Provides information about available AFL function properties.")

