<!-- loioa42a0b87344d463386ebbeb0651c3470 -->

# M\_INIFILE\_CONTENT\_HISTORY System View

Provides change history information for configuration \(ini\) files.



<a name="loioa42a0b87344d463386ebbeb0651c3470___m__i_n_i_f_i_l_e__c_o_n_t_e_n_t_s_1struct_M_INIFILE_CONTENTS"/>

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

TIME

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the timestamp when the configuration setting was changed.

</td>
</tr>
<tr>
<td valign="top">

FILE\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of the configuration file.

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

Displays the configuration layer: DEFAULT, SYSTEM, HOST, or DATABASE.

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

Displays the host name, if the LAYER\_NAME is HOST. Otherwise, this value is NULL.

</td>
</tr>
<tr>
<td valign="top">

USER\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the user name if the change was made by an SAP HANA user.

</td>
</tr>
<tr>
<td valign="top">

APPLICATION\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the value of the APPLICATION session variable, if an application made the change. Otherwise, this value is NULL.

</td>
</tr>
<tr>
<td valign="top">

APPLICATION\_USER\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the value of the APPLICATIONUSER session variable, if an application made the change. Otherwise, this value is NULL.

</td>
</tr>
<tr>
<td valign="top">

APPLICATION\_SOURCE

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of the application source if an application made the change. Otherwise, this value is NULL.

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

Displays the name of the section in the configuration file where the change was made.

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

Displays the name of the configuration key that was changed.

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

Displays the new configuration value.

</td>
</tr>
<tr>
<td valign="top">

PREV\_VALUE

</td>
<td valign="top">

NVARCHAR\(5000\)

</td>
<td valign="top">

Displays the value of the configuration parameter before the change was made.

</td>
</tr>
<tr>
<td valign="top">

COMMENTS

</td>
<td valign="top">

NVARCHAR\(5000\)

</td>
<td valign="top">

Displays the comment provided, if any, at the time of the configuration change.

</td>
</tr>
</table>

**Related Information**  


[ALTER SYSTEM CLEAR INIFILE CONTENT HISTORY Statement \(System Management\)](../../010-SQL-Reference/012-SQL-Statements/alter-system-clear-inifile-content-history-statement-system-management-fb097f2.md "Clears ini file content history from the catalog.")

[Configuring SAP HANA System Properties (INI Files)](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2023_4_QRC/en-US/3f1a6a7dc31049409e1a9f9108d73d51.html "An SAP HANA database has several configuration (*.ini) files that contain properties for configuring the database and services.") :arrow_upper_right:

[M\_INIFILES System View](m-inifiles-system-view-20b18dc.md "Provides information about all configuration files.")

[M\_INIFILE\_CONTENTS System View](m-inifile-contents-system-view-20b16a7.md "Provides configuration information from INI files.")

[ALTER SYSTEM ALTER CONFIGURATION Statement \(System Management\)](../../010-SQL-Reference/012-SQL-Statements/alter-system-alter-configuration-statement-system-management-20d08a5.md "Sets or removes configuration parameters in an INI file.")

