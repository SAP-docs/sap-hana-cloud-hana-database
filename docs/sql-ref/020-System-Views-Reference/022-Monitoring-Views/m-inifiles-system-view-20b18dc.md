<!-- loio20b18dc475191014831bcf1d714840d5 -->

# M\_INIFILES System View

Provides information about all configuration files.



<a name="loio20b18dc475191014831bcf1d714840d5___m__i_n_i_f_i_l_e_s_1struct_M_INIFILES"/>

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

FILE\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the configuration file name.

</td>
</tr>
<tr>
<td valign="top">

DEFAULT\_LAYER

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Indicates whether or not the file has configuration on the default layer. This value is always TRUE.

</td>
</tr>
<tr>
<td valign="top">

SYSTEM\_LAYER

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Indicates whether or not the file has configuration on the system layer: TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

DATABASE\_LAYER

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Indicates whether or not the file has configuration on the database layer: TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

HOST\_LAYER

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Indicates whether or not the file has configuration on the host layer: TRUE/FALSE.

</td>
</tr>
</table>



<a name="loio20b18dc475191014831bcf1d714840d5__section_tw4_txz_xbc"/>

## Permissions

Unless otherwise specified, monitoring views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all monitoring views and their data regardless of the PUBLIC role and privilege grants.



<a name="loio20b18dc475191014831bcf1d714840d5___m__i_n_i_f_i_l_e_s_1fulldesc_M_INIFILES"/>

## Additional Information

You can update configuration file settings using the ALTER SYSTEM ALTER CONFIGURATION statement.

**Related Information**  


[Configuring SAP HANA System Properties (INI Files)](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2024_3_QRC/en-US/3f1a6a7dc31049409e1a9f9108d73d51.html "An SAP HANA database has several configuration (*.ini) files that contain properties for configuring the database and services.") :arrow_upper_right:

[M\_INIFILE\_CONTENTS System View](m-inifile-contents-system-view-20b16a7.md "Provides configuration information from INI files.")

[M\_INIFILE\_CONTENT\_HISTORY System View](m-inifile-content-history-system-view-a42a0b8.md "Provides change history information for configuration (ini) files.")

[ALTER SYSTEM ALTER CONFIGURATION Statement \(System Management\)](../../010-SQL-Reference/012-SQL-Statements/alter-system-alter-configuration-statement-system-management-20d08a5.md "Sets or removes configuration parameters in an INI file.")

