<!-- loio9e7401268b0c4dbda5d5186773ba14ab -->

# TABLE\_PLACEMENT\_LOCATIONS System View

Provides table placement location information.



<a name="loio9e7401268b0c4dbda5d5186773ba14ab__section_rwh_cck_vhb"/>

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

LOCATION\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the location name.

</td>
</tr>
<tr>
<td valign="top">

INCLUDE

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the list of volume IDs or synonyms which are added to the respective location name.

</td>
</tr>
<tr>
<td valign="top">

EXCLUDE

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the list of volume IDs or synonyms which are removed from the respective location name.

</td>
</tr>
</table>



<a name="loio9e7401268b0c4dbda5d5186773ba14ab__section_jpn_jxz_2zb"/>

## Additional Information

Unless otherwise specified, system views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all system views and their data regardless of the PUBLIC role and privilege grants.

**Related Information**  


[ALTER SYSTEM ALTER TABLE PLACEMENT Statement \(System Management\)](../../010-SQL-Reference/012-SQL-Statements/alter-system-alter-table-placement-statement-system-management-0715b97.md "Changes table classification and placement settings for table groups.")

[Table Placement](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2023_4_QRC/en-US/22888f9344954f258284d2dd936d0d0a.html "Table classification and table placement configuration, enhanced by partitioning, build the foundation for controlling the data distribution in a SAP HANA scale-out environment.") :arrow_upper_right:

[TABLES System View](tables-system-view-2101973.md "Provides information about tables in the database.")

[TABLE\_PLACEMENT System View](table-placement-system-view-522cc8e.md "Provides table placement information.")

[TABLE\_PLACEMENT\_LOCATIONS System View](table-placement-locations-system-view-9e74012.md "Provides table placement location information.")

[M\_TABLE\_PLACEMENT\_LOCATIONS System View](../022-Monitoring-Views/m-table-placement-locations-system-view-7ecc1cc.md "Provides table placement location monitoring information.")

[M\_TABLE\_LOCATIONS System View](../022-Monitoring-Views/m-table-locations-system-view-20c65d5.md "Provides information about tables and their logical location. Physical locations are shown in M_TABLE_PERSISTENCE_LOCATIONS.")

