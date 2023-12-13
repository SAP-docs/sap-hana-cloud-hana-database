<!-- loio2992220ef88f4e6aa52b6352f74921f2 -->

# ANONYMIZATION\_VIEWS System View

Provides information about anonymized views in the SAP HANA database.



<a name="loio2992220ef88f4e6aa52b6352f74921f2___t_r_i_g_g_e_r_s_1struct_TRIGGERS"/>

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

SCHEMA\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the schema name of the anonymized view.

</td>
</tr>
<tr>
<td valign="top">

VIEW\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of the anonymized view.

</td>
</tr>
<tr>
<td valign="top">

ALGORITHM

</td>
<td valign="top">

NVARCHAR\(32\)

</td>
<td valign="top">

Displays the algorithm used to anonymize the view: K-ANONYMITY/DIFFERENTIAL PRIVACY.

</td>
</tr>
<tr>
<td valign="top">

PARAMETERS

</td>
<td valign="top">

NCLOB

</td>
<td valign="top">

Displays the view-level anonymization parameters defined for the view, in JSON format.

</td>
</tr>
</table>



<a name="loio2992220ef88f4e6aa52b6352f74921f2__section_ov2_h3c_bzb"/>

## Permissions

Unless otherwise specified, system views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all system views and their data regardless of the PUBLIC role and privilege grants.

**Related Information**  


[ANONYMIZATION\_VIEW\_COLUMNS System View](anonymization-view-columns-system-view-ee12fae.md "Provides information about the anonymized columns in SAP HANA database.")

[M\_ANONYMIZATION\_VIEWS System View](../022-Monitoring-Views/m-anonymization-views-system-view-6a44772.md "Provides runtime information about anonymized views.")

[VIEWS System View](views-system-view-2102bf2.md "Lists available views.")

[CREATE VIEW Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/create-view-statement-data-definition-20d5fa9.md "Creates a view on the database.")

[ALTER VIEW Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/alter-view-statement-data-definition-3bc8951.md "Alters the definition, restrictions, or options on a view.")

[REFRESH VIEW Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/refresh-view-statement-data-definition-81e1583.md "Refreshes an anonymized view.")

