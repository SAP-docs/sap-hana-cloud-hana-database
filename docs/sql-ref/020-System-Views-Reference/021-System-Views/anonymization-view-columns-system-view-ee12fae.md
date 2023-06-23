<!-- loioee12faebcecd4929a84160e503f9bc41 -->

# ANONYMIZATION\_VIEW\_COLUMNS System View

Provides information about the anonymized columns in SAP HANA database.



<a name="loioee12faebcecd4929a84160e503f9bc41___t_r_i_g_g_e_r_s_1struct_TRIGGERS"/>

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

COLUMN\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the name of the column with anonymization parameters.



</td>
</tr>
<tr>
<td valign="top">

POSITION



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Displays the ordinal position of the view column.



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

Displays the column-level anonymization parameters defined for the view, in JSON format.



</td>
</tr>
</table>

**Related Information**  


[ANONYMIZATION\_VIEWS System View](anonymization-views-system-view-2992220.md "Provides information about anonymized views in the SAP HANA database.")

[M\_ANONYMIZATION\_VIEWS System View](../022-Monitoring-Views/m-anonymization-views-system-view-6a44772.md "Provides runtime information about anonymized views.")

[VIEWS System View](views-system-view-2102bf2.md "Lists available views.")

[CREATE VIEW Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/create-view-statement-data-definition-20d5fa9.md "Creates a view on the database.")

[ALTER VIEW Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/alter-view-statement-data-definition-3bc8951.md "Alters the definition, restrictions, or options on a view.")

[REFRESH VIEW Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/refresh-view-statement-data-definition-81e1583.md "Refreshes an anonymized view.")

