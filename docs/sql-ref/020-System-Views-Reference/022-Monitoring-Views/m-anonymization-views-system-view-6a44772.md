<!-- loio6a44772e5dad4457b8285202f8f776ed -->

# M\_ANONYMIZATION\_VIEWS System View

Provides runtime information about anonymized views.



<a name="loio6a44772e5dad4457b8285202f8f776ed___t_r_i_g_g_e_r_s_1struct_TRIGGERS"/>

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

Displays the schema name.

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

ANONYMIZATION\_STATUS

</td>
<td valign="top">

NVARCHAR\(16\)

</td>
<td valign="top">

Displays the status of the anonymized view.

Possible values for views anonymized using the DIFFERENTIAL\_PRIVACY algorithm are READY, INVALID, or REFRESHING.

Possible values for views anonymized using the K-ANONYMITY and L-DIVERSITY algorithm are CREATED, REFRESHING, READY, or INVALID.

</td>
</tr>
<tr>
<td valign="top">

REFRESH\_RECOMMENDED

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether a refresh is recommended: TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

LAST\_REFRESH\_TIME

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the finish time of the latest refresh.

</td>
</tr>
<tr>
<td valign="top">

LAST\_REFRESH\_PARAMETERS

</td>
<td valign="top">

NCLOB

</td>
<td valign="top">

Displays the parameters specified during the last REFRESH VIEW command on the view, in JSON format.

</td>
</tr>
</table>



<a name="loio6a44772e5dad4457b8285202f8f776ed__section_ckk_p32_qbc"/>

## Permissions

Unless otherwise specified, monitoring views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all monitoring views and their data regardless of the PUBLIC role and privilege grants.

**Related Information**  


[ANONYMIZATION\_VIEWS System View](../021-System-Views/anonymization-views-system-view-2992220.md "Provides information about anonymized views in the SAP HANA database.")

[ANONYMIZATION\_VIEW\_COLUMNS System View](../021-System-Views/anonymization-view-columns-system-view-ee12fae.md "Provides information about the anonymized columns in SAP HANA database.")

[VIEWS System View](../021-System-Views/views-system-view-2102bf2.md "Lists available views.")

[CREATE VIEW Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/create-view-statement-data-definition-20d5fa9.md "Creates a view on the database.")

[ALTER VIEW Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/alter-view-statement-data-definition-3bc8951.md "Alters the definition, restrictions, or options on a view.")

[REFRESH VIEW Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/refresh-view-statement-data-definition-81e1583.md "Refreshes an anonymized view.")

