<!-- loio0eff3c0e8970497c9973d828f08d40c2 -->

# M\_CONFIGURATION\_PARAMETER\_VALUES System View

Displays landscape service parameter values.



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
<tr>
<td valign="top">

SECTION

</td>
<td valign="top">

NVARCHAR\(128\)

</td>
<td valign="top">

Displays the section of the parameter.

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

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether or not the parameter is an indexed parameter: TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

FILE\_NAME

</td>
<td valign="top">

NVARCHAR\(16\)

</td>
<td valign="top">

Displays the name of the file where the parameter value is defined.

</td>
</tr>
<tr>
<td valign="top">

LAYER\_NAME

</td>
<td valign="top">

NVARCHAR\(8\)

</td>
<td valign="top">

Displays that layer that the parameter is defined on.

</td>
</tr>
<tr>
<td valign="top">

VALUE

</td>
<td valign="top">

NVARCHAR\(5000\)

</td>
<td valign="top">

Displays the parameter value.

</td>
</tr>
<tr>
<td valign="top">

HAS\_PROPERTIES

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether or not the parameter has properties: TRUE or FALSE.

</td>
</tr>
<tr>
<td valign="top">

RAW\_VALUE

</td>
<td valign="top">

NVARCHAR\(5000\)

</td>
<td valign="top">

Displays the value of the configuration parameter, as stored in the ini file.

</td>
</tr>
<tr>
<td valign="top">

VIOLATED\_RESTRICTIONS

</td>
<td valign="top">

NVARCHAR\(64\)

</td>
<td valign="top">

Displays the restrictions violated by the set value: CUSTOM, VALUE\_RESTRICTION, or LAYER\_RESTRICTION.

</td>
</tr>
<tr>
<td valign="top">

RESTART\_REQUIRED

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays if the parameter value has been changed and requires a restart to become effective: TRUE/FALSE.

</td>
</tr>
</table>

**Related Information**  


[CONFIGURATION\_PARAMETER\_PROPERTIES System View](../021-System-Views/configuration-parameter-properties-system-view-e8c6c69.md "Displays metadata and properties of the public configuration parameters for SAP HANA.")

[Configuration Parameters for the Table Consistency Check](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2023_4_QRC/en-US/49ff94736bb84e948321cb1e8cd1ca22.html "A set of configuration parameters in the indexserver.ini file is available to control the manual table consistency check.") :arrow_upper_right:

[ALTER SYSTEM ALTER CONFIGURATION Statement \(System Management\)](../../010-SQL-Reference/012-SQL-Statements/alter-system-alter-configuration-statement-system-management-20d08a5.md "Sets or removes configuration parameters in an INI file.")

