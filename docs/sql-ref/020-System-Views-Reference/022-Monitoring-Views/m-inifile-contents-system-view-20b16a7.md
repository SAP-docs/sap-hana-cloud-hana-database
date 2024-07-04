<!-- loio20b16a7e75191014ae4bfdef8a652a22 -->

# M\_INIFILE\_CONTENTS System View

Provides configuration information from INI files.



<a name="loio20b16a7e75191014ae4bfdef8a652a22___m__i_n_i_f_i_l_e__c_o_n_t_e_n_t_s_1struct_M_INIFILE_CONTENTS"/>

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

LAYER\_NAME

</td>
<td valign="top">

NVARCHAR\(16\)

</td>
<td valign="top">

Displays the configuration layer: DEFAULT, SYSTEM, HOST or DATABASE.

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

Displays the configuration section name.

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

Displays the configuration key name.

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

Displays the configuration value.

</td>
</tr>
</table>



<a name="loio20b16a7e75191014ae4bfdef8a652a22__section_i34_lyz_xbc"/>

## Permissions

Unless otherwise specified, monitoring views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all monitoring views and their data regardless of the PUBLIC role and privilege grants.

**Related Information**  


[Configuring SAP HANA System Properties (INI Files)](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2024_3_QRC/en-US/3f1a6a7dc31049409e1a9f9108d73d51.html "An SAP HANA database has several configuration (*.ini) files that contain properties for configuring the database and services.") :arrow_upper_right:

[M\_INIFILES System View](m-inifiles-system-view-20b18dc.md "Provides information about all configuration files.")

[M\_INIFILE\_CONTENT\_HISTORY System View](m-inifile-content-history-system-view-a42a0b8.md "Provides change history information for configuration (ini) files.")

[ALTER SYSTEM ALTER CONFIGURATION Statement \(System Management\)](../../010-SQL-Reference/012-SQL-Statements/alter-system-alter-configuration-statement-system-management-20d08a5.md "Sets or removes configuration parameters in an INI file.")

