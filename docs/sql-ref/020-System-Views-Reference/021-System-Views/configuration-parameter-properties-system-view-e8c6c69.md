<!-- loioe8c6c69d693b401bb8d9a35373ebbeb4 -->

# CONFIGURATION\_PARAMETER\_PROPERTIES System View

Displays metadata and properties of the public configuration parameters for SAP HANA.



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

SECTION

</td>
<td valign="top">

NVARCHAR\(128\)

</td>
<td valign="top">

Displays the section of the parameter to configure.

</td>
</tr>
<tr>
<td valign="top">

KEY

</td>
<td valign="top">

NVARCHAR\(128\)

</td>
<td valign="top">

Displays the parameter key.

</td>
</tr>
<tr>
<td valign="top">

HAS\_KEY\_INDEX

</td>
<td valign="top">

NVARCHAR\(9\)

</td>
<td valign="top">

Displays whether or not the parameter is indexed: NO, OPTIONAL, or MANDATORY.

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

Displays a description of the parameter.

</td>
</tr>
<tr>
<td valign="top">

DATA\_TYPE\_NAME

</td>
<td valign="top">

NVARCHAR\(32\)

</td>
<td valign="top">

Displays the data type of the parameter.

</td>
</tr>
<tr>
<td valign="top">

VALUE\_LIST\_SEPARATOR

</td>
<td valign="top">

NVARCHAR\(1\)

</td>
<td valign="top">

Displays the element separator character for value lists. Returns NULL for simple values.

</td>
</tr>
<tr>
<td valign="top">

DEFAULT\_VALUE

</td>
<td valign="top">

NVARCHAR\(5000\)

</td>
<td valign="top">

Displays the default value of the parameter.

</td>
</tr>
<tr>
<td valign="top">

RESTART\_REQUIRED

</td>
<td valign="top">

NVARCHAR\(8\)

</td>
<td valign="top">

Displays whether or not a restart is required. The values are: TRUE, FALSE, or CUSTOM. CUSTOM indicates a custom function or callback to decide whether a restart is required or not depending on the new value to be set.

</td>
</tr>
<tr>
<td valign="top">

INIFILE\_NAMES

</td>
<td valign="top">

NVARCHAR\(32\)

</td>
<td valign="top">

Displays the .ini files that can contain the parameter value, for example:<code>service.ini, <i class="varname">&lt;service&gt;</i>.ini, global.ini</code> 

</td>
</tr>
<tr>
<td valign="top">

UNIT

</td>
<td valign="top">

NVARCHAR\(16\)

</td>
<td valign="top">

Displays the unit that the value is measured in, for example, megabytes, kilobytes, seconds, and so on.

</td>
</tr>
<tr>
<td valign="top">

VALUE\_RESTRICTIONS

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the restrictions for the supported values.

</td>
</tr>
<tr>
<td valign="top">

CUSTOM\_RESTRICTIONS

</td>
<td valign="top">

NVARCHAR\(1024\)

</td>
<td valign="top">

Displays the description of the custom restriction, if one is defined.

</td>
</tr>
<tr>
<td valign="top">

LAYER\_RESTRICTIONS

</td>
<td valign="top">

NVARCHAR\(8\)

</td>
<td valign="top">

Displays the layer name if a parameter can only be set on specific layers: SYSTEM, HOST, or READONLY.

</td>
</tr>
<tr>
<td valign="top">

IS\_READ\_ONLY

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays if the parameter is set to read only.

</td>
</tr>
<tr>
<td valign="top">

IS\_SYSTEM\_MANAGED

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays if a parameter is managed internally by the system.

</td>
</tr>
<tr>
<td valign="top">

IS\_TEMPLATE

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether the configuration parameter templates or regular parameters are used: TRUE/FALSE.

</td>
</tr>
</table>



<a name="loioe8c6c69d693b401bb8d9a35373ebbeb4__section_pbd_11q_bzb"/>

## Permissions

Unless otherwise specified, system views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all system views and their data regardless of the PUBLIC role and privilege grants.

**Related Information**  


[SAP HANA Cloud Configuration Parameter Reference](https://help.sap.com/viewer/138dcf7d779543608917a2307a6115f2/2023_4_QRC/en-US/4b4d88980622427ab2d6ca8c05448166.html "Reference documentation for public configuration parameters in SAP HANA Cloud.") :arrow_upper_right:

